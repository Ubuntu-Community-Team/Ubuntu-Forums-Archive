---
title: "Superbrothers black screen"
date: 2012-08-21
forum: Gaming &amp; Leisure
---

### Post by Jannay on 2012-08-21
I installed Superbrothers via Ubuntu Software center but when I run it all I get is a black screen. I'm able to get to the desktop with the Super key and from there I can see that the CPU is at 95% but nothing is happening with the game.
I'm running 12.04 on an Athlon 3500+ machine with GeForce 6600GT

Here is the content of the ~/.capy/SwordAndSworcery/log.txt
```

Info: Superbrothers: Sword & Sworcery EP Version 1.02
Info: Linux LANG: et_EE.UTF-8
Info: Capy::DriverPlatform::initOS() OK!
Info: Capy::DriverPlatform::initialise() OK!
Info: Capy::DriverFileSystem::initialise() OK!
Info: Resource Directory: '/opt/swordandsworcery/bin/../res/'
Info: Capy::DriverArchive::initialise() OK!
Info: EventManager::initialise() OK!
Info: Capy::DriverInput::initialise() OK!
Info: Creating the FMOD System...
Info: Pre-initializing...
Info: Determining capabilities of sound card...
Info: Capabilities= '0' : '2'
Info: Setting speaker mode to '2'
Info: Finally initializing FMOD...
Info: Successfully initialized FMOD with no errors!
Info: setMediaPath(/opt/swordandsworcery/bin/../res/sounds/)
Info: File handle looking for: /opt/swordandsworcery/bin/../res/sounds/SSS.fev
Info: /opt/swordandsworcery/bin/../res/sounds/SSS.fev
Info: Start loading music system
Info: Done loading music system
Info: Capy::DriverAudio::initialise() OK!
Info: FMOD Memory: current load:    1898314, max:    1898314
Info: Capy::DriverGraphics::initScreen() OK!
Info: Capy::DriverGraphics::initialise() OK!
Info: Capy::DriverGraphics2d::initialise() OK!
Info: SpriteManager::initialise() OK!
Info: EntityManager::initialise() OK!
Info: FontManager::initialise() OK!
Info: ParticleManager::initialise() OK!
Info: LuaManager::initialise() OK!
Info: Set caption
Info: Set video mode
Info: OpenGL version: 2.1.2 NVIDIA 173.14.35
Info: OpenGL vendor: NVIDIA Corporation 
Info: Renderer: GeForce 6600 GT/PCI/SSE2/3DNOW!
Info: OpenGL Texture: 2048 x 2048
Info: Current Resolution: 1440 x 900 (fullscreen)
Info: Mipmapping: enabled
Info: Loading default textures...
Info: Finished loading default textures
Info: Available resolutions
Info:   1440 x 900
Info:   1360 x 768
Info:   1152 x 864
Info:   1024 x 768
Info:   960 x 600
Info:   960 x 540
Info:   840 x 525
Info:   832 x 624
Info:   800 x 600
Info:   800 x 512
Info:   720 x 450
Info:   680 x 384
Info:   640 x 512
Info:   640 x 480
Info:   576 x 432
Info:   512 x 384
Info:   416 x 312
Info:   400 x 300
Info:   320 x 240
Info: Supported Resolutions
Info:   1440 x 900
Info:   1360 x 768
Info:   1152 x 864
Info:   1024 x 768
Info:   960 x 600
Info:   960 x 540
Info:   840 x 525
Info:   832 x 624
Info:   800 x 600
Info:   800 x 512
Info:   720 x 450
Info:   680 x 384
Info:   640 x 512
Info:   640 x 480
Info:   576 x 432
Info:   512 x 384
Info:   416 x 312
Info:   400 x 300
Info:   320 x 240
Info: initComponents() ok!
Info: Engine::initialise() ok!
Info: game date time: Tue Aug 21 23:38:06 2012
Info: switchScene: titlescreen
Info: begin music cue: FadeOut
Info: end music cue: FadeOut
Info: /opt/swordandsworcery/bin/../res/sounds/SSSpeoplecombat.fsb
Info: Loading scene: /opt/swordandsworcery/bin/../res/scenes/titlescreen

```Any ideas how to debug or solve the problem?

Edit: I got the game to work when I logged in into the Unity 2D session.

---

