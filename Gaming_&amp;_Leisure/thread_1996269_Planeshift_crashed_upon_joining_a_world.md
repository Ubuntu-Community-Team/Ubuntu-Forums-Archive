---
title: "Planeshift crashed upon joining a world"
date: 2012-06-04
forum: Gaming &amp; Leisure
---

### Post by unitedanarchy on 2012-06-04
I am on Ubuntu 11.10 on a Macbook late 2007 13", After being in IRCs for a while I think my problem is with shaders and my graphics card being an Intel GMA X3100 I think, I'm not sure if that is the right graphics card. Anyway, Help would be appreciated.

---

### Post by Perfect Storm on 2012-06-04
if it's shader problem try this; [http://www.hydlaaplaza.com/smf/index.php?topic=26514.0](http://www.hydlaaplaza.com/smf/index.php?topic=26514.0)

But it's years old and may not be the problem.


Instead launch the game via the terminal and post the output.

---

### Post by unitedanarchy on 2012-06-04
Right now it says this 

valeskagrim@ValeskaGrim:/opt/PlaneShift$ sudo ./psclient
Your configuration files are in... /home/valeskagrim/.PlaneShift

crystalspace.pluginmgr.loadplugin:
  could not load plugin ‘crystalspace.sndsys.renderer.null’
ATTENTION: default value of option force_s3tc_enable overridden by environment.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x6400002
  Serial number of failed request:  95
  Current serial number in output stream:  99
valeskagrim@ValeskaGrim:/opt/PlaneShift$ 




and doesn't do anything when I run the psclient file, Before it said other things, But I think I lost the fubar post thing. Here's the output of play in pslaunch, 

