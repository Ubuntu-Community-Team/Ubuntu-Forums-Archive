---
title: "Sword &amp; Sworcery Clashes back to login on sandybridge"
date: 2012-06-05
forum: Gaming &amp; Leisure
---

### Post by tuppe666 on 2012-06-05
Currently using 12.04 64 bit and Sword & Sworcery crashes my computer. I just want to know is anyone else has a fix or is even experiencing the same problem.

---

### Post by BcRich on 2012-06-05
> **tuppe666 said:**
> Currently using 12.04 64 bit and Sword & Sworcery crashes my computer. I just want to know is anyone else has a fix or is even experiencing the same problem.
I'm trying to install it with the same setup. I downloaded the x64 deb (as I was having problems installing other HIB titles through Software Center). So I'm currently using GDebi package installer to install it. The installer seems to be downloading additional package files, but no information is given as to what it is downloading or how much longer the download has left.
Anyway, if I do manage to get it installed I'll let you know, if I have the same prob... ... ...

---

### Post by BcRich on 2012-06-05
Hi tuppe666
It had to install about 100MB of additional packages, but once that was done everything installed 100%. Game plays fine too thus far :) I'm not using a sandybridge, I'm using an AMD 1075t, and 6850 Gpu. Do you think that makes a difference? I'm not sure.
Did the game install without any problems for you? Could you elaborate on the details of how the crashing occurs?

---

### Post by hotweiss on 2012-06-07
I have the same problem.  Game crashes for me to.

> 
Info: Start loading music system
Info: Done loading music system
Info: Capy::DriverAudio::initialise() OK!
Info: FMOD Memory: current load:      58971, max:      67779
Info: Capy::DriverGraphics::initScreen() OK!
Info: Capy::DriverGraphics::initialise() OK!
Info: Capy::DriverGraphics2d::initialise() OK!
Info: SpriteManager::initialise() OK!
Info: EntityManager::initialise() OK!
Info: FontManager::initialise() OK!
Info: ParticleManager::initialise() OK!
Info: LuaManager::initialise() OK!
Info: OpenGL version: 4.2.11627 Compatibility Profile Context
Info: OpenGL vendor: ATI Technologies Inc. 
Info: Renderer: AMD Radeon HD 6520G
Info: OpenGL Texture: 2048 x 2048
Info: Current Resolution: 1366 x 768 (fullscreen)
Info: Mipmapping: enabled
Info: Engine::initialise() ok!
Info: game date time: Thu Jun  7 12:26:19 2012
Info: switchScene: titlescreen
Error: FMOD Event System update error! (81) This command failed because System::init or System::setDriver was not called. 
Info: Loading scene: /opt/swordandsworcery/bin/../res/scenes/titlescreen
Error: FMOD Event System update error! (81) This command failed because System::init or System::setDriver was not called. 

---

### Post by thatguruguy on 2012-06-07
> **tuppe666 said:**
> Currently using 12.04 64 bit and Sword & Sworcery crashes my computer. I just want to know is anyone else has a fix or is even experiencing the same problem.

Unless you provide information on what's happening, it's impossible to help you.

What kind of graphics hardware do you have?

What happens when you run the program from the terminal?

---

### Post by BcRich on 2012-06-07
hi hotweiss
here's the log file from my working installation
```
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
Info: Start loading music system
Info: Done loading music system
Info: Capy::DriverAudio::initialise() OK!
Info: FMOD Memory: current load:    1864676, max:    1864676
Info: Capy::DriverGraphics::initScreen() OK!
Info: Capy::DriverGraphics::initialise() OK!
Info: Capy::DriverGraphics2d::initialise() OK!
Info: SpriteManager::initialise() OK!
Info: EntityManager::initialise() OK!
Info: FontManager::initialise() OK!
Info: ParticleManager::initialise() OK!
Info: LuaManager::initialise() OK!
Info: Successfully loaded save.
Info: OpenGL version: 1.4 (2.1 (4.2.11631 Compatibility Profile Context))
Info: OpenGL vendor: ATI Technologies Inc. 
Info: Renderer: AMD Radeon HD 6800 Series  
Info: OpenGL Texture: 269025027 x 269025027
Info: Current Resolution: 1920 x 1080 (fullscreen)
Info: Mipmapping: enabled
Info: Engine::initialise() ok!
Info: game date time: Thu Jun  7 14:12:23 2012
Info: switchScene: titlescreen
Info: begin music cue: FadeOut
Info: end music cue: FadeOut
Info: Loading scene: /opt/swordandsworcery/bin/../res/scenes/titlescreen
Info: music param theCloudState: 0.000000
Info: begin music cue: theCloud_Title
Info: music param theCloudState: 1.000000
Info: Current Resolution: 1920 x 1080 (windowed)
```
In the event that you installed it to anything other than the default location, you might want to check that paths are correct.

---

### Post by tuppe666 on 2012-06-07
> **thatguruguy said:**
> Unless you provide information on what's happening, it's impossible to help you.

What kind of graphics hardware do you have?

What happens when you run the program from the terminal?

Sorry its got kind complicated, and I don't really understand. It works sometimes and other times it doesn't which is not helpful. It leaves no trace in dmesg or /sys/kernel/debug/dri/0/i915_error_state.

My hardware is just an i5-2500K HD Graphics 3000
I cannot see what happens if I run it in terminal, because it crashes X

---

### Post by thatguruguy on 2012-06-07
> **tuppe666 said:**
> Sorry its got kind complicated, and I don't really understand. It works sometimes and other times it doesn't which is not helpful. It leaves no trace in dmesg or /sys/kernel/debug/dri/0/i915_error_state.

My hardware is just an i5-2500K HD Graphics 3000
I cannot see what happens if I run it in terminal, because it crashes X

You may want to check your S&S log.  You can get it by typing:

```
gedit ~/.capy/SwordAndSworcery/log.txt
```
Feel free to substitute the editor of your choice for gedit.

---

