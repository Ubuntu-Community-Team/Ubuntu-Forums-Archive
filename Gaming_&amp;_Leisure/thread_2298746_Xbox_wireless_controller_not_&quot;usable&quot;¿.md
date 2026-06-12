---
title: "Xbox wireless controller not &quot;usable&quot;¿?"
date: 2015-10-13
forum: Gaming &amp; Leisure
---

### Post by aitor-alonso on 2015-10-13
Hi all,

I'm trying to use my x360 wireless controllers on my ubuntu server + kodi + rom collection browser plugin + mame.

The thing is, when i plugin the wireless receiver i can see in dmesg that it's being properly recognised and i see them listed on /dev/input/event* and /dev/input/js*

First controller outputs stuff with a cat /dev/input/js0, jstest /dev/input/js0 also outputs properly.

Now, whenever i launch mame, although it auto-maps Joy 1 keys, they doesn't seem to correspond to actual /dev/input/js0 keys because it doesn't receive my input.

If i try to map manually any key by pressing a gamepad button it doesn't get recognised as well.

I've tried both with xpad module and xboxsrv driver with same results. Manually executed debug tools seem to work but when it comes to mame... no luck.

So my question is, what am i missing here? Could it be something related to permissions due to being an ubuntu-server install? What else can i check?


Kind regards.

p.s. i'm running ubuntu server 15.04 -> 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by aitor-alonso on 2015-10-16
I've tested same wireless controller on ubuntu laptop (desktop edition, same release) and it works flawlessly with ootb xpad driver + mame.

Any ideas what should i look into/debug?

---

### Post by shutterfoot on 2015-10-25
Have you tried running it in desktop edition on your desktop?

---

### Post by Chris on 2015-10-25
Yeah I ran in to that when I was trying a 360 controller on my Kodi media server. The problem is that there is some userland something or other that sets the permissions so that the current desktop user can use the joystick but if the machine is just a media/server with no user logged in to a desktop then the permissions will be such that a normal use can't access the /dev/input/eventXX for the joystick (mame will not use /dev/input/jsX, only the event device; actually it's because of SDL).

What I did was create a file "/etc/udev/rules.d/70-joystick.rules" and inside that file put this line:
```
SUBSYSTEM=="input", ENV{ID_INPUT_JOYSTICK}=="?*", TAG+="uaccess", GROUP="kodi", MODE="660"
```

Change the GROUP="kodi" to the group of the user you want to have access to the joystick.

Worked fine after that.

---

### Post by aitor-alonso on 2015-10-26
Hi,

Thanks to you both for your answers.

@shutterfoot: Yes, i've tested it on desktop edition and it works fine. I assume it must be some misconfiguration i've on my server edition after few release upgrades :-?

@Chris: I've tried adding that rule file, reboot, and result is pretty much the same, no luck with mame :-(

ls -l /dev/input
drwxr-xr-x 2 root root     120 oct 26 19:46 by-id
drwxr-xr-x 2 root root     140 oct 26 19:46 by-path
crw-rw---- 1 root input 13, 64 oct 26 19:46 event0
crw-rw---- 1 root input 13, 65 oct 26 19:46 event1
crw-rw---- 1 root input 13, 66 oct 26 19:46 event2
crw-rw---- 1 root input 13, 67 oct 26 19:46 event3
crw-rw---- 1 root input 13, 68 oct 26 19:46 event4
crw-rw---- 1 root input 13, 69 oct 26 19:46 event5
crw-rw---- 1 root input 13, 70 oct 26 19:47 event6
crw-rw---- 1 root input 13, 71 oct 26 19:47 event7
crw-rw---- 1 root input 13, 72 oct 26 19:47 event8
crw-rw---- 1 root input 13, 73 oct 26 19:47 event9
crw-rw-r-- 1 root input 13,  0 oct 26 19:47 js0
crw-rw-r-- 1 root input 13,  1 oct 26 19:47 js1
crw-rw-r-- 1 root input 13,  2 oct 26 19:47 js2
crw-rw-r-- 1 root input 13,  3 oct 26 19:47 js3
crw-rw---- 1 root input 13, 63 oct 26 19:46 mice
crw-rw---- 1 root input 13, 32 oct 26 19:46 mouse0
crw-rw---- 1 root input 13, 33 oct 26 19:46 mouse1

