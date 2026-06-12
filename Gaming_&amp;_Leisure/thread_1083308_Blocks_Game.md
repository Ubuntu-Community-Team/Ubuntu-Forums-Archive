---
title: "Blocks Game"
date: 2009-02-28
forum: Gaming &amp; Leisure
---

### Post by amylase on 2009-02-28
Hi everyone,

RE: How to compile and run Blocks game.

I came across this peaceful little game where you control a little white man jumping and pushing boxes in a world full of boxes. 

The game looks likes this: 
[http://www.youtube.com/watch?v=I9c01OyUaPo&feature=related](http://www.youtube.com/watch?v=I9c01OyUaPo&feature=related) 
and is downloadable here
[http://sourceforge.net/project/showfiles.php?group_id=207669&package_id=248711](http://sourceforge.net/project/showfiles.php?group_id=207669&package_id=248711)

I managed to uncompress all the files out of the tar.bz2 ball and placed it under a directory called Blocks-1.1 under home directory. Blocks-1.1 contains these entries:
config.xml  data      INSTALL  msvc    SConstruct  source
COPYING     external  levels   README  shaders

Now, I tried to type in ./configure and am told:
> bash: ./configure: No such file or directory

So I cat INSTALL which tells me these:
> Building Blocks for Linux:

Required external libraries:
	OpenGL
	OpenEXR 
	OpenAL
	freeALUT
	freetype2
	FTGL
	Ogg/Vorbis

Required build-tools:
	SCons
	GCC

Build instructions:
	Simply use the following command to build the game:
		scons			# Build Blocks
	If you have a multi-processor system, the build-process can be 
	accelerated with the '-j' option:

		scons -j2 		# Build Blocks with 2 concurrent threads

Playing Blocks:
	
	You can	immediately play, by calling './Blocks config.xml'
	
	'config.xml' is a configuration file, that has to be supplied.

	To build a binary only version, you will need to copy the following 
	files and directories in 'Blocks':

		Blocks
		data/
		levels/
		shaders/
	
	You will need these in the working directory, where you start Blocks.

#################################################
Building Blocks for Windows:

You will need Visual Studio 2005 to build Blocks with the project-files in this directory.
The free express-edition should work as well with some tweaks. 	


On typing scons # Build Blocks, I get this message:
> could not open file '/etc/apt/sources.list'
bash: scons#: command not found

I am a bit lost now. How do I get this game to compile and run? Any advices would be greatly appreciated. I'm running Ubuntu 8.10. Thanks.

---

### Post by Perfect Storm on 2009-03-01
Did you install those things that is needed (+ build-essential + -dev of those pakages). Also as it says you need to install scons.

---

### Post by amylase on 2009-03-01
Thanks AI. How do I check if I already have these onboard, and if not how do I install them?

OpenGL
OpenEXR
OpenAL
freeALUT
freetype2
FTGL
Ogg/Vorbis
SCons

---

### Post by Perfect Storm on 2009-03-01
You can use synaptic package manager to search for these packages.

exampel for OpenEXR;

search for openexr. There may pop more up, but as you can see libopenexr6 is already installed. To compiled something from sources you need to install the -dev version of this package, which is called libopenexr-dev.

---

### Post by amylase on 2009-03-07
Hi AI thanks for the advices. I installed all the things listed and their -dev as well where available. Tries scons command again. This time it went on for 3 minutes building things and then terminated with this error message: "/usr/bin/ld: cannot find -lXxf86vm".

What is -lXxf86vm? How do I correct this error?
Here is the entire output I got on screen. Thanks a lot.

> :~/Blocks$ scons # Build Blocks
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o source/base/BlkLoop.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/base/BlkLoop.cpp
g++ -o source/base/BlkScene.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/base/BlkScene.cpp
g++ -o source/base/BlkScreen.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/base/BlkScreen.cpp
g++ -o source/blocks/BlkActionBlock.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/blocks/BlkActionBlock.cpp
g++ -o source/blocks/BlkFixedBlock.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/blocks/BlkFixedBlock.cpp
g++ -o source/blocks/BlkNormalBlock.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/blocks/BlkNormalBlock.cpp
g++ -o source/cameras/BlkDirectionalLightCamera.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/cameras/BlkDirectionalLightCamera.cpp
g++ -o source/cameras/BlkPlayerCamera.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/cameras/BlkPlayerCamera.cpp
g++ -o source/cameras/BlkSpotLightCamera.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/cameras/BlkSpotLightCamera.cpp
g++ -o source/cameras/BlkTitleCamera.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/cameras/BlkTitleCamera.cpp
g++ -o source/effects/BlkDepthOfField.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/effects/BlkDepthOfField.cpp
g++ -o source/fbo/BlkDeferredFBO.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/fbo/BlkDeferredFBO.cpp
g++ -o source/fbo/BlkDepthFBO.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/fbo/BlkDepthFBO.cpp
g++ -o source/fbo/BlkTexture2DFBO.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/fbo/BlkTexture2DFBO.cpp
g++ -o source/font/BlkFtglOutlineFont.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/font/BlkFtglOutlineFont.cpp
g++ -o source/game/BlkFailOSD.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkFailOSD.cpp
g++ -o source/game/BlkGame.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkGame.cpp
g++ -o source/game/BlkGameFail.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkGameFail.cpp
g++ -o source/game/BlkGameMain.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkGameMain.cpp
g++ -o source/game/BlkGamePause.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkGamePause.cpp
g++ -o source/game/BlkGameSetup.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkGameSetup.cpp
g++ -o source/game/BlkGameTitle.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkGameTitle.cpp
g++ -o source/game/BlkGoal.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkGoal.cpp
g++ -o source/game/BlkMarble.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkMarble.cpp
g++ -o source/game/BlkOnScreenDisplay.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkOnScreenDisplay.cpp
g++ -o source/game/BlkPauseOSD.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkPauseOSD.cpp
g++ -o source/game/BlkSetupOSD.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkSetupOSD.cpp
g++ -o source/game/BlkTitleOSD.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/game/BlkTitleOSD.cpp
g++ -o source/geometry/BlkCPolyhedron.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/geometry/BlkCPolyhedron.cpp
g++ -o source/geometry/BlkMesh.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/geometry/BlkMesh.cpp
g++ -o source/input/BlkControllerInput.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/input/BlkControllerInput.cpp
g++ -o source/input/BlkControllerInputConf.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/input/BlkControllerInputConf.cpp
g++ -o source/input/BlkQuakeInput.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/input/BlkQuakeInput.cpp
g++ -o source/lights/BlkDirectionalLight.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/lights/BlkDirectionalLight.cpp
g++ -o source/lights/BlkEmission.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/lights/BlkEmission.cpp
g++ -o source/lights/BlkShadowlessPointLight.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/lights/BlkShadowlessPointLight.cpp
g++ -o source/lights/BlkSpotLight.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/lights/BlkSpotLight.cpp
g++ -o source/octree/BlkLeaf.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/octree/BlkLeaf.cpp
g++ -o source/octree/BlkOctree.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/octree/BlkOctree.cpp
g++ -o source/openglTests/BlkOpenGLTests.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/openglTests/BlkOpenGLTests.cpp
g++ -o source/player/BlkPlayer.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/player/BlkPlayer.cpp
g++ -o source/player/BlkPlayerFalling.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/player/BlkPlayerFalling.cpp
g++ -o source/player/BlkPlayerHoldingBlock.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/player/BlkPlayerHoldingBlock.cpp
g++ -o source/player/BlkPlayerIdle.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/player/BlkPlayerIdle.cpp
g++ -o source/player/BlkPlayerOnWall.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/player/BlkPlayerOnWall.cpp
g++ -o source/player/BlkPlayerRunning.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/player/BlkPlayerRunning.cpp
g++ -o source/player/BlkPlayerState.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/player/BlkPlayerState.cpp
g++ -o source/renderer/BlkNewRenderer.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/renderer/BlkNewRenderer.cpp
g++ -o source/renderer/BlkRenderActionBlock.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/renderer/BlkRenderActionBlock.cpp
g++ -o source/renderer/BlkRenderController.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/renderer/BlkRenderController.cpp
source/renderer/BlkRenderController.cpp: In member function 'void Blk::RenderController::render()':
source/renderer/BlkRenderController.cpp:234: warning: invalid access to non-static data member 'Blk::Interleaved::texCoord' of NULL object
source/renderer/BlkRenderController.cpp:234: warning: (perhaps the 'offsetof' macro was used incorrectly)
source/renderer/BlkRenderController.cpp:235: warning: invalid access to non-static data member 'Blk::Interleaved::color' of NULL object
source/renderer/BlkRenderController.cpp:235: warning: (perhaps the 'offsetof' macro was used incorrectly)
source/renderer/BlkRenderController.cpp:236: warning: invalid access to non-static data member 'Blk::Interleaved::normal' of NULL object
source/renderer/BlkRenderController.cpp:236: warning: (perhaps the 'offsetof' macro was used incorrectly)
source/renderer/BlkRenderController.cpp:237: warning: invalid access to non-static data member 'Blk::Interleaved::tangent' of NULL object
source/renderer/BlkRenderController.cpp:237: warning: (perhaps the 'offsetof' macro was used incorrectly)
source/renderer/BlkRenderController.cpp:238: warning: invalid access to non-static data member 'Blk::Interleaved::vertex' of NULL object
source/renderer/BlkRenderController.cpp:238: warning: (perhaps the 'offsetof' macro was used incorrectly)
g++ -o source/renderer/BlkRenderFixedBlock.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/renderer/BlkRenderFixedBlock.cpp
g++ -o source/renderer/BlkRenderNormalBlock.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/renderer/BlkRenderNormalBlock.cpp
g++ -o source/shader/BlkShader.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/shader/BlkShader.cpp
g++ -o source/skybox/BlkSkybox.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/skybox/BlkSkybox.cpp
g++ -o source/sound/BlkSoundController.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/sound/BlkSoundController.cpp
source/sound/BlkSoundController.cpp: In constructor 'Blk::SoundController::SoundController()':
source/sound/BlkSoundController.cpp:34: warning: deprecated conversion from string constant to 'char*'
g++ -o source/tests/Game-Test.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/tests/Game-Test.cpp
g++ -o source/texture/BlkDepthTexture.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/texture/BlkDepthTexture.cpp
g++ -o source/texture/BlkTexture2D.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/texture/BlkTexture2D.cpp
g++ -o source/xml/BlkAnimatedMesh.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/xml/BlkAnimatedMesh.cpp
g++ -o source/xml/BlkXmlConfig.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/xml/BlkXmlConfig.cpp
g++ -o source/xml/BlkXmlLevel.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/xml/BlkXmlLevel.cpp
g++ -o source/xml/BlkXmlObject.o -c -I/usr/include -I/usr/include/OpenEXR -I/usr/include/freetype2 -Isource -Iexternal/GLee -Iexternal/glfw/include -Iexternal/tinyxml source/xml/BlkXmlObject.cpp
g++ -o Blocks source/base/BlkLoop.o source/base/BlkScene.o source/base/BlkScreen.o source/blocks/BlkActionBlock.o source/blocks/BlkFixedBlock.o source/blocks/BlkNormalBlock.o source/cameras/BlkDirectionalLightCamera.o source/cameras/BlkPlayerCamera.o source/cameras/BlkSpotLightCamera.o source/cameras/BlkTitleCamera.o source/effects/BlkDepthOfField.o source/fbo/BlkDeferredFBO.o source/fbo/BlkDepthFBO.o source/fbo/BlkTexture2DFBO.o source/font/BlkFtglOutlineFont.o source/game/BlkFailOSD.o source/game/BlkGame.o source/game/BlkGameFail.o source/game/BlkGameMain.o source/game/BlkGamePause.o source/game/BlkGameSetup.o source/game/BlkGameTitle.o source/game/BlkGoal.o source/game/BlkMarble.o source/game/BlkOnScreenDisplay.o source/game/BlkPauseOSD.o source/game/BlkSetupOSD.o source/game/BlkTitleOSD.o source/geometry/BlkCPolyhedron.o source/geometry/BlkMesh.o source/input/BlkControllerInput.o source/input/BlkControllerInputConf.o source/input/BlkQuakeInput.o source/lights/BlkDirectionalLight.o source/lights/BlkEmission.o source/lights/BlkShadowlessPointLight.o source/lights/BlkSpotLight.o source/octree/BlkLeaf.o source/octree/BlkOctree.o source/openglTests/BlkOpenGLTests.o source/player/BlkPlayer.o source/player/BlkPlayerFalling.o source/player/BlkPlayerHoldingBlock.o source/player/BlkPlayerIdle.o source/player/BlkPlayerOnWall.o source/player/BlkPlayerRunning.o source/player/BlkPlayerState.o source/renderer/BlkNewRenderer.o source/renderer/BlkRenderActionBlock.o source/renderer/BlkRenderController.o source/renderer/BlkRenderFixedBlock.o source/renderer/BlkRenderNormalBlock.o source/shader/BlkShader.o source/skybox/BlkSkybox.o source/sound/BlkSoundController.o source/tests/Game-Test.o source/texture/BlkDepthTexture.o source/texture/BlkTexture2D.o source/xml/BlkAnimatedMesh.o source/xml/BlkXmlConfig.o source/xml/BlkXmlLevel.o source/xml/BlkXmlObject.o external/GLee/GLee.o external/tinyxml/tinystr.o external/tinyxml/tinyxml.o external/tinyxml/tinyxmlerror.o external/tinyxml/tinyxmlparser.o -Lexternal/glfw/lib/x11 -L/usr/lib -lGL -lGLU -lX11 -lpthread -lXxf86vm -lm -lImath -lIlmImf -lIex -lHalf -lopenal -lalut -logg -lvorbis -lvorbisfile -lfreetype -lftgl -lglfw32
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
scons: *** [Blocks] Error 1
scons: building terminated because of errors.


---

### Post by amylase on 2009-03-07
Problem solved. I installed libXxf86vm-dev and this time scons went from start to finish. What's sad though is after going through all this trouble compiling, the game doesn't load:

> ~/Blocks$ ./Blocks config.xml
parse XML - complete
calculate vertices - complete
shaders/emissionPass.vert: Compilation failed.

shaders/emissionPass.frag: Compilation failed.

Linking failed.

Segmentation fault


I suspect this is now problem with the game itself for which I might try contact the guy who made it. 

Thanks a lot for all the help.

[B]
Addendum:[/B]
It turns out my graphic card isn't good enough for it. You need at least Geforce 6000 or something to run it.

---

