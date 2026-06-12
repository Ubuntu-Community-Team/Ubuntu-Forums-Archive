---
title: "Lubuntu 17.04 - Retroarch freezes just after starting"
date: 2017-10-12
forum: Emulators
---

### Post by marcelo-milani92 on 2017-10-12
Greetings all!

Retroarch always worked for me out of the box, but with this new installation of Lubuntu for some reason, it just crashes (freezes up) just after starting, I've tried installing it from the official repositories, from the app store and from the latest '[COLOR=#333333]libretro/testing' ppa
always with the same result, I really don't think is something to do with the packages per se, because my parent's computer is running the exact same version of Lubuntu that is in my machine, and in their computer it works great from the same repository.

I'm running:
  Lubuntu 17.04 Zesty
  4.10.0-37 generic Kernel
  Intel Core i7-3610QM
  8GB of RAM
  HD4000 integrated GPU - With GT630M [/COLOR]discrete GPU [COLOR=#333333]using the latest Nvidia proprietary drivers (Prime profile on PowerSave, using the integrated GPU, [/COLOR]Nvidia GPU disabled[COLOR=#333333])

Retroarch starts up, it shows the menu, the nice blue waves animation, working great, then, after a second or two it just freezes, OpenBox can't close the window, the only way to close it it's by killing it through task manager or closing the terminal emulator window that invoked it.

This is the output of 'retroarch --verbose':
[/COLOR]```
RetroArch [INFO] :: This is RetroArch version 1.4.1 (Git d8855ca)RetroArch [INFO] :: === Build =======================================
Capabilities: MMX MMXEXT SSE1 SSE2 SSE3 SSSE3 SSE4 SSE4.2 AVX AES 
Built: Feb 26 2017
RetroArch [INFO] :: Version: 1.4.1
RetroArch [INFO] :: Git: d8855ca
RetroArch [INFO] :: =================================================
RetroArch [INFO] :: Loading default config.
RetroArch [INFO] :: Looking for config in: "/home/bryn/.config/retroarch/retroarch.cfg".
RetroArch [INFO] :: Environ SET_PIXEL_FORMAT: RGB565.
RetroArch [INFO] :: Version of libretro API: 1
RetroArch [INFO] :: Compiled against API: 1
RetroArch [INFO] :: Set audio input rate to: 29970.03 Hz.
RetroArch [INFO] :: Video @ 960x720
RetroArch [ERROR] :: Failed to connect to Wayland server.
RetroArch [INFO] :: GLX_OML_sync_control and GLX_MESA_swap_control supported, using better swap control method...
RetroArch [INFO] :: UST: 0, MSC: 0, SBC: 0
RetroArch [INFO] :: Found GL context: x
RetroArch [INFO] :: Detecting screen resolution 1920x1080.
RetroArch [INFO] :: [GLX]: X = 0, Y = 0, W = 960, H = 720.
RetroArch [INFO] :: [GLX]: Found swap function: glXSwapIntervalMESA.
RetroArch [INFO] :: [GLX]: glXSwapInterval(1)
RetroArch [INFO] :: [GL]: Vendor: Intel Open Source Technology Center, Renderer: Mesa DRI Intel(R) Ivybridge Mobile .
RetroArch [INFO] :: [GL]: Version: 3.0 Mesa 17.0.7.
RetroArch [INFO] :: GL: Using resolution 960x720
RetroArch [INFO] :: [GL]: Default shader backend found: glsl.
RetroArch [INFO] :: [Shader driver]: Using GLSL shader backend.
RetroArch [INFO] :: Checking GLSL shader support ...
RetroArch [WARN] :: [GL]: Stock GLSL shaders will be used.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: Found GLSL vertex shader.
RetroArch [INFO] :: Found GLSL fragment shader.
RetroArch [INFO] :: Linking GLSL program.
RetroArch [INFO] :: [GL]: Using 4 textures.
RetroArch [INFO] :: [GL]: Loaded 1 program(s).
RetroArch [INFO] :: [GL]: Using GL_RGB565 for texture uploads.
RetroArch [INFO] :: Found joypad driver: "udev".
RetroArch [INFO] :: Using font rendering backend: freetype.
RetroArch [INFO] :: [DBus]: Suspended screensaver via DBus.
RetroArch [INFO] :: [PulseAudio]: Requested 24576 bytes buffer, got 18432.
RetroArch [INFO] :: Found menu display driver: "menu_display_gl".
RetroArch [INFO] :: Using font rendering backend: freetype.
RetroArch [INFO] :: Using font rendering backend: freetype.
RetroArch [INFO] :: SRAM will not be saved.
RetroArch [INFO] :: Loading history file: [/home/bryn/.config/retroarch/content_history.lpl].
RetroArch [INFO] :: Loading history file: [/home/bryn/.config/retroarch/content_music_history.lpl].
RetroArch [INFO] :: Loading history file: [/home/bryn/.config/retroarch/content_video_history.lpl].
RetroArch [INFO] :: Loading history file: [/home/bryn/.config/retroarch/content_image_history.lpl].
RetroArch [INFO] :: [GL]: VSync => on
RetroArch [INFO] :: [GLX]: glXSwapInterval(1)
RetroArch [INFO] :: [GL]: VSync => on
RetroArch [INFO] :: [GLX]: glXSwapInterval(1)
RetroArch [INFO] :: [PulseAudio]: Pausing.

```

[COLOR=#333333]Maybe '[/COLOR]RetroArch [INFO] :: [PulseAudio]: Pausing.' has something to do with it? What do you guys think?

[COLOR=#333333]Again, this is very strange, I had been running Ubuntu Budgie on my machine a month or so back, and Retroarch worked a treat, as it did on vanilla Ubuntu before that.

Any help would be great, thanks guys!
[/COLOR]

---

### Post by deadflowr on 2017-10-12
*Thread moved to **Emulators***

Are you sure the problem isn't related to the Error output
```
RetroArch [ERROR] :: Failed to connect to Wayland server.
```

---

### Post by marcelo-milani92 on 2017-10-12
Sorry to have posted on the wrong section.

I think that error is to be expected, as I'm not using Wayland, just plain old X.
This line also appears on my folk's machine, which is also not running Wayland, and it works.

---

### Post by magejohnyjtp on 2017-10-23
I'm having this exact problem too, with  nearly identical output. I'm on GalliumOS (a variant of Ubuntu for chromebooks; it uses LXDM) and I'm using RetroArch 1.6.7. When I start RetroArch it opens a dimmed, unresponsive window, and I have to issue [FONT=courier new]pkill -9 retroarch[/FONT] to get it to close.

---

### Post by marcelo-milani92 on 2017-10-31
I just changed distros, currently using Xubuntu-Core, and guess what, it works now... Maybe it was something to do with Lubuntu, when installing retroarch on it I just used > sudo apt install retroarch

To install it here on Xubuntu-Core I used a command I got on a popular and reputable site about Linux here on Brazil: > [http://www.diolinux.com.br/2015/06/retroarch-todos-os-emuladores-em-um.html]("http://www.diolinux.com.br/search")

The command used was: > **sudo add-apt-repository ppa:libretro/stable -y && sudo apt-get update && sudo apt-get install retroarch retroarch-* libretro-* -y**
It will install retroarch and all of the available 'cores' it takes a while but it works.

This is the output of retroarch --verbose on my machine, now under Xubuntu-Core:

```

[INFO] RetroArch 1.6.7 (Git 8e8bdaa)
[INFO] === Build =======================================
Capabilities: MMX MMXEXT SSE1 SSE2 SSE3 SSSE3 SSE4 SSE4.2 AVX AES 
Built: Oct 24 2017
[INFO] Version: 1.6.7
[INFO] Git: 8e8bdaa
[INFO] =================================================
[INFO] [Config]: Loading default config.
[INFO] [Config]: loading config from: (null).
[INFO] Looking for config in: "/home/bryn/.config/retroarch/retroarch.cfg".
[INFO] Environ SET_PIXEL_FORMAT: RGB565.
[INFO] Version of libretro API: 1
[INFO] Compiled against API: 1
[INFO] [Audio]: Set audio input rate to: 29970.03 Hz.
[INFO] [Video]: Video @ 960x720
[ERROR] [Wayland]: Failed to connect to Wayland server.
[INFO] [GLX]: GLX_OML_sync_control and GLX_MESA_swap_control supported, using better swap control method...
[INFO] [GL]: Found GL context: x
[INFO] [GL]: Detecting screen resolution 1920x1080.
[INFO] [GLX]: X = 0, Y = 0, W = 960, H = 720.
[INFO] [GLX]: Found swap function: glXSwapIntervalMESA.
[INFO] [GLX]: glXSwapInterval(1)
[INFO] [GL]: Vendor: Intel Open Source Technology Center, Renderer: Mesa DRI Intel(R) Ivybridge Mobile .
[INFO] [GL]: Version: 3.0 Mesa 17.2.2.
[INFO] [GL]: Using resolution 960x720
[INFO] [GL]: Default shader backend found: glsl.
[INFO] [Shader driver]: Using GLSL shader backend.
[INFO] [GLSL]: Checking GLSL shader support ...
[WARN] [GL]: Stock GLSL shaders will be used.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GLSL]: Found GLSL vertex shader.
[INFO] [GLSL]: Found GLSL fragment shader.
[INFO] [GLSL]: Linking GLSL program.
[INFO] [GL]: Using 4 textures.
[INFO] [GL]: Loaded 1 program(s).
[INFO] [GL]: Using GL_RGB565 for texture uploads.
[INFO] [Joypad]: Found joypad driver: "udev".
[INFO] [Font]: Using font rendering backend: freetype.
[INFO] [DBus]: Suspended screensaver via DBus.
[INFO] [PulseAudio]: Requested 24576 bytes buffer, got 18432.
[INFO] [Menu]: Found menu display driver: "menu_display_gl".
[INFO] [Font]: Using font rendering backend: freetype.
[INFO] [Font]: Using font rendering backend: freetype.
[INFO] SRAM will not be saved.
[INFO] Loading history file: [/home/bryn/.config/retroarch/content_history.lpl].
[INFO] Loading history file: [/home/bryn/.config/retroarch/content_favorites.lpl].
[INFO] Loading history file: [/home/bryn/.config/retroarch/content_music_history.lpl].
[INFO] Loading history file: [/home/bryn/.config/retroarch/content_video_history.lpl].
[INFO] Loading history file: [/home/bryn/.config/retroarch/content_image_history.lpl].
[INFO] [GL]: VSync => on
[INFO] [GLX]: glXSwapInterval(1)
[INFO] [PulseAudio]: Unpausing.
[INFO] [GL]: VSync => on
[INFO] [GLX]: glXSwapInterval(1)
[INFO] [PulseAudio]: Pausing.

```

---

### Post by marcelo-milani92 on 2017-11-05
Well, this is odd. Retroarch just stopped working again, it worked 2 - 3 times, and then it started freezing at the start again. Still the 'retroarch --verbose' output looks to be the same.

For anyone having this problem, I found a retroarch appimage while looking for a solution on other sites:

[http://www.mediafire.com/file/00uk40lg8xmw2li/RetroArch_x86_64-1.3.4-r04.AppImage](http://www.mediafire.com/file/00uk40lg8xmw2li/RetroArch_x86_64-1.3.4-r04.AppImage)

For anyone that doesn't know what an appimage is go here: [https://appimage.org/](https://appimage.org/)

Just mark it as executable and run it, I don't think this is the most recent version of Retroarch, but it works, at least for now while we don't figure out what is going on with the PPA version.

---

### Post by kostkon on 2017-11-05
There is also a snap package you could try:
```
sudo snap install retroarch
```

---