I've done more findings. With fceux if i try to map the keys it does recognise the gamepad, so i can play NES games :-D

fceux.config
...
SDL.Input.GamePad.0A = 1
SDL.Input.GamePad.0B = 3
SDL.Input.GamePad.0DeviceNum = 0
SDL.Input.GamePad.0Down = 16
SDL.Input.GamePad.0Left = 13
SDL.Input.GamePad.0Right = 14
SDL.Input.GamePad.0Select = 8
SDL.Input.GamePad.0Start = 9
SDL.Input.GamePad.0TurboA = 0
SDL.Input.GamePad.0TurboB = 0
SDL.Input.GamePad.0Up = 15
...
SDL.Input.0 = GamePad.0
SDL.Input.1 = GamePad.1
SDL.Input.2 = Gamepad.2
SDL.Input.3 = Gamepad.3
SDL.Input.FTrainer.DeviceType = Keyboard
SDL.Input.FamilyKeyBoard.DeviceType = Keyboard
SDL.Input.GamePad.0DeviceType = Joystick
SDL.Input.GamePad.1DeviceType = None
SDL.Input.GamePad.2DeviceType = None
SDL.Input.GamePad.3DeviceType = None




With kodi, once i modify the keymap to add an entry with name Xbox 360 Wireless Receiver, it works fine as well

dmesg output:
[   67.917367] input: Xbox 360 Wireless Receiver as /devices/virtual/input/input6
[   67.917623] input: Xbox 360 Wireless Receiver as /devices/virtual/input/input7
[   67.917805] input: Xbox 360 Wireless Receiver as /devices/virtual/input/input8
[   67.917981] input: Xbox 360 Wireless Receiver as /devices/virtual/input/input9

But when it comes to mame, i still have something wrong :-\

If i go to key mapping menu of mame, i can see how it did automap to gampead's buttons but it doesn't read the input from the actual /dev/input/eventXX device nor can change mapping manually because when i press any button it doesn't capture the event :-?

Will be more than grateful if you can point me any direction to continue finding out what's happening under the hood.

Thanks a lot,

Regards.

---

