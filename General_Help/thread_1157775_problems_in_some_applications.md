---
title: "problems in some applications"
date: 2009-05-13
forum: General Help
---

### Post by AndyPaul on 2009-05-13
Hello i have some problems in 2d and 3d accleration (i think)
the applications that i cant run 
Boxee
XBMC
Enemy Territory
Ubuntu OS:9.04 x86
My system:
Pentium 4 2.4 GHz
512 MB ram DDR1
STLab ATI Radeon 9200
LOGS:
XBMC:
```
ubuntu@ubuntu-desktop:/usr/local/games/enemy-territory$ xbmc
The XBMC_HOME environment variable is not set.
Fatal error encountered, aborting
Error log at /home/ubuntu/.xbmc/temp/xbmc.log
Aborted
_________
|xbmc.log|
02:10:22 T:3065202544 M:210169856  NOTICE: -----------------------------------------------------------------------
02:10:22 T:3065202544 M:210169856  NOTICE: Starting XBMC, Platform: GNU/Linux.  Built on May  5 2009 (SVN:19929)
02:10:22 T:3065202544 M:210169856  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
02:10:22 T:3065202544 M:210169856  NOTICE: special://masterprofile/ is mapped to: /home/ubuntu/.xbmc/userdata
02:10:22 T:3065202544 M:210169856  NOTICE: special://home/ is mapped to: /home/ubuntu/.xbmc
02:10:22 T:3065202544 M:210169856  NOTICE: special://temp/ is mapped to: /home/ubuntu/.xbmc/temp
02:10:22 T:3065202544 M:210169856  NOTICE: The executable running is: /usr/share/xbmc/xbmc.bin
02:10:22 T:3065202544 M:210169856  NOTICE: Log File is located: /home/ubuntu/.xbmc/temp/xbmc.log
02:10:22 T:3065202544 M:210169856  NOTICE: -----------------------------------------------------------------------
02:10:24 T:3065202544 M:209858560  NOTICE: Setup SDL
02:10:25 T:3065202544 M:209002496    INFO: Available videomodes (xrandr):
02:10:25 T:3065202544 M:209002496    INFO: Number of connected outputs: 1
02:10:25 T:3065202544 M:209002496    INFO: Output 'VGA-0' has 10 modes
02:10:25 T:3065202544 M:209002496    INFO: ID:0x4f Name:1360x768 Refresh:59.798988 Width:1360 Height:768
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x50 Name:1152x864 Refresh:59.997059 Width:1152 Height:864
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x51 Name:1024x768 Refresh:60.003841 Width:1024 Height:768
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x52 Name:800x600 Refresh:60.316540 Width:800 Height:600
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x53 Name:640x480 Refresh:59.940479 Width:640 Height:480
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x110 Name:480i/60 Refresh:30.000000 Width:640 Height:480
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x111 Name:480p/60 Refresh:60.000000 Width:640 Height:480
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x112 Name:720p/60 Refresh:60.000000 Width:1280 Height:720
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x113 Name:1080i/60 Refresh:30.000000 Width:1920 Height:1080
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:209002496    INFO: ID:0x114 Name:1080p/60 Refresh:60.000000 Width:1920 Height:1080
02:10:25 T:3065202544 M:209002496    INFO: Pixel Ratio: 1.000000
02:10:25 T:3065202544 M:208793600   DEBUG: CLowLevelKeyboard::Initialize - XKb symbols pc_us_il(lyx)_2_ru_3_inet(evdev)_group(alt_shift_toggle)
02:10:25 T:3065202544 M:208793600    INFO: LIRC Initialize: connect failed: No such file or directory
02:10:25 T:3065202544 M:208793600    INFO: Drives are mapped
02:10:25 T:3065202544 M:208793600  NOTICE: load settings...
02:10:25 T:3065202544 M:208793600  NOTICE: special://profile/ is mapped to: special://masterprofile/
02:10:25 T:3065202544 M:208793600  NOTICE: loading special://masterprofile/guisettings.xml
02:10:25 T:3065202544 M:208793600  NOTICE: Getting hardware information now...
02:10:25 T:3065202544 M:208793600    INFO: Using analog output
02:10:25 T:3065202544 M:208793600    INFO: AC3 pass through is enabled
02:10:25 T:3065202544 M:208793600    INFO: DTS pass through is enabled
02:10:25 T:3065202544 M:208793600  NOTICE: Checking resolution 10
02:10:25 T:3065202544 M:208793600  NOTICE: Setting autoresolution mode 3
02:10:25 T:3065202544 M:208834560  NOTICE: No advancedsettings.xml to load (special://masterprofile/advancedsettings.xml)
02:10:25 T:3065202544 M:208834560  NOTICE: Default DVD Player: dvdplayer
02:10:25 T:3065202544 M:208834560  NOTICE: Default Video Player: dvdplayer
02:10:25 T:3065202544 M:208834560  NOTICE: Default Audio Player: paplayer
02:10:25 T:3065202544 M:208834560  NOTICE: special://masterprofile/sources.xml
02:10:25 T:3065202544 M:208834560    INFO: XRANDR: /usr/share/xbmc/xbmc-xrandr --output VGA-0 --mode 0x51
02:10:26 T:3065202544 M:208748544   DEBUG: Constructing surface 720x480, shared=(nil), fullscreen=0
02:10:26 T:3065202544 M:208748544    INFO: GLX Info: NOT Using destination window
02:10:26 T:3065202544 M:208375808  NOTICE: Using fbConfig[1]
02:10:26 T:3065202544 M:208375808    INFO: GLX Info: Using parent window
02:10:26 T:3065202544 M:208375808    INFO: GLX Info: Creating unshared context
02:10:26 T:3065202544 M:206819328  NOTICE: GL_VENDOR = Tungsten Graphics, Inc.
02:10:26 T:3065202544 M:206819328  NOTICE: GL_RENDERER = Mesa DRI R200 20060602 AGP 8x x86/MMX/SSE2 TCL
02:10:26 T:3065202544 M:206819328  NOTICE: GL_VERSION = 1.3 Mesa 7.4
02:10:26 T:3065202544 M:206819328  NOTICE: GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
02:10:26 T:3065202544 M:206819328    INFO: GL: Maximum texture width: 2048
02:10:26 T:3065202544 M:206819328    INFO: load language info file: special://xbmc/language/English/langinfo.xml
02:10:26 T:3065202544 M:206753792 WARNING: Trying to access old style dir: D:\media\media\Textures.xpr
02:10:26 T:3065202544 M:204279808   DEBUG: Load special://xbmc/media/Splash.png: 58.2ms
02:10:26 T:3065202544 M:206315520    INFO: load language file:special://xbmc/language/English/strings.xml
02:10:27 T:3065202544 M:206082048    INFO: load keymapping
02:10:27 T:3065202544 M:206082048    INFO: Loading special://xbmc/system/Keymap.xml
02:10:27 T:3065202544 M:206139392   DEBUG: CButtonTranslator::Load - no userdata keymap found, skipping
02:10:27 T:3065202544 M:206139392    INFO: Loading special://xbmc/system/Lircmap.xml
02:10:27 T:3065202544 M:206139392    INFO: Loading special://masterprofile/Lircmap.xml
02:10:27 T:3065202544 M:206139392    INFO: Checking skin version of: PM3.HD
02:10:27 T:3065202544 M:206139392    INFO: The above skin isn't suitable - checking the version of the default: PM3.HD
02:10:27 T:3065202544 M:206139392 WARNING: Emergency recovery console starting...
```Boxee:
```
ubuntu@ubuntu-desktop:/usr/local/games/enemy-territory$ cd /opt/boxee/
ubuntu@ubuntu-desktop:/opt/boxee$ sh run-boxee-desktop
13/05/09 06:16:00#DEBUG#bxbgprocess.cpp:142(Start)#bg process initialized. 1 worker threads created.
13/05/09 06:16:01#DEBUG#bxcurl.cpp:63(Initialize)#curl initialized. version <7.18.2>

Running Boxee test...
* Enable platform firectoriesAnd the log goes to... /tmp/ubuntu-
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  28
  Current serial number in output stream:  29
Boxee: asked to stop
Boxee: already stopped
BXBGProcess, Resolver Audio Processor, asked to stop, this = 0x8fa38e0
BXBGProcess, Resolver Video Processor, asked to stop, this = 0x8fa3874
BXBGProcess, , asked to stop, this = 0x8fa339c
BXBGProcess, Application Messenger, asked to stop, this = 0x8f0e7e4
BXBGProcess, Application Messenger, asked to stop, this = 0x8f0e7e4
_________________
|ubuntu-boxee.log|
02:16:01 T:3066898288 M:  7430144  NOTICE: Mapping drive Q to /opt/boxee
02:16:01 T:3066898288 M:  7430144  NOTICE: Mapping drive U to /home/ubuntu/.boxee
02:16:01 T:3066898288 M:  7430144  NOTICE: Mapping drive T to /home/ubuntu/.boxee/UserData
02:16:01 T:3066898288 M:  7430144  NOTICE: Mapping drive H to /home/ubuntu
02:16:01 T:3066898288 M:  7430144  NOTICE: -----------------------------------------------------------------------
02:16:01 T:3066898288 M:  7430144  NOTICE: Starting XBMC, Platform: GNU/Linux.  Built on Apr 26 2009 (SVN:5777M)
02:16:01 T:3066898288 M:  7430144  NOTICE: Q is mapped to: /opt/boxee
02:16:01 T:3066898288 M:  7430144  NOTICE: The executable running is: /opt/boxee/Boxee
02:16:01 T:3066898288 M:  7430144  NOTICE: Log File is located: /tmp/ubuntu-boxee.log
02:16:01 T:3066898288 M:  7430144  NOTICE: -----------------------------------------------------------------------
02:16:01 T:3066898288 M:  7430144  NOTICE: Setup SDL
02:16:01 T:3066898288 M:  6676480    INFO: Available videomodes (xrandr):
02:16:01 T:3066898288 M:  6676480    INFO: Number of connected outputs: 1
02:16:01 T:3066898288 M:  6676480    INFO: Output 'VGA-0' has 10 modes
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x4f Name:1360x768 Refresh:59.798988 Width:1360 Height:768
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x50 Name:1152x864 Refresh:59.997059 Width:1152 Height:864
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x51 Name:1024x768 Refresh:60.003841 Width:1024 Height:768
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x52 Name:800x600 Refresh:60.316540 Width:800 Height:600
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x53 Name:640x480 Refresh:59.940479 Width:640 Height:480
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x110 Name:480i/60 Refresh:30.000000 Width:640 Height:480
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x111 Name:480p/60 Refresh:60.000000 Width:640 Height:480
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x112 Name:720p/60 Refresh:60.000000 Width:1280 Height:720
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x113 Name:1080i/60 Refresh:30.000000 Width:1920 Height:1080
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: ID:0x114 Name:1080p/60 Refresh:60.000000 Width:1920 Height:1080
02:16:01 T:3066898288 M:  6676480    INFO: Pixel Ratio: 1.000000
02:16:01 T:3066898288 M:  6676480    INFO: Drives are mapped
02:16:01 T:3066898288 M:  6676480  NOTICE: load settings...
02:16:01 T:3066898288 M:  6676480  NOTICE: Mapping drive P to /home/ubuntu/.boxee/UserData
02:16:01 T:3066898288 M:  6676480  NOTICE: loading /home/ubuntu/.boxee/UserData/guisettings.xml
02:16:01 T:3066898288 M:  6561792  NOTICE: Getting hardware information now...
02:16:01 T:3066898288 M:  6561792    INFO: Using analog output
02:16:01 T:3066898288 M:  6561792    INFO: AC3 pass through is enabled
02:16:01 T:3066898288 M:  6561792    INFO: DTS pass through is enabled
02:16:01 T:3066898288 M:  6561792  NOTICE: Checking resolution 12
02:16:01 T:3066898288 M:  6561792  NOTICE: No advancedsettings.xml to load (/home/ubuntu/.boxee/UserData/advancedsettings.xml)
02:16:01 T:3066898288 M:  6561792  NOTICE: /home/ubuntu/.boxee/UserData/sources.xml
02:16:01 T:3066898288 M:  6561792   ERROR: Load Error loading /home/ubuntu/.boxee/UserData/sources.xml: Line 0, Failed to open file
02:16:01 T:3066898288 M:  6561792    INFO: Checking skinpath existence, and existence of keymap.xml:Q:\skin...
02:16:02 T:3066898288 M:  6582272    INFO: GLX Info: NOT Using destination window
02:16:02 T:3066898288 M:  6467584 WARNING: GLX: No Multisample buffers available, FSAA disabled
02:16:02 T:3066898288 M:  6467584    INFO: GLX Info: Using parent window
02:16:02 T:3066898288 M:  9789440   ERROR: (pthread_mutex_destroy(&m_mutex)): [XCriticalSection.cpp:86] 16
02:16:02 T:3066898288 M:  9805824    INFO: SMB: DEinitializing package
```Enemy Territory:
```
ubuntu@ubuntu-desktop:~$ cd /usr/local/games/enemy-territory
ubuntu@ubuntu-desktop:/usr/local/games/enemy-territory$ sh et
ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/ubuntu/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3729 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 50
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 50
Received signal 11, exiting...
Segmentation fault

```i cant install ati driver in System ->Administration->Hardware Drivers
"No proprietary drivers are in use on this system"
if i install the xorg-driver-fglrx
after restart my system fails at login screen it shows me half login screen and and after 2 sec its stack after removing xorg-driver-fglrx from recovery mode its works fine again but still without any accleration.
Sorry for my english.
Thats all hope for help :popcorn:.

---

### Post by salvachn on 2009-05-13
Enable the repository that contains third party applications.. Open a terminal and edit /etc/apt/sources.list:
> sudo gedit /etc/apt/sources.list
 Enable the jaunty partner repository:
 [...]


 ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.


 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner


 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[...]
  Then save the file.
  To enable the Medibuntu repository, please do the following:
  Import the repository:
  sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
  Import the gpg-key and update your package-list:
  sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update
  Then run
  sudo update-apt-xapian-index
 to make Synaptic display packages from third-party repositories.

---

