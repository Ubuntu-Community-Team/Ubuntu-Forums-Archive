---
title: "Planeshift wont work"
date: 2011-08-11
forum: Gaming &amp; Leisure
---

### Post by nidzo732 on 2011-08-11
I've downloaded and installed planeshift into my home directory, but when i try to run it, i just get a blank window.
Here's the output when i run it from the terminal
```

nidzo@nidzo-lt:~/PlaneShift$ ./pslaunch
Couldn't open xml file '/this/updateservers.xml'!
Unable to get root node!
Checking for updates to the updater: Using mirror http://updater.sajut.de/update/ for updaterinfo.xml
Opening GLX2D
Creating Context
Video driver GL/X version (direct renderer)
Visual ID: 0x0000000000000027, 24bit TrueColor
R8:G8:B8:A8, 
level 0, double buffered
NOTIFY: Applied: Broken ATI point sprites (ATI)
NOTIFY: Applied: ATI: Can't handle compressed formats for RECT textures
NOTIFY: Applied: ATI: RECT texture extension support apparently sucks
NOTIFY: Applied: ATI: 'Forceful' fixed function enable
NOTIFY: OpenGL renderer: AMD Radeon HD 6300M Series  (vendor: ATI Technologies Inc.) version 4.1.10665 Compatibility Profile Context
NOTIFY: Using windowed mode at resolution 1024x768.
NOTIFY: Pixel format: Color: 24 Alpha: 8 Depth: 24 Stencil: 8 AccumColor: 0 AccumAlpha: 0 MultiSamples: 0 
NOTIFY: Multisample: disabled
NOTIFY: Using VBO with 64 MB of VBO memory
Mounting skin: /planeshift/art/pslaunch.zip
Texture Manager parsing /paws/launcher/imagelist.xml
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/top_left_1.png<
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/top_right_1.png<
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/bottom_left_1.png<
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/bottom_right_1.png<
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/left_1.png<
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/right_1.png<
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/top_1.png<
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >/paws/base/maps/leather/bottom_1.png<
Thu Aug 11 21:58:43 2011, <src/common/sound/system.cpp:37 Initialize SEVERE>
Thu Aug 11 21:58:43 2011, Failed to locate Sound renderer!
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
Thu Aug 11 21:58:43 2011, <src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Thu Aug 11 21:58:43 2011, Could not open image: >Scaling Field Background<
Thu Aug 11 21:58:43 2011, Thu Aug 11 21:58:43 2011, ART ERROR: PawsTextureManager wasn't able to load the requested image: Scaling Field Background
DEBUG: Initializing OpenAL sound system
DEBUG: Retrieving available devices.
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
DEBUG: Available OpenAL device: PulseAudio Software
DEBUG: Available OpenAL device: ALSA Software
DEBUG: Available OpenAL device: PortAudio Software
DEBUG: Default OpenAL device: PulseAudio Software
DEBUG: No device specified
DEBUG: Falling back on default device
DEBUG: OpenAL context frequency: 44100 Hz
DEBUG: OpenAL context refresh: 21 Hz
DEBUG: OpenAL context uses asynchronous (threaded) context
DEBUG: OpenAL context should support 255 mono sources
DEBUG: OpenAL context should support 1 stereo sources
Couldn't locate resource Examine Background in the current skin!
Couldn't locate resource Examine Background in the current skin!
Using mirror http://updater.sajut.de/update/ for updateservers.xml
No updates needed!
Checking for updates to all files: Updates Available!

```

---

### Post by gordintoronto on 2011-08-11
Did you read the system requirements? What version of glibc do you have installed?

---

### Post by nidzo732 on 2011-08-12
How do i install glibc in natty. There is no package named glibc.

---

### Post by joeelmex on 2011-08-12
with reading a bit of the output it looks like you have a Ati mobile graphics card.  Im going to guess its a driver issue.  Try the close source drivers.

---