### Post by Chris on 2015-10-26
Yeah, you can see, none of your /dev/input/eventXX devices are accessible by normal users. That's the problem. I bet if you look in the logs (dmesg/kern.log), find which event device is the joystick, do a "sudo chmod 666" on the /dev/input/eventXX that is the joystick, then it will work. At least temporarily. You will need to figure out of the proper udev rule to make it permanent. You're running a newer version of Ubuntu than me (I'm 14.04) so that may be why my udev rule isn't work for you.

On 14.04 all the event devices are owned by root:root, yours are root:input which means they changed something relating to udev (or is 15.04 on systemd, I don't know). You could add your user (kodi?) to the "input" group and that should fix it although I'm not sure of the security implications of doing that (might not be a problem). "sudo gpasswd -a kodi input", then re-login the kodi user, will accomplish that.

---

### Post by aitor-alonso on 2015-10-27
I've tried both with the chmod 666 and adding the user to the input group and none of them solved the issue :-?

Let me paste bit more info in case it comes handy

$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root     120 oct 26 19:46 by-id
drwxr-xr-x 2 root root     140 oct 26 19:46 by-path
crw-rw---- 1 root input 13, 64 oct 26 19:46 event0
crw-rw---- 1 root input 13, 65 oct 26 19:46 event1
crw-rw---- 1 root input 13, 66 oct 26 19:46 event2
crw-rw---- 1 root input 13, 67 oct 26 19:46 event3
crw-rw---- 1 root input 13, 68 oct 26 19:46 event4
crw-rw---- 1 root input 13, 69 oct 26 19:46 event5
crw-rw-rw- 1 root input 13, 70 oct 26 19:47 event6
crw-rw---- 1 root input 13, 71 oct 26 19:47 event7
crw-rw---- 1 root input 13, 72 oct 26 19:47 event8
crw-rw---- 1 root input 13, 73 oct 26 19:47 event9
crw-rw-r-- 1 root input 13,  0 oct 26 19:47 js0
crw-rw-r-- 1 root input 13,  1 oct 26 19:47 js1
crw-rw-r-- 1 root input 13,  2 oct 26 19:47 js2
crw-rw-r-- 1 root input 13,  3 oct 26 19:47 js3
crw-rw---- 1 root input 13, 63 oct 26 19:46 mice
crw-rw---- 1 root input 13, 32 oct 26 19:46 mouse0
crw-rw---- 1 root input 13, 33 oct 26 19:46 mouse1


$ udevadm info /dev/input/event6
P: /devices/virtual/input/input6/event6
N: input/event6
E: DEVNAME=/dev/input/event6
E: DEVPATH=/devices/virtual/input/input6/event6
E: ID_INPUT=1
E: ID_INPUT_JOYSTICK=1
E: ID_SERIAL=noserial
E: MAJOR=13
E: MINOR=70
E: SUBSYSTEM=input
E: TAGS=:uaccess:seat:
E: USEC_INITIALIZED=67876939


$ udevadm info /dev/input/js0
P: /devices/virtual/input/input6/js0
N: input/js0
E: DEVNAME=/dev/input/js0
E: DEVPATH=/devices/virtual/input/input6/js0
E: ID_INPUT=1
E: ID_INPUT_JOYSTICK=1
E: ID_SERIAL=noserial
E: MAJOR=13
E: MINOR=0
E: SUBSYSTEM=input
E: TAGS=:seat:uaccess:
E: USEC_INITIALIZED=67847232

$ groups xbmc
xbmc : xbmc root adm dialout cdrom audio dip video plugdev games users aitor lpadmin deluge amule downloads input


$ ps aux


xbmc     17847  0.0  0.0   4476   752 ?        S    20:01   0:00 /bin/sh -c "/usr/games/mame" -v "/var/downloads/completed/juegos/mame/pbobble2.zip"
xbmc     17848 87.4  3.3 533968 136276 ?       Rl   20:01   1:51 /usr/games/mame -v /var/downloads/completed/juegos/mame/pbobble2.zip

Then when i try to map the keys, no matter what button i press it doesn't capture it, though in the img it can be seen that it did some kind of automapping to the joystick ???

[[IMG]http://s9.postimg.org/ykggwedkb/IMG_20151027_200302.jpg[/IMG]]("http://postimg.org/image/ykggwedkb/")

---

### Post by Chris on 2015-10-27
Yeah, I believe those joystick mappings are always there as defaults.

Have you looked at the output of the "mame -v"? It might give an indication of whether or not it's finding a joystick. I would try running it from a terminal or command line, not from xbmc/Kodi, and see what it prints out when it runs. If it detects a joystick it will be listed.

---

### Post by aitor-alonso on 2015-10-28
Here we go:

cat /home/xbmc/mame.log 
Available videodrivers: x11 mir wayland dummy 
Current Videodriver: x11
	Display #0
		Renderdrivers:
			    opengl (0x0)
			 opengles2 (0x0)
			  software (0x0)
Available audio drivers: 
	pulseaudio          
	alsa                
	dsp                 
	disk                
	dummy               
Build version:      0.160 (Mar 31 2015)
Build architecure:  SDLMAME_ARCH= 
Build defines 1:    SDLMAME_UNIX=1 SDLMAME_X11=1 SDLMAME_LINUX=1 
Build defines 1:    LSB_FIRST=1 PTR64=1 DISTRO=generic SYNC_IMPLEMENTATION=tc 
SDL/OpenGL defines: SDL_COMPILEDVERSION=2002 USE_OPENGL=1 USE_DISPATCH_GL=1 
Compiler defines A: __GNUC__=4 __GNUC_MINOR__=9 __GNUC_PATCHLEVEL__=2 __VERSION__="4.9.2" 
Compiler defines B: __amd64__=1 __x86_64__=1 __unix__=1 
Compiler defines C: __USE_FORTIFY_LEVEL=0 
Enter init_monitors
Adding monitor screen0 (1920 x 1080)
Leave init_monitors
Enter sdlwindow_init
Loaded opengl shared library: <default>
Using SDL multi-window OpenGL driver (SDL 2.0+)


Hints:
	SDL_FRAMEBUFFER_ACCELERATION             (null)
	SDL_RENDER_DRIVER                        (null)
	SDL_RENDER_OPENGL_SHADERS                (null)
	SDL_RENDER_SCALE_QUALITY                 (null)
	SDL_RENDER_VSYNC                         (null)
	SDL_VIDEO_X11_XVIDMODE                   (null)
	SDL_VIDEO_X11_XINERAMA                   (null)
	SDL_VIDEO_X11_XRANDR                     (null)
	SDL_GRAB_KEYBOARD                        (null)
	SDL_VIDEO_MINIMIZE_ON_FOCUS_LOSS         (null)
	SDL_IOS_IDLE_TIMER_DISABLED              (null)
	SDL_IOS_ORIENTATIONS                     (null)
	SDL_XINPUT_ENABLED                       (null)
	SDL_GAMECONTROLLERCONFIG                 (null)
	SDL_JOYSTICK_ALLOW_BACKGROUND_EVENTS     (null)
	SDL_ALLOW_TOPMOST                        (null)
	SDL_TIMER_RESOLUTION                     (null)
	SDL_RENDER_DIRECT3D_THREADSAFE           (null)
	SDL_VIDEO_ALLOW_SCREENSAVER              1
	SDL_ACCELEROMETER_AS_JOYSTICK            (null)
	SDL_MAC_CTRL_CLICK_EMULATE_RIGHT_CLICK   (null)
	SDL_VIDEO_WIN_D3DCOMPILER                (null)
	SDL_VIDEO_WINDOW_SHARE_PIXEL_FORMAT      (null)
	SDL_VIDEO_MAC_FULLSCREEN_SPACES          (null)
	SDL_MOUSE_RELATIVE_MODE_WARP             (null)
Leave sdlwindow_init
Enter sdl_info::create
OpenGL: X.Org
OpenGL: Gallium 0.4 on AMD CEDAR (DRM 2.40.0, LLVM 3.6.2)
OpenGL: 3.0 Mesa 11.0.2
OpenGL: texture rectangle supported
OpenGL: non-power-of-2 textures supported (new method)
OpenGL: vertex buffer supported
OpenGL: pixel buffers supported
OpenGL: framebuffer object supported
OpenGL: GLSL supported, but disabled
OpenGL: max texture size 16384 x 16384
Leave sdl_info_ogl::create
Keyboard: Start initialization
Input: Adding Kbd #0: System keyboard
Keyboard: Registered System keyboard
Keyboard: End initialization
Mouse: Start initialization
Input: Adding Mouse #0: System mouse
Mouse: Registered System mouse
Mouse: End initialization
Joystick: Start initialization
Input: Adding Joy #0: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 0 mapped to logical id 1
Input: Adding Joy #1: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 1 mapped to logical id 2
Input: Adding Joy #2: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 2 mapped to logical id 3
Input: Adding Joy #3: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 3 mapped to logical id 4
Joystick: End initialization
output: unable to open output notifier file /tmp/sdlmame_out
Audio: Start initialization
Audio: Driver is alsa
Audio: frequency: 48000, channels: 2, samples: 512
sdl_create_buffers: creating stream buffer of 25600 bytes
Audio: End initialization
Region ':maincpu' created
Region ':gfx1' created
Region ':gfx2' created
Searching font Liberation Sans in -fontpath
Matching font: /usr/share/fonts/truetype/liberation/LiberationSans-Regular.ttf
OpenGL: VBO supported
OpenGL: PBO supported
OpenGL: FBO supported
OpenGL: using vid filter: 1
Region ':audiocpu' created
Region ':ensoniq.0' created
Region ':extra' created
Starting Puzzle Bobble 2 (Ver 2.3O 1995/07/31) ':'
Optional device 'oki' not found
  (missing dependencies; rescheduling)
Starting M68EC020 ':maincpu'
Starting Serial EEPROM 93C46 (64x16) ':eeprom'
Starting Video Screen ':screen'
Optional device 'finder_dummy_tag' not found
Starting gfxdecode ':gfxdecode'
Starting palette ':palette'
Starting Taito Ensoniq Sound System ':taito_en'
Starting M68000 ':audiocpu'
Starting MC68681 DUART ':duart68681'
Starting MC68681 DUART CHANNEL ':duart68681:cha'
Starting MC68681 DUART CHANNEL ':duart68681:chb'
Starting MB87078 Volume Controller ':mb87078'
Starting Speaker ':lspeaker'
  (missing dependencies; rescheduling)
Starting Speaker ':rspeaker'
  (missing dependencies; rescheduling)
Starting ES5505 ':ensoniq'
Starting Puzzle Bobble 2 (Ver 2.3O 1995/07/31) ':'
Optional device 'oki' not found
  (missing dependencies; rescheduling)
Starting Speaker ':lspeaker'
Starting Speaker ':rspeaker'
Starting Puzzle Bobble 2 (Ver 2.3O 1995/07/31) ':'
Optional device 'oki' not found
GL texture: copy 0, shader 0, dynamic 0, 320x232 320x232 [RGB32, Equal: 1, Palette: 0,
            scale 1x1, border 0, pitch 416,320/16384], bytes/pix 4
GL texture: copy 0, shader 0, dynamic 0, 320x232 320x232 [RGB32, Equal: 1, Palette: 0,
            scale 1x1, border 0, pitch 416,320/16384], bytes/pix 4
Average speed: 99.09% (5 seconds)
sdl_kill: closing audio
Enter sdlwindow_exit
Leave sdlwindow_exit
Joystick: Start deinitialization
Joystick: End deinitialization

---

### Post by Chris on 2015-10-30
Looks like it's finding the joystick so I'm not sure what's going on. I believe once I got to that point it just worked in mame. I'm trying to remember if I had to do anything else (I don't have that controller any more).

---

### Post by aitor-alonso on 2015-10-30
I've got another non-xbox joystick to test, but i remember the result was the same. I'll update once i'm back at home with logs using it instead.

Thanks a lot for your help Chris.

---

### Post by aitor-alonso on 2015-10-30
Adding same logs with a logitech wingman joystick plugged in. Result is the same. On MAME key bindings i can see it automaps to wingman's buttons but it doesn't actually capture when i press any button :(

cat /home/xbmc/mame.log 
Available videodrivers: x11 mir wayland dummy 
Current Videodriver: x11
	Display #0
		Renderdrivers:
			    opengl (0x0)
			 opengles2 (0x0)
			  software (0x0)
Available audio drivers: 
	pulseaudio          
	alsa                
	dsp                 
	disk                
	dummy               
Build version:      0.160 (Mar 31 2015)
Build architecure:  SDLMAME_ARCH= 
Build defines 1:    SDLMAME_UNIX=1 SDLMAME_X11=1 SDLMAME_LINUX=1 
Build defines 1:    LSB_FIRST=1 PTR64=1 DISTRO=generic SYNC_IMPLEMENTATION=tc 
SDL/OpenGL defines: SDL_COMPILEDVERSION=2002 USE_OPENGL=1 USE_DISPATCH_GL=1 
Compiler defines A: __GNUC__=4 __GNUC_MINOR__=9 __GNUC_PATCHLEVEL__=2 __VERSION__="4.9.2" 
Compiler defines B: __amd64__=1 __x86_64__=1 __unix__=1 
Compiler defines C: __USE_FORTIFY_LEVEL=0 
Enter init_monitors
Adding monitor screen0 (1920 x 1080)
Leave init_monitors
Enter sdlwindow_init
Loaded opengl shared library: <default>
Using SDL multi-window OpenGL driver (SDL 2.0+)


Hints:
	SDL_FRAMEBUFFER_ACCELERATION             (null)
	SDL_RENDER_DRIVER                        (null)
	SDL_RENDER_OPENGL_SHADERS                (null)
	SDL_RENDER_SCALE_QUALITY                 (null)
	SDL_RENDER_VSYNC                         (null)
	SDL_VIDEO_X11_XVIDMODE                   (null)
	SDL_VIDEO_X11_XINERAMA                   (null)
	SDL_VIDEO_X11_XRANDR                     (null)
	SDL_GRAB_KEYBOARD                        (null)
	SDL_VIDEO_MINIMIZE_ON_FOCUS_LOSS         (null)
	SDL_IOS_IDLE_TIMER_DISABLED              (null)
	SDL_IOS_ORIENTATIONS                     (null)
	SDL_XINPUT_ENABLED                       (null)
	SDL_GAMECONTROLLERCONFIG                 (null)
	SDL_JOYSTICK_ALLOW_BACKGROUND_EVENTS     (null)
	SDL_ALLOW_TOPMOST                        (null)
	SDL_TIMER_RESOLUTION                     (null)
	SDL_RENDER_DIRECT3D_THREADSAFE           (null)
	SDL_VIDEO_ALLOW_SCREENSAVER              1
	SDL_ACCELEROMETER_AS_JOYSTICK            (null)
	SDL_MAC_CTRL_CLICK_EMULATE_RIGHT_CLICK   (null)
	SDL_VIDEO_WIN_D3DCOMPILER                (null)
	SDL_VIDEO_WINDOW_SHARE_PIXEL_FORMAT      (null)
	SDL_VIDEO_MAC_FULLSCREEN_SPACES          (null)
	SDL_MOUSE_RELATIVE_MODE_WARP             (null)
Leave sdlwindow_init
Enter sdl_info::create
OpenGL: X.Org
OpenGL: Gallium 0.4 on AMD CEDAR (DRM 2.40.0, LLVM 3.6.2)
OpenGL: 3.0 Mesa 11.0.2
OpenGL: texture rectangle supported
OpenGL: non-power-of-2 textures supported (new method)
OpenGL: vertex buffer supported
OpenGL: pixel buffers supported
OpenGL: framebuffer object supported
OpenGL: GLSL supported, but disabled
OpenGL: max texture size 16384 x 16384
Leave sdl_info_ogl::create
Keyboard: Start initialization
Input: Adding Kbd #0: System keyboard
Keyboard: Registered System keyboard
Keyboard: End initialization
Mouse: Start initialization
Input: Adding Mouse #0: System mouse
Mouse: Registered System mouse
Mouse: End initialization
Joystick: Start initialization
Input: Adding Joy #0: Logitech Inc. WingMan RumblePad
Joystick: Logitech Inc. WingMan RumblePad
Joystick:   ...  5 axes, 9 buttons 1 hats 0 balls
Joystick:   ...  Physical id 0 mapped to logical id 1
Input: Adding Joy #1: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 1 mapped to logical id 2
Input: Adding Joy #2: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 2 mapped to logical id 3
Input: Adding Joy #3: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 3 mapped to logical id 4
Input: Adding Joy #4: Xbox 360 Wireless Receiver
Joystick: Xbox 360 Wireless Receiver
Joystick:   ...  4 axes, 17 buttons 0 hats 0 balls
Joystick:   ...  Physical id 4 mapped to logical id 5
Joystick: End initialization
output: unable to open output notifier file /tmp/sdlmame_out
Audio: Start initialization
Audio: Driver is alsa
Audio: frequency: 48000, channels: 2, samples: 512
sdl_create_buffers: creating stream buffer of 25600 bytes
Audio: End initialization
Region ':maincpu' created
Searching font Liberation Sans in -fontpath
Matching font: /usr/share/fonts/truetype/liberation/LiberationSans-Regular.ttf
OpenGL: VBO supported
OpenGL: PBO supported
OpenGL: FBO supported
OpenGL: using vid filter: 1
Region ':gfx1' created
Region ':gfx2' created
Region ':audiocpu' created
Region ':ensoniq.0' created
Region ':extra' created
Starting Puzzle Bobble 2 (Ver 2.3O 1995/07/31) ':'
Optional device 'oki' not found
  (missing dependencies; rescheduling)
Starting M68EC020 ':maincpu'
Starting Serial EEPROM 93C46 (64x16) ':eeprom'
Starting Video Screen ':screen'
Optional device 'finder_dummy_tag' not found
Starting gfxdecode ':gfxdecode'
Starting palette ':palette'
Starting Taito Ensoniq Sound System ':taito_en'
Starting M68000 ':audiocpu'
Starting MC68681 DUART ':duart68681'
Starting MC68681 DUART CHANNEL ':duart68681:cha'
Starting MC68681 DUART CHANNEL ':duart68681:chb'
Starting MB87078 Volume Controller ':mb87078'
Starting Speaker ':lspeaker'
  (missing dependencies; rescheduling)
Starting Speaker ':rspeaker'
  (missing dependencies; rescheduling)
Starting ES5505 ':ensoniq'
Starting Puzzle Bobble 2 (Ver 2.3O 1995/07/31) ':'
Optional device 'oki' not found
  (missing dependencies; rescheduling)
Starting Speaker ':lspeaker'
Starting Speaker ':rspeaker'
Starting Puzzle Bobble 2 (Ver 2.3O 1995/07/31) ':'
Optional device 'oki' not found
GL texture: copy 0, shader 0, dynamic 0, 320x232 320x232 [RGB32, Equal: 1, Palette: 0,
            scale 1x1, border 0, pitch 416,320/16384], bytes/pix 4
GL texture: copy 0, shader 0, dynamic 0, 320x232 320x232 [RGB32, Equal: 1, Palette: 0,
            scale 1x1, border 0, pitch 416,320/16384], bytes/pix 4
Average speed: 78.34% (20 seconds)
sdl_kill: closing audio
Sound buffer: overflows=0 underflows=250
Enter sdlwindow_exit
Leave sdlwindow_exit
Joystick: Start deinitialization
Joystick: End deinitialization


cat /var/log/kern.log
Oct 30 19:37:29 bestia kernel: [  668.376320] usb 4-3: new low-speed USB device number 5 using ohci-pci
Oct 30 19:37:29 bestia kernel: [  668.560195] usb 4-3: New USB device found, idVendor=046d, idProduct=c20a
Oct 30 19:37:29 bestia kernel: [  668.560256] usb 4-3: New USB device strings: Mfr=4, Product=32, SerialNumber=0
Oct 30 19:37:29 bestia kernel: [  668.560264] usb 4-3: Product: WingMan RumblePad
Oct 30 19:37:29 bestia kernel: [  668.560270] usb 4-3: Manufacturer: Logitech Inc.
Oct 30 19:37:39 bestia kernel: [  678.609178] logitech 0003:046D:C20A.0006: timeout initializing reports
Oct 30 19:37:39 bestia kernel: [  678.609838] input: Logitech Inc. WingMan RumblePad as /devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/0003:046D:C20A.0006/input/input10
Oct 30 19:37:39 bestia kernel: [  678.610655] logitech 0003:046D:C20A.0006: input,hidraw3: USB HID v1.10 Joystick [Logitech Inc. WingMan RumblePad] on usb-0000:00:12.0-3/input0

dmesg
[  668.376320] usb 4-3: new low-speed USB device number 5 using ohci-pci
[  668.560195] usb 4-3: New USB device found, idVendor=046d, idProduct=c20a
[  668.560256] usb 4-3: New USB device strings: Mfr=4, Product=32, SerialNumber=0
[  668.560264] usb 4-3: Product: WingMan RumblePad
[  668.560270] usb 4-3: Manufacturer: Logitech Inc.
[  678.609178] logitech 0003:046D:C20A.0006: timeout initializing reports
[  678.609838] input: Logitech Inc. WingMan RumblePad as /devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/0003:046D:C20A.0006/input/input10
[  678.610655] logitech 0003:046D:C20A.0006: input,hidraw3: USB HID v1.10 Joystick [Logitech Inc. WingMan RumblePad] on usb-0000:00:12.0-3/input0
[  678.610691] logitech 0003:046D:C20A.0006: Force feedback for Logitech variant 2 rumble devices by Anssi Hannula <anssi.hannula@gmail.com>

---

### Post by Chris on 2015-10-30
One thing that is different is that I'm using MAME 0.166 that I built myself. Could there be a change between 0.160 and 0.166?

---

### Post by aitor-alonso on 2015-10-31
I've tried with retroarch & libretro-mame installed from stable ppa (even older version than 0.160) and it works like a charm. This retroarch-joypad-autoconfig does it magic with no issue.

Again, thanks a lot for your help Chris. Now i can go back to childhood :-)

---

