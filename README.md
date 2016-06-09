# three.js-glsl-simple-underwater-shader
This is a simple underwater effect shader written in glsl for three.js usage.

<h1>Requirement:</h1>
1. three.js
2. CopyShader.js
3. EffectComposer.js
4. RenderPass.js
5. MaskPass.js
6. ShaderPass.js

<h1>How to get these required files:</h1>
1. go to http://threejs.org/
2. choose "download" on left menu
3. extract downloaded file to get a folder named "three.js-master"
4. you will need these files:

    three.js-master/build/three.js, 
    three.js-master/example/js/shaders/CopyShader.js, 
    three.js-master/examplejs/postprocessing/RenderPass.js, 
    three.js-master/examplejs/postprocessing/MaskPass.js, 
    three.js-master/examplejs/postprocessing/ShaderPass.js

<h1>How to use the shader:</h1>
1. import all necessary reference files
2. import the shader file "vergil_water_shader.js"
3. add these lines outside the main loop:

            var composer, effect, effect2, effect3, effect4;
            composer = new THREE.EffectComposer( renderer );
            composer.addPass( new THREE.RenderPass( scene, camera ) );
            effect = new THREE.ShaderPass( THREE.VergilWaterShader );
            effect.uniforms['centerX'].value = 0.8;
            effect.uniforms['centerY'].value = 0.8;
            composer.addPass( effect );
            effect2 = new THREE.ShaderPass( THREE.VergilWaterShader );
            effect2.uniforms['centerX'].value = 0.2;
            effect2.uniforms['centerY'].value = 0.2;
            composer.addPass( effect2 );
            effect3 = new THREE.ShaderPass( THREE.VergilWaterShader );
            effect3.uniforms['centerX'].value = 0.2;
            effect3.uniforms['centerY'].value = 0.8;
            composer.addPass( effect3 );
            effect4 = new THREE.ShaderPass( THREE.VergilWaterShader );
            effect4.uniforms['centerX'].value = 0.8;
            effect4.uniforms['centerY'].value = 0.2;
            effect4.renderToScreen = true;
            composer.addPass( effect4 )
            
            
4. add these lines inside the main loop:

    	effect.uniforms['time'].value += Math.random();
	effect2.uniforms['time'].value += Math.random();
	effect3.uniforms['time'].value += Math.random();
	effect4.uniforms['time'].value += Math.random();
    	composer.render();//this should replace "renderer.render()" in your previous
            
<h1>Run examples</h1>
1. Go to "underwater_shader/example/magnifier_effect_example" or "underwater_shader/example/underwater_effect_example"
2. run "index.html" using a web browser


