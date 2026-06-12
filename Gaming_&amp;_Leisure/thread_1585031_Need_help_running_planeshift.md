---
title: "Need help running planeshift"
date: 2010-09-29
forum: Gaming &amp; Leisure
---

### Post by iarenoob on 2010-09-29
Hi I recently tried running planeshift and it seems to work fine except that there is no way to actually log in.  I don't know what its supposed to look like but it seems to me there should be a login screen or something when i first start it but there is nothing as you can see from the screen shot.  Yes, i did update. the terminal says something about not being able to find a skin or something.

---

### Post by P4man on 2010-09-30
Can you show (or copy paste) the output from the command line?
What videocard do you have?

---

### Post by iarenoob on 2010-09-30
my terminal says the following:

```
  WARNING: could not load plugin 'crystalspace.syntax.loader.service.text'
ERROR: Couldn't load plugin with class 'crystalspace.syntax.loader.service.text'!
WARNING: failed to initialize plugin 'crystalspace.graphics3d.shadercompiler.xmlshader'
WARNING: failed to initialize plugin 'crystalspace.graphics3d.shadercompiler.weaver'
WARNING: could not load plugin 'crystalspace.syntax.loader.service.text'
ERROR: Couldn't load plugin with class 'crystalspace.syntax.loader.service.text'!
WARNING: failed to initialize plugin 'crystalspace.graphics3d.shadercompiler.xmlshader'
WARNING: could not load plugin 'crystalspace.level.loader'
WARNING: could not load plugin 'crystalspace.level.loader'
WARNING: Can not load default shader vars, no iSyntaxService available
Opening GLX2D
Checking for updates to the updater: Using mirror [http://planeshift.clevertech.net/Updates/](http://planeshift.clevertech.net/Updates/) for updaterinfo.xml
Creating Context
Video driver GL/X version (direct renderer)
Visual ID: 0x0000000000000027, 24bit TrueColor
R8:G8:B8:A8, 
level 0, double buffered
WARNING: could not load plugin 'crystalspace.syntax.loader.service.text'
ERROR: Couldn't load plugin with class 'crystalspace.syntax.loader.service.text'!
NOTIFY: Applied: Broken ATI point sprites (ATI)
NOTIFY: Applied: ATI: Can't handle compressed formats for RECT textures
NOTIFY: Applied: ATI: RECT texture extension support apparently sucks
NOTIFY: Applied: ATI: 'Forceful' fixed function enable
NOTIFY: OpenGL renderer: ATI Mobility Radeon HD 5000 Series (vendor: ATI Technologies Inc.) version 3.2.9756 Compatibility Profile Context
NOTIFY: Using windowed mode at resolution 1024x768.
NOTIFY: Pixel format: Color: 24 Alpha: 8 Depth: 24 Stencil: 8 AccumColor: 0 AccumAlpha: 0 MultiSamples: 0 
NOTIFY: Multisample: disabled
NOTIFY: Using VBO with 64 MB of VBO memory
Default shader /shader/std_lighting.xml not available
Using mirror [http://216.6.227.163/updater/](http://216.6.227.163/updater/) for updaterinfo.xml
/shader/std_lighting_portal.xml: 'xmlshader' shader compiler not available
Default shader /shader/std_lighting_portal.xml not available
WARNING: could not load plugin 'crystalspace.renderloop.step.generic.type'
Failed to load plugin crystalspace.renderloop.step.generic.type; pandemonium will ensue.
WARNING: could not load plugin 'crystalspace.rendermanager.unshadowed'
No rendermanager set!
Mounting skin: /planeshift/art/pslaunch.zip
Texture Manager parsing /paws/launcher/imagelist.xml
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/top_left_1.png<
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/top_right_1.png<
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/bottom_left_1.png<
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/bottom_right_1.png<
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/left_1.png<
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/right_1.png<
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/top_1.png<
Thu Sep 30 21:45:26 2010, <src/common/paws/pawsimagedrawable.cpp:66 PreparePixmap SEVERE>
Thu Sep 30 21:45:26 2010, Could not open image: >/paws/base/maps/leather/bottom_1.png<
Thu Sep 30 21:45:26 2010, <src/common/sound/system.cpp:36 Initialize SEVERE>
Thu Sep 30 21:45:26 2010, Failed to locate Sound renderer!
DEBUG: Initializing OpenAL sound system
DEBUG: Retrieving available devices.
DEBUG: Available OpenAL device: PulseAudio Default
DEBUG: Available OpenAL device: ALSA Default
DEBUG: Available OpenAL device: OSS Default
DEBUG: Available OpenAL device: Null Output
DEBUG: Default OpenAL device: PulseAudio Default
DEBUG: No device specified
DEBUG: Falling back on default device
Using mirror [http://216.6.227.163/updater/](http://216.6.227.163/updater/) for updateservers.xml
DEBUG: OpenAL context frequency: 44100 Hz
DEBUG: OpenAL context refresh: 21 Hz
DEBUG: OpenAL context uses asynchronous (threaded) context
DEBUG: OpenAL context should support 255 mono sources
DEBUG: OpenAL context should support 1 stereo sources
No updates needed!
Checking for updates to all files: No updates needed!
Couldn't locate resource Examine Background in the current skin!
Couldn't locate resource Examine Background in the current skin!
 
```

I am using an ATI HD 5000 "evergreen" card with the proprietary catalyst drivers.

---

### Post by P4man on 2010-10-01
Looks like a corrupted or incomplete download. You could check if those PNGs are really there or try downloading it again?

---

### Post by iarenoob on 2010-10-01
I think your right, those files don't seem to exist.  Maybe it has something to do with how I installed it, what location would u recommend putting the installation in? 
Planeshift installs with a binary installer like many windows applications btw.

---

### Post by P4man on 2010-10-02
install it to your homefolder, and dont use sudo, unless it says it has to. you could try running the game with sudo, it may work for root if you installed it as root (but thats not a good idea).

---

