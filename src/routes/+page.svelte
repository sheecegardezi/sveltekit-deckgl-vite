<script>
	import { onMount } from 'svelte';
	const COUNTRIES = 'https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_0_scale_rank.geojson'; //eslint-disable-line

	onMount(async() => {

		const { Deck } = await import('@deck.gl/core');
		const { GeoJsonLayer}  = await import('@deck.gl/layers');
		
		

		const INITIAL_VIEW_STATE = {
			latitude: 51.47,
			longitude: 0.45,
			zoom: 4,
			bearing: 0,
			pitch: 30
		};

		new Deck({
			initialViewState: INITIAL_VIEW_STATE,
			controller: true,
			layers: [
				new GeoJsonLayer({
					id: 'base-map',
					data: COUNTRIES,
					// Styles
					stroked: true,
					filled: true,
					lineWidthMinPixels: 2,
					opacity: 0.4,
					getLineColor: [60, 60, 60],
					getFillColor: [200, 200, 200]
				})
			]
		});
	});

</script>