valeskagrim@ValeskaGrim:/opt/PlaneShift$ sudo ./pslaunch
WARNING: could not load plugin ‘iSoundManager’
ERROR: Couldn't load plugin with class ‘iSoundManager’!
Opening GLX2D
Checking for updates to the updater: Using mirror [http://194.116.72.94/update/](http://194.116.72.94/update/) for updaterinfo.xml
ATTENTION: default value of option force_s3tc_enable overridden by environment.
Creating Context
Video driver GL/X version (direct renderer)
Visual ID: 0x0000000000000021, 24bit TrueColor
R8:G8:B8:A8, 
level 0, double buffered
NOTIFY: Applied: Intel DRI: Disable texture compression
NOTIFY: OpenGL renderer: Mesa DRI Intel(R) 965GM  (vendor: Tungsten Graphics, Inc) version 2.1 Mesa 7.11
NOTIFY: Using windowed mode at resolution 1024x747.
NOTIFY: Pixel format: Color: 24 Alpha: 8 Depth: 24 Stencil: 8 AccumColor: 0 AccumAlpha: 0 MultiSamples: 0 
NOTIFY: Multisample: disabled
NOTIFY: Using VBO with 64 MB of VBO memory
Mounting skin: /planeshift/art/pslaunch.zip
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/top_left_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/top_right_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/bottom_left_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/bottom_right_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/left_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/right_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/top_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >/paws/base/maps/leather/bottom_1.png<
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:50 2012, Mon Jun  4 17:34:50 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:50 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:50 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:50 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:51 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:51 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:51 2012, Mon Jun  4 17:34:51 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
DEBUG: Initializing OpenAL sound system
DEBUG: Retrieving available devices.
DEBUG: Available OpenAL device: PulseAudio Default
DEBUG: Available OpenAL device: ALSA Default
DEBUG: Available OpenAL device: No Output
DEBUG: Default OpenAL device: PulseAudio Default
DEBUG: No device specified
DEBUG: Falling back on default device
DEBUG: OpenAL context frequency: 44100 Hz
DEBUG: OpenAL context refresh: 43 Hz
DEBUG: OpenAL context uses asynchronous (threaded) context
DEBUG: OpenAL context should support 255 mono sources
DEBUG: OpenAL context should support 1 stereo sources
Skin loaded: elves.zip
Couldn't locate resource Examine Background in the current skin!
Couldn't locate resource Examine Background in the current skin!
Using mirror [http://194.116.72.94/update/](http://194.116.72.94/update/) for updateservers.xml
No updates needed!
Checking for updates to all files: No updates needed!
DEBUG: Closing OpenAL sound system
DEBUG: Closing OpenAL sound system
Your configuration files are in... /home/valeskagrim/.PlaneShift

crystalspace.pluginmgr.loadplugin:
  could not load plugin ‘crystalspace.sndsys.renderer.null’
ATTENTION: default value of option force_s3tc_enable overridden by environment.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x6600002
  Serial number of failed request:  95
  Current serial number in output stream:  99
WARNING: could not load plugin ‘iSoundManager’
ERROR: Couldn't load plugin with class ‘iSoundManager’!
Opening GLX2D
ATTENTION: default value of option force_s3tc_enable overridden by environment.
Creating Context
Checking for updates to the updater: Using mirror [http://194.116.72.94/update/](http://194.116.72.94/update/) for updaterinfo.xml
Video driver GL/X version (direct renderer)
Visual ID: 0x0000000000000021, 24bit TrueColor
R8:G8:B8:A8, 
level 0, double buffered
NOTIFY: Applied: Intel DRI: Disable texture compression
NOTIFY: OpenGL renderer: Mesa DRI Intel(R) 965GM  (vendor: Tungsten Graphics, Inc) version 2.1 Mesa 7.11
NOTIFY: Using windowed mode at resolution 1024x747.
NOTIFY: Pixel format: Color: 24 Alpha: 8 Depth: 24 Stencil: 8 AccumColor: 0 AccumAlpha: 0 MultiSamples: 0 
NOTIFY: Multisample: disabled
NOTIFY: Using VBO with 64 MB of VBO memory
Mounting skin: /planeshift/art/pslaunch.zip
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/top_left_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/top_right_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/bottom_left_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/bottom_right_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/left_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/right_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/top_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >/paws/base/maps/leather/bottom_1.png<
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Mon Jun  4 17:34:53 2012, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Mon Jun  4 17:34:53 2012, Could not open image: >Scaling Field Background<
Mon Jun  4 17:34:53 2012, Mon Jun  4 17:34:53 2012, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
DEBUG: Initializing OpenAL sound system
DEBUG: Retrieving available devices.
DEBUG: Available OpenAL device: PulseAudio Default
DEBUG: Available OpenAL device: ALSA Default
DEBUG: Available OpenAL device: No Output
DEBUG: Default OpenAL device: PulseAudio Default
DEBUG: No device specified
DEBUG: Falling back on default device
DEBUG: OpenAL context frequency: 44100 Hz
DEBUG: OpenAL context refresh: 43 Hz
DEBUG: OpenAL context uses asynchronous (threaded) context
DEBUG: OpenAL context should support 255 mono sources
DEBUG: OpenAL context should support 1 stereo sources
Skin loaded: elves.zip
Couldn't locate resource Examine Background in the current skin!
Couldn't locate resource Examine Background in the current skin!
Using mirror [http://194.116.72.94/update/](http://194.116.72.94/update/) for updateservers.xml
No updates needed!
Checking for updates to all files: No updates needed!
DEBUG: Closing OpenAL sound system
DEBUG: Closing OpenAL sound system
valeskagrim@ValeskaGrim:/opt/PlaneShift$ 



When I pressed play the window went away and came back to the same thing.

---

### Post by Perfect Storm on 2012-06-05
> X Error of failed request: BadValue (integer parameter out of range for operation)

This may indicate that the game starts up in a resolution that are a) not supported by your monitor or b) not supported by your video driver.

Try check your home directory for a hidden file/folder that contain(s) planeshift's config file and change the resolution.


Also never run an application/game with sudo (if it's not explicit is a system tool that ask for it). You'll ruined the permission of your config files of the game (may be the problem in this case), and you'll compromise the security of your system.

---

### Post by unitedanarchy on 2012-06-05
I turned the settings all the way down to see if it would keep me from getting issues, Should I revert it and try it?

---

### Post by unitedanarchy on 2012-06-05
Also, How do I add myself to the group games?

---

### Post by Perfect Storm on 2012-06-05
> **unitedanarchy said:**
> I turned the settings all the way down to see if it would keep me from getting issues, Should I revert it and try it?

never hurt to try different settings.


To add you to games group;
```
sudo usermod -a -G games USERNAME
```

May required to logout/login before taken effect.

---

### Post by unitedanarchy on 2012-06-05
Okay, Now only some of the files have a lock image on them, And all the ones I need to start the game I have access to I believe.

---

