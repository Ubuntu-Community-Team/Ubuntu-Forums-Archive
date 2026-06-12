---
title: "bsnes 0.048 (Super Nintendo Emulator) released!"
date: 2009-07-12
forum: Gaming &amp; Leisure
---

### Post by dfreer on 2009-07-12
I created this thread to inform Ubuntu users about an alternative to ZSNES/snes9x, since it seems not much is mentioned/known about bsnes around these parts.

For those of you who have used ZSNES in the past but have yet to try bsnes, I'd suggest giving it a whirl. While ZSNES is great, and still very much an important SNES emulator, bsnes has come a long way in a relatively short amount of time. 

bsnes is, as far as I'm aware, the most accurate SNES emulator to date. Let me give you an uneducated rundown: Only three titles unplayable (each requiring special co-processors that have yet to be reverse-engineered by *anyone*), accurate sound core (snesGT and snes9x both have this I believe), save-state support for most titles, cheat code support, runs on the major three platforms (Windows/Mac/Linux).

It does require a beefy processor; Minimum Recommended CPU being a Intel Core Solo. If your processor isn't up to snuff, ZSNES is still a great alternative. Keep an eye out for bsnes though as the emulator is very much under active development, and optimizations will push the CPU requirements down even further.

From byuu's Homepage:
> 
Starting with this release, I wish to take bsnes in a new direction. It has always excelled in accuracy, as the only SNES emulator to offer a full 100% compatibility rate with all known commercial software. But over the years, it has also gained an impressive array of features and enhancements not found anywhere else. It is also the only actively developed SNES emulator with rapid, periodic releases. Its only achilles heel is the steep system requirements, which is quickly being overcome by aggressive new optimizations and steadily-increasing hardware speeds.

In an effort to make bsnes even more accessible to everyone, starting with this release, bsnes is now fully open source software, licensed under the terms of the GNU General Public License. I would like to work toward positioning bsnes as a truly general use emulator, and would welcome any help with this.

Specifically, I am looking for an interested Debian maintainer to package bsnes for Linux users; as well as for anyone interested in helping to optimize and improve bsnes as a whole. It also seems that many still do not know about bsnes, I'd appreciate advice and help on spreading the word. Please leave a message on my forum if you are interested.

I would also welcome and support any forks that target specific areas: a speed-oriented version, a tool-assisted speedrun version, netplay bindings, and so on. As part of this targeting, I've also released a custom debugger-enabled version, which trades a bit of speed in turn for best-in-class debugging capabilities.

Please check back here over the following few days, I'll be writing up documentation explaining all of the various unique features of bsnes, as well as detailed compilation instructions for programmers.
Changelog:

    * corrected a small bug in HDMA processing; fixes College Football '97 flickering
    * corrected ROMBR and PBR SuperFX register masking; fixes Voxel demo [MooglyGuy]
    * DSP-4 driver AI bug fixed [Jonas Quinn]
    * added save state support to the S-DD1, S-RTC, DSP-1, DSP-2 and ST-0010 co-processors
    * fixed a freeze issue when the S-SMP encounters STOP and SLEEP opcodes
    * Cx4 save states no longer need floating-point values, and are thus fully portable now
    * added new custom file loading dialog; allows non-modal usage, screenshot previews and ROM info summary, among many other benefits
    * added support for IPS soft-patching
    * added blargg's File_Extractor library
    * added support for archives compressed using 7-zip, RAR and BZip2; which is in addition to existing support for Gzip, ZIP and JMA
    * state manager now properly updates the timestamp column on saves [FitzRoy]
    * added OpenGL renderer to OS X port
    * fixed system beep issue with keyboard input on OS X port
    * fixed menubar visibility issue on OS X port
    * fixed a Display handle leak on Linux port [snzzbk]
    * X-video driver now releases SHM memory properly upon exit [emon]
    * fixed Direct3D rendering issue that was blurring video on some cards [Fes]
    * enhanced window positioning code for all platforms
    * debugger is now GUI-driven instead of via command-line
    * memory hex editor is now fully usable
    * added PPU video RAM viewer to debugger
    * added S-CPU and S-SMP tracing capabilities to debugger
    * Qt version upgraded to 4.5.2, and compiled with optimizations enabled; runs faster but makes the binary slightly larger
    * too many code cleanups to list

EDIT: the user manual is now up. Please have a look, perhaps there are features there which you weren't aware of ;)


Download here:
[http://www.byuu.org/](http://www.byuu.org/)

EDIT: Edited original post to reflect current status.

---

### Post by Grishka on 2009-07-12
the ['blank file browser window'](http://board.byuu.org/viewtopic.php?f=3&t=128) bug still persists... 64-bit folks have to run the game directly, ie. bsnes ./rudra.smc, not from the file open menu.

---

### Post by byuu on 2009-07-13
I cannot reproduce this bug on my system, 64-bit Xubuntu 9.04. I have triple-checked my file loading code, src/ui_qt/utility/cartridge.cpp:
```
  QString filename = QFileDialog::getOpenFileName(0,
    "Load Cartridge",
    (config.path.rom != "" ? config.path.rom : config.path.current),
    "SNES images (*.smc *.sfc *.swc *.fig *.bs *.st"
    #if defined(GZIP_SUPPORT)
    " *.zip *.gz"
    #endif
    #if defined(JMA_SUPPORT)
    " *.jma"
    #endif
    ");;"
    "All files (*)"
  );
```I would appreciate if someone who is experiencing this error could assist in debugging it.

EDIT: new info on my forum. It's (most likely) not a bug on bsnes' side.

> System -> Preferences -> Qt4 Settings, Select GUI Style choose Plastique.If you guys could please confirm the version of QGtkStyle in use ... I was told by the Qt developer who made QGtkStyle that this was a known bug in v4.4, and indeed I experienced it back then as well. I don't see this bug in Xubuntu, so perhaps mainline Ubuntu is still using the outdated version of QGtkStyle?

If you guys *do* have QGtkStyle v4.5, I'll try and get in contact with the theme maintainer about this.

One last workaround would be to manually specify a ROM path (settings->config->paths) so that it doesn't default you to "". That should take care of it as well.

---

### Post by mister_playboy on 2009-07-20
Minimum 2.0 GHz dual core processor for SNES games?  I only have a 1.87GHz dual core... :(

I'll take a look when I get a proper computer...lol.

---

### Post by byuu on 2009-07-21
Okay, the file dialog issue has been resolved:
[http://code.google.com/p/qgtkstyle/issues/detail?id=85](http://code.google.com/p/qgtkstyle/issues/detail?id=85)
It will be fixed in the next official version of Qt. The workaround for now is to edit src/ui_qt/utility/cartridge.cpp. Replace the first function with this one:

```
string Utility::selectCartridge() {
  audio.clear();
  application.timer->stop();
  QString filename = QFileDialog::getOpenFileName(0,
    "Load Cartridge",
    utf8() << (config.path.rom != "" ? config.path.rom : config.path.current),
    "SNES images (*.smc *.sfc *.swc *.fig *.bs *.st"
    #if defined(GZIP_SUPPORT)
    " *.zip *.gz"
    #endif
    #if defined(JMA_SUPPORT)
    " *.jma"
    #endif
    ");;"
    "All files (*)"
  );
  application.timer->start(0);

  string name = filename.toUtf8().constData();
  if(strlen(name) > 0) config.path.current = basepath(name);
  return name;
}
```Or you can wait for v049 ... perhaps this weekend or next ;)

Many thanks to the QGtkStyle author, jensbw, for both fixing this as well as coming up with a workaround for bsnes!

> Minimum 2.0 GHz dual core processor for SNES games?  I only have a 1.87GHz dual core...The minimum specs are intentionally set higher than required, to ensure all games always run at full speed. 1.87GHz should be more than enough. I get 160-190fps at 3GHz. It also only uses / needs one core.

The slowest processor you can get fullspeed on right now is an AMD Athlon or Sempron 2600+.

As a Linux user, be sure to change your video driver to either OpenGL or X-Video, as the default SDL driver is notoriously slow.

---

### Post by Nevon on 2009-07-21
Maybe I'm dumb, but how exactly do I install this? Running *make* only gives me:
```
nevon@loltop:~/Desktop/src$ make
rcc ui_qt/resource/resource.qrc -o ui_qt/resource/resource.rcc
make: rcc: Command not found
make: *** [ui_qt/resource/resource.rcc] Error 127
```

---

### Post by tukuyomi on 2009-07-21
You have to install qt4-qmake, libqt4-dev, and build-essential

@ mister_playboy: bsnes is quite different from others emulators, as it focuses on accuracy, hence higher system requirements :)

---

### Post by byuu on 2009-07-21
> how exactly do I install this?

On a related tangent, are there any reputable maintainers here who would be willing to add bsnes to the official Debian and/or Ubuntu repos? We can discuss a license that will be compatible with that. If so, please catch me on irc.freenode.net.

---

### Post by hikaricore on 2009-07-21
> **byuu said:**
> On a related tangent, are there any reputable maintainers here who would be willing to add bsnes to the official Debian and/or Ubuntu repos? We can discuss a license that will be compatible with that. If so, please catch me on irc.freenode.net.

Probably best to make the request on Launchpad.
Devs and maintainers don't really read the gaming forum.  :)

---

### Post by mister_playboy on 2009-07-21
> **tukuyomi said:**
> You have to install qt4-qmake, libqt4-dev, and build-essential

@ mister_playboy: bsnes is quite different from others emulators, as it focuses on accuracy, hence higher system requirements :)

Okay... when I try to build it, I get this pile of errors :confused::

```
mister7playboy@VGN-NR430E:~/Desktop/src$ make
rcc ui_qt/resource/resource.qrc -o ui_qt/resource/resource.rcc
moc -f ui_qt/application/application.moc.hpp -o ui_qt/application/application.moc
moc -f ui_qt/base/about.moc.hpp -o ui_qt/base/about.moc
moc -f ui_qt/base/htmlviewer.moc.hpp -o ui_qt/base/htmlviewer.moc
moc -f ui_qt/base/loader.moc.hpp -o ui_qt/base/loader.moc
moc -f ui_qt/base/main.moc.hpp -o ui_qt/base/main.moc
moc -f ui_qt/settings/advanced.moc.hpp -o ui_qt/settings/advanced.moc
moc -f ui_qt/settings/audio.moc.hpp -o ui_qt/settings/audio.moc
moc -f ui_qt/settings/input.moc.hpp -o ui_qt/settings/input.moc
moc -f ui_qt/settings/paths.moc.hpp -o ui_qt/settings/paths.moc
moc -f ui_qt/settings/settings.moc.hpp -o ui_qt/settings/settings.moc
moc -f ui_qt/settings/utility/inputcapture.moc.hpp -o ui_qt/settings/utility/inputcapture.moc
moc -f ui_qt/settings/video.moc.hpp -o ui_qt/settings/video.moc
moc -f ui_qt/tools/cheateditor.moc.hpp -o ui_qt/tools/cheateditor.moc
moc -f ui_qt/tools/statemanager.moc.hpp -o ui_qt/tools/statemanager.moc
moc -f ui_qt/tools/tools.moc.hpp -o ui_qt/tools/tools.moc
g++ -O3 -fomit-frame-pointer -Ilib `pkg-config --cflags QtCore QtGui` -c ui_qt/main.cpp -o obj/main.o
gcc -O3 -fomit-frame-pointer -static -Ilib -c lib/libco/libco.c -o obj/libco.o
g++ -O3 -fomit-frame-pointer -Ilib -DVIDEO_GLX -DVIDEO_XV -DVIDEO_SDL -DVIDEO_QTIMAGE -DAUDIO_ALSA -DAUDIO_OPENAL -DAUDIO_OSS -DAUDIO_PULSEAUDIO -DAUDIO_AO -DINPUT_SDL -DINPUT_X `sdl-config --cflags` `pkg-config --cflags QtCore QtGui` -c lib/ruby/ruby.cpp -o obj/ruby.o
/bin/sh: sdl-config: not found
In file included from lib/ruby/ruby_impl.cpp:64,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/video/sdl.cpp:3:31: error: X11/extensions/Xv.h: No such file or directory
lib/ruby/video/sdl.cpp:4:34: error: X11/extensions/Xvlib.h: No such file or directory
lib/ruby/video/sdl.cpp:6:21: error: SDL/SDL.h: No such file or directory
In file included from lib/ruby/ruby_impl.cpp:101,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/ao.cpp:6:19: error: ao/ao.h: No such file or directory
In file included from lib/ruby/ruby_impl.cpp:109,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/openal.cpp:11:21: error: AL/al.h: No such file or directory
lib/ruby/audio/openal.cpp:12:22: error: AL/alc.h: No such file or directory
In file included from lib/ruby/ruby_impl.cpp:117,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/pulseaudio.cpp:6:26: error: pulse/simple.h: No such file or directory
lib/ruby/audio/pulseaudio.cpp:7:25: error: pulse/error.h: No such file or directory
In file included from lib/ruby/ruby_impl.cpp:64,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/video/sdl.cpp:13: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
lib/ruby/video/sdl.cpp:13: error: expected ‘;’ before ‘*’ token
lib/ruby/video/sdl.cpp: In member function ‘void ruby::pVideoSDL::resize(unsigned int, unsigned int)’:
lib/ruby/video/sdl.cpp:48: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:48: error: ‘SDL_FreeSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp:49: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:50: error: ‘SDL_SWSURFACE’ was not declared in this scope
lib/ruby/video/sdl.cpp:52: error: ‘SDL_CreateRGBSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp: In member function ‘bool ruby::pVideoSDL::lock(uint32_t*&, unsigned int&, unsigned int, unsigned int)’:
lib/ruby/video/sdl.cpp:60: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:60: error: ‘SDL_MUSTLOCK’ was not declared in this scope
lib/ruby/video/sdl.cpp:60: error: ‘SDL_LockSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp:61: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp: In member function ‘void ruby::pVideoSDL::unlock()’:
lib/ruby/video/sdl.cpp:66: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:66: error: ‘SDL_MUSTLOCK’ was not declared in this scope
lib/ruby/video/sdl.cpp:66: error: ‘SDL_UnlockSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp: In member function ‘void ruby::pVideoSDL::clear()’:
lib/ruby/video/sdl.cpp:70: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:70: error: ‘SDL_MUSTLOCK’ was not declared in this scope
lib/ruby/video/sdl.cpp:70: error: ‘SDL_LockSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp:72: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:75: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:75: error: ‘SDL_MUSTLOCK’ was not declared in this scope
lib/ruby/video/sdl.cpp:75: error: ‘SDL_UnlockSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp: In member function ‘void ruby::pVideoSDL::refresh()’:
lib/ruby/video/sdl.cpp:83: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:83: error: ‘SDL_MUSTLOCK’ was not declared in this scope
lib/ruby/video/sdl.cpp:83: error: ‘SDL_LockSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp:85: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:88: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:88: error: ‘SDL_MUSTLOCK’ was not declared in this scope
lib/ruby/video/sdl.cpp:88: error: ‘SDL_UnlockSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp:93: error: ‘SDL_Rect’ was not declared in this scope
lib/ruby/video/sdl.cpp:93: error: expected `;' before ‘src’
lib/ruby/video/sdl.cpp:95: error: ‘src’ was not declared in this scope
lib/ruby/video/sdl.cpp:100: error: ‘dest’ was not declared in this scope
lib/ruby/video/sdl.cpp:105: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:105: error: ‘screen’ was not declared in this scope
lib/ruby/video/sdl.cpp:105: error: ‘SDL_SoftStretch’ was not declared in this scope
lib/ruby/video/sdl.cpp:106: error: ‘SDL_UpdateRect’ was not declared in this scope
lib/ruby/video/sdl.cpp: In member function ‘bool ruby::pVideoSDL::init()’:
lib/ruby/video/sdl.cpp:116: error: ‘SDL_INIT_VIDEO’ was not declared in this scope
lib/ruby/video/sdl.cpp:116: error: ‘SDL_InitSubSystem’ was not declared in this scope
lib/ruby/video/sdl.cpp:117: error: ‘screen’ was not declared in this scope
lib/ruby/video/sdl.cpp:117: error: ‘SDL_HWSURFACE’ was not declared in this scope
lib/ruby/video/sdl.cpp:117: error: ‘SDL_SetVideoMode’ was not declared in this scope
lib/ruby/video/sdl.cpp:119: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp: In member function ‘void ruby::pVideoSDL::term()’:
lib/ruby/video/sdl.cpp:129: error: ‘buffer’ was not declared in this scope
lib/ruby/video/sdl.cpp:129: error: ‘SDL_FreeSurface’ was not declared in this scope
lib/ruby/video/sdl.cpp:130: error: ‘SDL_INIT_VIDEO’ was not declared in this scope
lib/ruby/video/sdl.cpp:130: error: ‘SDL_QuitSubSystem’ was not declared in this scope
In file included from lib/ruby/ruby_impl.cpp:72,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/video/xv.cpp: At global scope:
lib/ruby/video/xv.cpp:7: error: expected constructor, destructor, or type conversion before ‘*’ token
lib/ruby/video/xv.cpp:37: error: ISO C++ forbids declaration of ‘XvImage’ with no type
lib/ruby/video/xv.cpp:37: error: expected ‘;’ before ‘*’ token
lib/ruby/video/xv.cpp: In member function ‘bool ruby::pVideoXv::set(const nall::string&, const nall::any&)’:
lib/ruby/video/xv.cpp:75: error: ‘XvSetPortAttribute’ was not declared in this scope
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::refresh()’:
lib/ruby/video/xv.cpp:131: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:134: error: ‘XvShmPutImage’ was not declared in this scope
lib/ruby/video/xv.cpp: In member function ‘bool ruby::pVideoXv::init()’:
lib/ruby/video/xv.cpp:147: error: ‘XvAdaptorInfo’ was not declared in this scope
lib/ruby/video/xv.cpp:147: error: ‘adaptor_info’ was not declared in this scope
lib/ruby/video/xv.cpp:149: error: ‘XvQueryAdaptors’ was not declared in this scope
lib/ruby/video/xv.cpp:153: error: ‘XvInputMask’ was not declared in this scope
lib/ruby/video/xv.cpp:154: error: ‘XvImageMask’ was not declared in this scope
lib/ruby/video/xv.cpp:161: error: ‘XvFreeAdaptorInfo’ was not declared in this scope
lib/ruby/video/xv.cpp:203: error: ‘XvSetPortAttribute’ was not declared in this scope
lib/ruby/video/xv.cpp:208: error: ‘XvImageFormatValues’ was not declared in this scope
lib/ruby/video/xv.cpp:208: error: ‘format’ was not declared in this scope
lib/ruby/video/xv.cpp:208: error: ‘XvListImageFormats’ was not declared in this scope
lib/ruby/video/xv.cpp:211: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:219: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:227: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:235: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:243: error: ‘XvYUV’ was not declared in this scope
lib/ruby/video/xv.cpp:243: error: ‘XvPacked’ was not declared in this scope
lib/ruby/video/xv.cpp:255: error: ‘XvYUV’ was not declared in this scope
lib/ruby/video/xv.cpp:255: error: ‘XvPacked’ was not declared in this scope
lib/ruby/video/xv.cpp:272: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:272: error: ‘XvShmCreateImage’ was not declared in this scope
lib/ruby/video/xv.cpp:273: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:278: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:279: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb32(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:315: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb24(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:326: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb16(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:343: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb15(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:358: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_yuy2(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:373: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_uyvy(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:396: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
In file included from lib/ruby/ruby_impl.cpp:101,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/ao.cpp: At global scope:
lib/ruby/audio/ao.cpp:13: error: ‘ao_sample_format’ does not name a type
lib/ruby/audio/ao.cpp:14: error: ISO C++ forbids declaration of ‘ao_device’ with no type
lib/ruby/audio/ao.cpp:14: error: expected ‘;’ before ‘*’ token
lib/ruby/audio/ao.cpp: In member function ‘bool ruby::pAudioAO::set(const nall::string&, const nall::any&)’:
lib/ruby/audio/ao.cpp:33: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp: In member function ‘void ruby::pAudioAO::sample(uint16_t, uint16_t)’:
lib/ruby/audio/ao.cpp:42: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:42: error: ‘ao_play’ was not declared in this scope
lib/ruby/audio/ao.cpp: In member function ‘bool ruby::pAudioAO::init()’:
lib/ruby/audio/ao.cpp:51: error: ‘ao_default_driver_id’ was not declared in this scope
lib/ruby/audio/ao.cpp:54: error: ‘driver_format’ was not declared in this scope
lib/ruby/audio/ao.cpp:57: error: ‘AO_FMT_LITTLE’ was not declared in this scope
lib/ruby/audio/ao.cpp:59: error: ‘ao_option’ was not declared in this scope
lib/ruby/audio/ao.cpp:59: error: ‘options’ was not declared in this scope
lib/ruby/audio/ao.cpp:60: error: ‘ao_info’ was not declared in this scope
lib/ruby/audio/ao.cpp:60: error: ‘di’ was not declared in this scope
lib/ruby/audio/ao.cpp:60: error: ‘ao_driver_info’ was not declared in this scope
lib/ruby/audio/ao.cpp:63: error: ‘ao_append_option’ was not declared in this scope
lib/ruby/audio/ao.cpp:66: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:66: error: ‘ao_open_live’ was not declared in this scope
lib/ruby/audio/ao.cpp: In member function ‘void ruby::pAudioAO::term()’:
lib/ruby/audio/ao.cpp:73: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:74: error: ‘ao_close’ was not declared in this scope
lib/ruby/audio/ao.cpp: In constructor ‘ruby::pAudioAO::pAudioAO()’:
lib/ruby/audio/ao.cpp:80: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:81: error: ‘ao_initialize’ was not declared in this scope
In file included from lib/ruby/ruby_impl.cpp:109,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/openal.cpp: At global scope:
lib/ruby/audio/openal.cpp:20: error: ISO C++ forbids declaration of ‘ALCdevice’ with no type
lib/ruby/audio/openal.cpp:20: error: expected ‘;’ before ‘*’ token
lib/ruby/audio/openal.cpp:21: error: ISO C++ forbids declaration of ‘ALCcontext’ with no type
lib/ruby/audio/openal.cpp:21: error: expected ‘;’ before ‘*’ token
lib/ruby/audio/openal.cpp:22: error: ‘ALuint’ does not name a type
lib/ruby/audio/openal.cpp:23: error: ‘ALenum’ does not name a type
lib/ruby/audio/openal.cpp: In member function ‘void ruby::pAudioOpenAL::sample(uint16_t, uint16_t)’:
lib/ruby/audio/openal.cpp:80: error: ‘ALuint’ was not declared in this scope
lib/ruby/audio/openal.cpp:80: error: expected `;' before ‘albuffer’
lib/ruby/audio/openal.cpp:83: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:83: error: ‘AL_BUFFERS_PROCESSED’ was not declared in this scope
lib/ruby/audio/openal.cpp:83: error: ‘alGetSourcei’ was not declared in this scope
lib/ruby/audio/openal.cpp:85: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:85: error: ‘albuffer’ was not declared in this scope
lib/ruby/audio/openal.cpp:85: error: ‘alSourceUnqueueBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:86: error: ‘alDeleteBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:94: error: ‘albuffer’ was not declared in this scope
lib/ruby/audio/openal.cpp:94: error: ‘alGenBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:95: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘format’
lib/ruby/audio/openal.cpp:95: error: ‘alBufferData’ was not declared in this scope
lib/ruby/audio/openal.cpp:96: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:96: error: ‘alSourceQueueBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:100: error: ‘ALint’ was not declared in this scope
lib/ruby/audio/openal.cpp:100: error: expected `;' before ‘playing’
lib/ruby/audio/openal.cpp:101: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:101: error: ‘AL_SOURCE_STATE’ was not declared in this scope
lib/ruby/audio/openal.cpp:101: error: ‘playing’ was not declared in this scope
lib/ruby/audio/openal.cpp:101: error: ‘alGetSourcei’ was not declared in this scope
lib/ruby/audio/openal.cpp:102: error: ‘AL_PLAYING’ was not declared in this scope
lib/ruby/audio/openal.cpp:102: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:102: error: ‘alSourcePlay’ was not declared in this scope
lib/ruby/audio/openal.cpp: In member function ‘bool ruby::pAudioOpenAL::init()’:
lib/ruby/audio/openal.cpp:120: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:120: error: ‘alcOpenDevice’ was not declared in this scope
lib/ruby/audio/openal.cpp:121: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:121: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:121: error: ‘alcCreateContext’ was not declared in this scope
lib/ruby/audio/openal.cpp:122: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:122: error: ‘alcMakeContextCurrent’ was not declared in this scope
lib/ruby/audio/openal.cpp:123: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:123: error: ‘alGenSources’ was not declared in this scope
lib/ruby/audio/openal.cpp:133: error: ‘AL_POSITION’ was not declared in this scope
lib/ruby/audio/openal.cpp:133: error: ‘alListener3f’ was not declared in this scope
lib/ruby/audio/openal.cpp:134: error: ‘AL_VELOCITY’ was not declared in this scope
lib/ruby/audio/openal.cpp:135: error: ‘ALfloat’ was not declared in this scope
lib/ruby/audio/openal.cpp:135: error: expected `;' before ‘listener_orientation’
lib/ruby/audio/openal.cpp:136: error: ‘AL_ORIENTATION’ was not declared in this scope
lib/ruby/audio/openal.cpp:136: error: ‘listener_orientation’ was not declared in this scope
lib/ruby/audio/openal.cpp:136: error: ‘alListenerfv’ was not declared in this scope
lib/ruby/audio/openal.cpp: In member function ‘void ruby::pAudioOpenAL::term()’:
lib/ruby/audio/openal.cpp:151: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:151: error: ‘alIsSource’ was not declared in this scope
lib/ruby/audio/openal.cpp:151: error: ‘AL_TRUE’ was not declared in this scope
lib/ruby/audio/openal.cpp:153: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:153: error: ‘AL_SOURCE_STATE’ was not declared in this scope
lib/ruby/audio/openal.cpp:153: error: ‘alGetSourcei’ was not declared in this scope
lib/ruby/audio/openal.cpp:154: error: ‘AL_PLAYING’ was not declared in this scope
lib/ruby/audio/openal.cpp:155: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:155: error: ‘alSourceStop’ was not declared in this scope
lib/ruby/audio/openal.cpp:157: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:157: error: ‘AL_BUFFERS_QUEUED’ was not declared in this scope
lib/ruby/audio/openal.cpp:159: error: ‘ALuint’ was not declared in this scope
lib/ruby/audio/openal.cpp:159: error: expected `;' before ‘albuffer’
lib/ruby/audio/openal.cpp:160: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:160: error: ‘albuffer’ was not declared in this scope
lib/ruby/audio/openal.cpp:160: error: ‘alSourceUnqueueBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:161: error: ‘alDeleteBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:166: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:166: error: ‘alDeleteSources’ was not declared in this scope
lib/ruby/audio/openal.cpp:167: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:170: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:171: error: ‘alcMakeContextCurrent’ was not declared in this scope
lib/ruby/audio/openal.cpp:172: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:172: error: ‘alcDestroyContext’ was not declared in this scope
lib/ruby/audio/openal.cpp:173: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:176: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:177: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:177: error: ‘alcCloseDevice’ was not declared in this scope
lib/ruby/audio/openal.cpp:178: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp: In constructor ‘ruby::pAudioOpenAL::pAudioOpenAL()’:
lib/ruby/audio/openal.cpp:188: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:189: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:190: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:191: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘format’
lib/ruby/audio/openal.cpp:191: error: ‘AL_FORMAT_STEREO16’ was not declared in this scope
In file included from lib/ruby/ruby_impl.cpp:117,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/pulseaudio.cpp: At global scope:
lib/ruby/audio/pulseaudio.cpp:14: error: ISO C++ forbids declaration of ‘pa_simple’ with no type
lib/ruby/audio/pulseaudio.cpp:14: error: expected ‘;’ before ‘*’ token
lib/ruby/audio/pulseaudio.cpp:15: error: ‘pa_sample_spec’ does not name a type
lib/ruby/audio/pulseaudio.cpp: In member function ‘bool ruby::pAudioPulseAudio::set(const nall::string&, const nall::any&)’:
lib/ruby/audio/pulseaudio.cpp:40: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp: In member function ‘void ruby::pAudioPulseAudio::sample(uint16_t, uint16_t)’:
lib/ruby/audio/pulseaudio.cpp:48: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp:53: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp:53: error: ‘pa_simple_write’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp: In member function ‘bool ruby::pAudioPulseAudio::init()’:
lib/ruby/audio/pulseaudio.cpp:64: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘spec’
lib/ruby/audio/pulseaudio.cpp:64: error: ‘PA_SAMPLE_S16LE’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp:65: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘spec’
lib/ruby/audio/pulseaudio.cpp:66: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘spec’
lib/ruby/audio/pulseaudio.cpp:69: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp:72: error: ‘PA_STREAM_PLAYBACK’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp:75: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘spec’
lib/ruby/audio/pulseaudio.cpp:79: error: ‘pa_simple_new’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp:80: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp:81: error: ‘pa_strerror’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp: In member function ‘void ruby::pAudioPulseAudio::term()’:
lib/ruby/audio/pulseaudio.cpp:91: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp:93: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp:93: error: ‘pa_simple_flush’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp:94: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp:94: error: ‘pa_simple_free’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp:95: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/pulseaudio.cpp: In constructor ‘ruby::pAudioPulseAudio::pAudioPulseAudio()’:
lib/ruby/audio/pulseaudio.cpp:105: error: ‘struct ruby::pAudioPulseAudio::<anonymous>’ has no member named ‘handle’
In file included from lib/ruby/ruby_impl.cpp:153,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/input/sdl.cpp: At global scope:
lib/ruby/input/sdl.cpp:21: error: ISO C++ forbids declaration of ‘SDL_Joystick’ with no type
lib/ruby/input/sdl.cpp:21: error: expected ‘;’ before ‘*’ token
lib/ruby/input/sdl.cpp: In member function ‘bool ruby::pInputSDL::poll(int16_t*)’:
lib/ruby/input/sdl.cpp:152: error: ‘SDL_JoystickUpdate’ was not declared in this scope
lib/ruby/input/sdl.cpp:154: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:158: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:158: error: ‘SDL_JoystickNumHats’ was not declared in this scope
lib/ruby/input/sdl.cpp:160: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:160: error: ‘SDL_JoystickGetHat’ was not declared in this scope
lib/ruby/input/sdl.cpp:161: error: ‘SDL_HAT_UP’ was not declared in this scope
lib/ruby/input/sdl.cpp:162: error: ‘SDL_HAT_RIGHT’ was not declared in this scope
lib/ruby/input/sdl.cpp:163: error: ‘SDL_HAT_DOWN’ was not declared in this scope
lib/ruby/input/sdl.cpp:164: error: ‘SDL_HAT_LEFT’ was not declared in this scope
lib/ruby/input/sdl.cpp:168: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:168: error: ‘SDL_JoystickNumAxes’ was not declared in this scope
lib/ruby/input/sdl.cpp:170: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:170: error: ‘SDL_JoystickGetAxis’ was not declared in this scope
lib/ruby/input/sdl.cpp:175: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:175: error: ‘SDL_JoystickGetButton’ was not declared in this scope
lib/ruby/input/sdl.cpp: In member function ‘bool ruby::pInputSDL::init()’:
lib/ruby/input/sdl.cpp:184: error: ‘SDL_INIT_JOYSTICK’ was not declared in this scope
lib/ruby/input/sdl.cpp:184: error: ‘SDL_InitSubSystem’ was not declared in this scope
lib/ruby/input/sdl.cpp:185: error: ‘SDL_IGNORE’ was not declared in this scope
lib/ruby/input/sdl.cpp:185: error: ‘SDL_JoystickEventState’ was not declared in this scope
lib/ruby/input/sdl.cpp:211: error: ‘SDL_NumJoysticks’ was not declared in this scope
lib/ruby/input/sdl.cpp:212: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:212: error: ‘SDL_JoystickOpen’ was not declared in this scope
lib/ruby/input/sdl.cpp: In member function ‘void ruby::pInputSDL::term()’:
lib/ruby/input/sdl.cpp:222: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:222: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:222: error: ‘SDL_JoystickClose’ was not declared in this scope
lib/ruby/input/sdl.cpp:223: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
lib/ruby/input/sdl.cpp:226: error: ‘SDL_INIT_JOYSTICK’ was not declared in this scope
lib/ruby/input/sdl.cpp:226: error: ‘SDL_QuitSubSystem’ was not declared in this scope
lib/ruby/input/sdl.cpp: In constructor ‘ruby::pInputSDL::pInputSDL()’:
lib/ruby/input/sdl.cpp:230: error: ‘struct ruby::pInputSDL::<anonymous>’ has no member named ‘gamepad’
make: *** [obj/ruby.o] Error 1
```

---

### Post by Grishka on 2009-07-21
> **mister_playboy said:**
> Okay... when I try to build it, I get this pile of errors :confused::

[apt://libsdl1.2-dev](apt://libsdl1.2-dev), [apt://libxv-dev](apt://libxv-dev), [apt://libao-dev](apt://libao-dev), [apt://libpulse-dev](apt://libpulse-dev).

---

### Post by byuu on 2009-07-21
You're missing lots of libs.

sudo apt-get install build-essential libqt4-dev libsdl1.2-dev libpulse-dev libasound-dev libxtst-dev libxv-dev libopenal-dev libao-dev libxv-dev
make enable_gzip=true enable_jma=true
sudo make install

---

### Post by stillious on 2009-07-21
Yay, save states :D

---

### Post by mister_playboy on 2009-07-21
> **byuu said:**
> You're missing lots of libs.

sudo apt-get install build-essential libqt4-dev libsdl1.2-dev libpulse-dev libasound-dev libxtst-dev libxv-dev libopenal-dev libao-dev libxv-dev
make enable_gzip=true enable_jma=true
sudo make install

Ah, okay.  I had only got the ones mentioned previously in the thread.  I didn't see any list of deps on the webpage... :oops:

Anyway, it does start up, but I'm having some trouble setting the file paths... I can't type directly in the box, and hitting the "select" button gives me this:

[[IMG]http://img43.imageshack.us/img43/1623/screenshotqzt.th.png[/IMG]](http://img43.imageshack.us/i/screenshotqzt.png/)

Did something go wrong in the build?

---

### Post by mister_playboy on 2009-07-21
> **Grishka said:**
> the ['blank file browser window'](http://board.byuu.org/viewtopic.php?f=3&t=128) bug still persists... 64-bit folks have to run the game directly, ie. bsnes ./rudra.smc, not from the file open menu.

I see this is the same problem I have.  I'm on 64-bit Ubuntu 9.04.

**EDIT** Changing QT's GUI to Plastique solved the problem.

---

### Post by byuu on 2009-07-21
>  Anyway, it does start up, but I'm having some trouble setting the file paths... I can't type directly in the box, and hitting the "select" button gives me this:I mentioned that on the previous page >_>'

The file dialog box is broken due to a bug in QGtkStyle's event timer priorities, see:
[http://code.google.com/p/qgtkstyle/issues/detail?id=85](http://code.google.com/p/qgtkstyle/issues/detail?id=85)

I have a simpler workaround now, as well. Edit src/ui_qt/application/application.cpp line 79 from:
```
timer->start(0);
```To:
```
timer->start(1);
```
And then recompile, and it will work :)

I hope it runs okay for you ^_^
Be sure to change the video driver under Settings->Configuration->Advanced to either OpenGL or X-Video, whichever one you have.

---

### Post by mister_playboy on 2009-07-21
It's runs great!  I had trouble with the pull-down menus flickering and not displaying, but turning of Compiz solved that... zsnes has similar problems for me.  I have brief audio-cutouts at 7 second intervals... something zsnes also does.  Probably PulseAudio's fault, but it works for everything else and I don't want to mess it up... :)

Putting in something with a lot of motion (NBA Jam TE), it is obvious that the playback is smoother here.  Pretty awesome!

Thanks for the help!  I'll try the recompile, too.

---

### Post by Nevon on 2009-07-21
> **tukuyomi said:**
> You have to install qt4-qmake, libqt4-dev, and build-essential

```
The following packages have unmet dependencies:
  libqt4-dev: Depends: libqt4-dbus (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqt4-qt3support (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqt4-xml (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqtcore4 (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqtgui4 (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqt4-network (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqt4-svg (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-webkit (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-sql (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqt4-script (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqt4-scripttools (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-xmlpatterns (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-designer (= 4.5.0-0ubuntu4.1) but 4.5.1-1~ppa1~jaunty1 is to be installed
              Depends: libqt4-help (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-assistant (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-test (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4.5.0-0ubuntu4.1) but it is not going to be installed
E: Broken packages
```

\\:D/

---

### Post by hikaricore on 2009-07-21
If you read the output there you have a bunch of ppa packages installed (or trying to install), these are conflicting with the dependencies.
This is the kinda thing you should be aware of when using third party sources.  :p  Try disabling them and do it again.

---

### Post by tukuyomi on 2009-07-22
> **mister_playboy said:**
> It's runs great!  I had trouble with the pull-down menus flickering and not displaying, but turning of Compiz solved that... zsnes has similar problems for me.  I have brief audio-cutouts at 7 second intervals... something zsnes also does.  Probably PulseAudio's fault, but it works for everything else and I don't want to mess it up... :)

Putting in something with a lot of motion (NBA Jam TE), it is obvious that the playback is smoother here.  Pretty awesome!

Thanks for the help!  I'll try the recompile, too.Flickering... you're probably using OpenGL driver; I suggest you to use the XVideo instead if it works for you :)

---

### Post by BoyOfDestiny on 2009-09-28
bsnes 0.052 is now out. It's worth mentioning it is now licensed under the GPL, so hopefully there will be a proper ubuntu package eventually. Along with a plethora of improvements with the past couple of releases, ips auto patching has been added, a boon to those stuck with plenty of ips files...

Grab bsnes and snesreader (for opening archived rom files with bsnes) here:
[http://byuu.org/bsnes/](http://byuu.org/bsnes/)

---

### Post by mister_playboy on 2009-09-29
I would like to say thanks for the user manual... maybe it's because I'm a nerd that I like to RTFM, but all too often, there simply isn't one!

I appreciate this sort of extra work very much.

---

### Post by byuu on 2009-09-29
v052 now defaults to OpenGL if you haven't used it before. If you don't have OpenGL, change the video driver under Settings->Configuration->Advanced. SDL was safer, but it was too slow and gave a bad first impression.

> It's worth mentioning it is now licensed under the GPL, so hopefully there will be a proper ubuntu package eventually.

Yeah, I really hope so. I'm not the best Linux coder so I could use some help getting it more stable on the less common window managers and such.

We will likely need to talk. I separated snesreader from bsnes for two reasons:
- decompression support source code was 3x bigger than my entire emulator core o.O
- unrar is not fully GPL (it can be disabled by a #define)

Also worth noting:
- libjma does not yet work on 64-bit systems
- zlib can be substituted for the system zlib easily; I include it for Windows users

Even though bsnes doesn't need it at all (it dynamically links to it only if present), it should be a dependency since otherwise you can't open ZIP, GZ, BZ2, JMA, 7Z or RAR archives; and IPS patching won't work without it.

> I would like to say thanks for the user manual

Thank you, I'm glad you liked it :D

I'm going to update it again this weekend with more info and updated pics. I added some pretty menu and panel icons to spruce it up like Snes9X-GTK.

Before: [http://byuu.org/bsnes/ui/input-controllers.png](http://byuu.org/bsnes/ui/input-controllers.png)
After: [http://byuu.org/images/bsnes_20090927.png](http://byuu.org/images/bsnes_20090927.png)

I'll also post an FAQ and compilation guide at that time. In the mean time, feel free to ask any questions here.

---

### Post by seanj on 2009-10-01
Managed to compile bsnes with the instructions in this thread, but when I load a ROM, it runs super slow and the sound stutters really badly.

---

### Post by tukuyomi on 2009-10-01
Can you tell what kind of computer you are using?

---

### Post by mister_playboy on 2009-10-01
> **seanj said:**
> Managed to compile bsnes with the instructions in this thread, but when I load a ROM, it runs super slow and the sound stutters really badly.

Sounds like you probably don't meet the minimum system requirements... they are quite high for bsnes.

---

### Post by hikaricore on 2009-10-01
> **mister_playboy said:**
> Sounds like you probably don't meet the minimum system requirements... they are quite high for bsnes.

I've had similar issues on a highend quad core system (with plenty of ram and a great video card) so I wouldn't assume that just yet.
Last time I tried bsnes I decided just to wait for the app to mature a little bit before testing again.

---

### Post by byuu on 2009-10-02
It's amusing that 80% of my development time is spent fixing Linux incompatibilities, and despite being 10% of my userbase, I get more bug reports from Linux users than from Windows and OS X users combined. At *some* point you have to think that maybe it's not the programmer, but the OS.

But I use Linux myself, so I'm determined to get it to work. Problem is I only have so many test systems. It runs great on all of mine.

If it doesn't work on yours, I would love some programming help. Or at least, please provide me with some information:
- processor
- video card
- Xlib driver name
- bsnes video, audio and input drivers selected

If no one helps to identify the problem areas, then I won't ever be able to fix them.

Be sure to try all the drivers. If you use the SDL video driver (default for v050 and prior), then obviously performance is going to suck. A 3x scale in SDL is more demanding than the core emulation itself.

---

### Post by hikaricore on 2009-10-02
I wasn't aware that it didn't use OpenGL by default.  O.o
There's a mystery and a half solved.

When I get a chance to test it out again I'll provide you with the requested info.

As for Linux there's nothing wrong with Linux, just perhaps your crossplatform usability needs a little work.
SDL is terrible on such a cpu intensive application as bsnes.  >.<

---

### Post by tukuyomi on 2009-10-04
Hello!
I've build a deb package from bsnes 0.052, you can find it here:
[http://kuro-hitsuji.net/~tukuyomi/stuff/bsnes/bsnes_052-1_i386.deb](http://kuro-hitsuji.net/~tukuyomi/stuff/bsnes/bsnes_052-1_i386.deb)
The recommended way to install is to use [apt://gdebi](apt://gdebi) (if installed, right-click on the .deb file).

---

### Post by byuu on 2009-10-05
>  When I get a chance to test it out again I'll provide you with the requested info.Cool, thanks a bunch; I hope it works better for you this time.

> As for Linux there's nothing wrong with Linux, just perhaps your crossplatform usability needs a little work.  SDL is terrible on such a cpu intensive application as bsnes.  >.<That's actually what I mean. If I use OpenGL, then libre video drivers like 'nv' won't work out of the box. If I use X-Video, then a few lousy drivers with no overlay support won't work. I was defaulting to SDL, but it gives such a bad impression that I'd rather the emulator give an error on first run if OpenGL is not present.

None of the APIs allow me to control Vsync from the application, so my "Sync Video" option is useless.

Audio is even worse: I provide ALSA, OSS, PulseAudio, OpenAL and libao; only one works great based on which one is the native API; and some platforms still can't produce sound: there's still libsndio (OpenBSD), Sun Audio (NetBSD, Open Solaris), etc.

---

### Post by mocha on 2009-10-07
Why can't you do vsync with OpenGL?  This shouldn't be a problem.

---

### Post by byuu on 2009-10-07
Because Vsync is controlled by the Xorg drivers. For nvidia, you have to run nvidia-settings and check "Sync to Vblank" under the OpenGL tab. You can't control the setting from OpenGL because the half-thought-out API did not consider or include Vsync control.

That may have even been acceptable if not for the fact that nvidia-settings forgets your settings every time you restart Xorg, and Vsync gets disabled again. If you restart nvidia-settings, you'll see the option is checked and "automagically" it Vsyncs again. So I guess the moral is to auto-start nvidia-settings on startup?

Windows has the proprietary wglSwapIntervalEXT(1) that works on one in three cards, and Apple has CGLSetParameter(context, kCGLCPSwapInterval, &(1)); that works everywhere. I know of no glX equivalent.

X-Video has XV_SYNC_TO_VBLANK atom on *some* Xv drivers, but most (::cough:: nvidia) again ignore the setting and use what's in its control panel instead. Xv is even worse, it simply doesn't Vsync at all when a compositor is enabled (even in mplayer, etc; not a bug in my driver.)

---

### Post by mocha on 2009-10-07
> **byuu said:**
> Because Vsync is controlled by the Xorg drivers. For nvidia, you have to run nvidia-settings and check "Sync to Vblank" under the OpenGL tab. You can't control the setting from OpenGL because the half-thought-out API did not consider or include Vsync control.

That may have even been acceptable if not for the fact that nvidia-settings forgets your settings every time you restart Xorg, and Vsync gets disabled again. If you restart nvidia-settings, you'll see the option is checked and "automagically" it Vsyncs again. So I guess the moral is to auto-start nvidia-settings on startup?

Windows has the proprietary wglSwapIntervalEXT(1) that works on one in three cards, and Apple has CGLSetParameter(context, kCGLCPSwapInterval, &(1)); that works everywhere. I know of no glX equivalent.

X-Video has XV_SYNC_TO_VBLANK atom on *some* Xv drivers, but most (::cough:: nvidia) again ignore the setting and use what's in its control panel instead. Xv is even worse, it simply doesn't Vsync at all when a compositor is enabled (even in mplayer, etc; not a bug in my driver.)

Just have your startup tasks execute "nvidia-settings -l" to load the settings from there.  Also, you can easily control it via the environment variables

```
__GL_SYNC_DISPLAY_DEVICE="DFP-1"
__GL_SYNC_TO_VBLANK="1"
```

---

### Post by BoyOfDestiny on 2009-11-05
Just a heads up that bsnes 0.055 is out, and has Super Gameboy support (a first!)

---

### Post by tukuyomi on 2009-11-06
DEBs are also available :)
[http://88.191.30.201/~tukuyomi/stuff/bsnes/bsnes_v055/](http://88.191.30.201/~tukuyomi/stuff/bsnes/bsnes_v055/)

---

### Post by grossaffe on 2009-11-06
I'm having trouble compiling.  We really need a list of dependencies to compile this.

```
moc -f ui_qt/base/loader.moc.hpp -o ui_qt/base/loader.moc
ui_qt/base/loader.moc.hpp:45: Error: syntax error
make: *** [ui_qt/base/loader.moc] Error 1

```

---

### Post by BoyOfDestiny on 2009-11-06
```
objdump -p /usr/local/bin/bsnes | grep NEEDED
  NEEDED               libopenal.so.1
  NEEDED               libSDL-1.2.so.0
  NEEDED               libGL.so.1
  NEEDED               libXv.so.1
  NEEDED               libasound.so.2
  NEEDED               libao.so.2
  NEEDED               libpulse-simple.so.0
  NEEDED               libQtGui.so.4
  NEEDED               libQtCore.so.4
  NEEDED               libstdc++.so.6
  NEEDED               libm.so.6
  NEEDED               libgcc_s.so.1
  NEEDED               libc.so.6
  NEEDED               libdl.so.2
  NEEDED               libpulse.so.0
  NEEDED               libX11.so.6
  NEEDED               libXext.so.6

```

All are in apt/synaptic, pretty much just add -dev as a suffix.
i.e. libpulse-dev

---

### Post by mister_playboy on 2009-11-06
> **tukuyomi said:**
> DEBs are also available :)
[http://88.191.30.201/~tukuyomi/stuff/bsnes/bsnes_v055/](http://88.191.30.201/~tukuyomi/stuff/bsnes/bsnes_v055/)

32-bit, anyway... ;)

---

### Post by stillious on 2009-11-11
> **mister_playboy said:**
> 32-bit, anyway... ;)

I compiled this for amd64. I don't guarantee it will work, but hey :) (works fine for me).

---

### Post by byuu on 2009-11-18
v056 will be out probably this weekend. It adds:
- multi-destination key mapping (eg Joypad 1 Start = Shift+KB0::Return)
- turbo buttons and turbo switches (eg asciiPad support)
- multi-source key mapping (eg Joypad 1 Start = Shift+KB0::Return;JP0::Button7) [pseudo-supported for two sources]
- fast BS-X / Sufami Turbo / Super Game Boy cart loading [bypasses BIOS selection screen]
- scanlines for every filter, including NTSC
- a ton of Super Game Boy bug fixes and improvements
- OpenGL pixel shader support (hopefully)

> moc -f ui_qt/base/loader.moc.hpp -o ui_qt/base/loader.moc
ui_qt/base/loader.moc.hpp:45: Error: syntax errorYour system has Qt3 development tools on it. Edit src/lib/nall/Makefile-qt and change moc := moc and rcc := rcc to moc := moc-qt4 and rcc := rcc-qt4

> [http://ubuntuforums.org/attachment.php?attachmentid=134929&d=1257470598](http://ubuntuforums.org/attachment.php?attachmentid=134929&d=1257470598)Where are the menu and status bars at? o.O
The areas are black, but there's room for them. Maybe it's the no-auto-shrink in v055 in play and you turned them off.

---

### Post by BoyOfDestiny on 2009-11-19
> **byuu said:**
> ...
Where are the menu and status bars at? o.O
The areas are black, but there's room for them. Maybe it's the no-auto-shrink in v055 in play and you turned them off.

I pressed Esc, I normally don't use the menus much after initial setup, (which is why I have no problem when I use commandline driven emulators...) 

So that "no-auto-shrink" is a bug then? 
Are there plans to fix that, even though it's something quite minor? 

It would have to re-size the window but maintain the position of the emulated screen. Otherwise it might be kind of jarring (i.e. make the picture jump around when escape is pressed then pressed again.)

Thanks.

---

### Post by byuu on 2009-11-19
> So that "no-auto-shrink" is a bug then? 
Are there plans to fix that, even though it's something quite minor? 

It would have to re-size the window but maintain the position of the emulated screen. Otherwise it might be kind of jarring (i.e. make the picture jump around when escape is pressed then pressed again.)

That's the reason I had it like that in v055, so that your video output and window sizing / position wouldn't change on you from simply executing common UI commands. Frankly, I liked it like that.

I get way, way more complaints because it *doesn't* auto-shrink, so I gave in and made it shrink again in v056.

I'd make it an option, but those have costs too. I don't want a program with more options than Firefox's about:config, simply because people can't agree on *anything* :(

---

### Post by BlackAura on 2009-11-20
> **byuu said:**
> Windows has the proprietary wglSwapIntervalEXT(1) that works on one in three cards, and Apple has CGLSetParameter(context, kCGLCPSwapInterval, &(1)); that works everywhere. I know of no glX equivalent.

Not sure if this'll be useful, given that it's a month late, but you certainly can control this with glX.

The GLX_SGI_swap_control glX extension has the glXSwapIntervalSGI function, which works exactly the same way as wglSwapIntervalEXT. Last time I checked, it was available in all drivers, but wasn't functional in MESA drivers (it exports the function, but it doesn't do anything).

MESA has glXSwapIntervalMESA which, works exactly the same way as wglSwapIntervalEXT ' glXSwapIntervalSGI, but only with MESA drivers. If you try the MESA one first, then the SGI only if the MESA one doesn't exist, that should do it.

There's also the GLX_EXT_swap_control extension, which provides the glXSwapIntervalEXT function, but I don't know how widely supported that extension is.

---

### Post by byuu on 2009-11-23
Thanks a bunch, Mocha and BlackAura. I've added support for glXSwapIntervalEXT+SGI+MESA (and pixel shader support) in v057. Works like a charm :)

For once it's only the Windows prot with the problem, wglSwapIntervalEXT does nothing there. Even OS X's CGL version works great.

---

### Post by mocha on 2009-11-28
> **byuu said:**
> Thanks a bunch, Mocha and BlackAura. I've added support for glXSwapIntervalEXT+SGI+MESA (and pixel shader support) in v057. Works like a charm :)

For once it's only the Windows prot with the problem, wglSwapIntervalEXT does nothing there. Even OS X's CGL version works great.


Looks great!  No tearing!  Tearing really bothers me for some reason.

---

### Post by NovaWasp on 2009-11-30
What's the best way to un-install BSNES once installed so I can install the latest version?  I'm still on .50.  

Thanks,

---

### Post by byuu on 2009-12-02
You can just sudo make install the new one on top of the old one. If you want the actual files, it writes to:

/usr/local/bin/bsnes
/usr/local/share/pixmaps/bsnes.png
/usr/local/share/applications/bsnes.desktop
~/.bsnes/bsnes.cfg

As of v052 or so there are separate libraries for filters, compression and Super Game Boy. They all go to /usr/local/lib and are named appropriately. Should be the only files in that folder most likely.

---

### Post by quequotion on 2010-01-08
Hello!

I'm getting stuck with the compile at ```
In file included from lib/ruby/ruby_impl.cpp:128,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/pulseaudio.cpp: In member function &#8216;void ruby::pAudioPulseAudio::sample(uint16_t, uint16_t)&#8217;:
lib/ruby/audio/pulseaudio.cpp:68: error: &#8216;pa_stream_begin_write&#8217; was not declared in this scope
lib/ruby/audio/pulseaudio.cpp: In member function &#8216;bool ruby::pAudioPulseAudio::init()&#8217;:
lib/ruby/audio/pulseaudio.cpp:99: error: &#8216;PA_CONTEXT_NOFLAGS&#8217; was not declared in this scope
lib/ruby/audio/pulseaudio.cpp: In member function &#8216;void ruby::pAudioPulseAudio::term()&#8217;:
lib/ruby/audio/pulseaudio.cpp:138: error: &#8216;pa_stream_cancel_write&#8217; was not declared in this scope
make: *** [obj/ruby.o] Error 1
``` but I've checked very carefully to make sure I have all of the libraries mentioned in this thread and I most certainly do. Could it be that bsnes won't compile with g++ 4.3? or is there one more library involved?

also, this is bsnes 059.

---

### Post by tukuyomi on 2010-01-08
Did you miss pulse developement files?
```
sudo apt-get install libpulse-dev
```

---

### Post by quequotion on 2010-01-08
> **tukuyomi said:**
> Did you miss pulse developement files?
```
sudo apt-get install libpulse-dev
```

I have that one too...

Does it help to know I'm compiling in Jaunty?

---

### Post by RPG Master on 2010-01-11
I am trying to compile this and I get these errors:

```
g++ -O3 -fomit-frame-pointer -Ilib -DVIDEO_GLX -DVIDEO_XV -DVIDEO_QTRASTER -DVIDEO_SDL -DAUDIO_ALSA -DAUDIO_OPENAL -DAUDIO_OSS -DAUDIO_PULSEAUDIO -DAUDIO_PULSEAUDIOSIMPLE -DAUDIO_AO -DINPUT_SDL -DINPUT_X `sdl-config --cflags` `pkg-config --cflags QtCore QtGui` -c lib/ruby/ruby.cpp -o obj/ruby.o
In file included from lib/ruby/ruby_impl.cpp:75,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/video/sdl.cpp:3:31: error: X11/extensions/Xv.h: No such file or directory
lib/ruby/video/sdl.cpp:4:34: error: X11/extensions/Xvlib.h: No such file or directory
In file included from lib/ruby/ruby_impl.cpp:112,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/ao.cpp:6:19: error: ao/ao.h: No such file or directory
In file included from lib/ruby/ruby_impl.cpp:120,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/openal.cpp:11:21: error: AL/al.h: No such file or directory
lib/ruby/audio/openal.cpp:12:22: error: AL/alc.h: No such file or directory
In file included from lib/ruby/ruby_impl.cpp:83,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/video/xv.cpp:7: error: expected constructor, destructor, or type conversion before ‘*’ token
lib/ruby/video/xv.cpp:37: error: ISO C++ forbids declaration of ‘XvImage’ with no type
lib/ruby/video/xv.cpp:37: error: expected ‘;’ before ‘*’ token
lib/ruby/video/xv.cpp: In member function ‘bool ruby::pVideoXv::set(const nall::string&, const nall::any&)’:
lib/ruby/video/xv.cpp:78: error: ‘XvSetPortAttribute’ was not declared in this scope
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::resize(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:95: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:98: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
In file included from lib/ruby/ruby_impl.cpp:83,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/video/xv.cpp:98: error: ‘XvShmCreateImage’ was not declared in this scope
lib/ruby/video/xv.cpp:100: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:101: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::refresh()’:
lib/ruby/video/xv.cpp:156: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:159: error: ‘XvShmPutImage’ was not declared in this scope
lib/ruby/video/xv.cpp: In member function ‘bool ruby::pVideoXv::init()’:
lib/ruby/video/xv.cpp:172: error: ‘XvAdaptorInfo’ was not declared in this scope
lib/ruby/video/xv.cpp:172: error: ‘adaptor_info’ was not declared in this scope
lib/ruby/video/xv.cpp:174: error: ‘XvQueryAdaptors’ was not declared in this scope
lib/ruby/video/xv.cpp:178: error: ‘XvInputMask’ was not declared in this scope
lib/ruby/video/xv.cpp:179: error: ‘XvImageMask’ was not declared in this scope
lib/ruby/video/xv.cpp:186: error: ‘XvFreeAdaptorInfo’ was not declared in this scope
lib/ruby/video/xv.cpp:228: error: ‘XvSetPortAttribute’ was not declared in this scope
lib/ruby/video/xv.cpp:233: error: ‘XvImageFormatValues’ was not declared in this scope
lib/ruby/video/xv.cpp:233: error: ‘format’ was not declared in this scope
lib/ruby/video/xv.cpp:233: error: ‘XvListImageFormats’ was not declared in this scope
lib/ruby/video/xv.cpp:236: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:244: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:252: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:260: error: ‘XvRGB’ was not declared in this scope
lib/ruby/video/xv.cpp:268: error: ‘XvYUV’ was not declared in this scope
lib/ruby/video/xv.cpp:268: error: ‘XvPacked’ was not declared in this scope
lib/ruby/video/xv.cpp:280: error: ‘XvYUV’ was not declared in this scope
lib/ruby/video/xv.cpp:280: error: ‘XvPacked’ was not declared in this scope
lib/ruby/video/xv.cpp:300: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:300: error: ‘XvShmCreateImage’ was not declared in this scope
lib/ruby/video/xv.cpp:301: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:306: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp:307: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::term()’:
lib/ruby/video/xv.cpp:326: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb32(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:346: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb24(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:357: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb16(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:374: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_rgb15(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:389: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_yuy2(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:404: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
lib/ruby/video/xv.cpp: In member function ‘void ruby::pVideoXv::render_uyvy(unsigned int, unsigned int)’:
lib/ruby/video/xv.cpp:427: error: ‘struct ruby::pVideoXv::<anonymous>’ has no member named ‘image’
In file included from lib/ruby/ruby_impl.cpp:112,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/ao.cpp: At global scope:
lib/ruby/audio/ao.cpp:13: error: ‘ao_sample_format’ does not name a type
lib/ruby/audio/ao.cpp:14: error: ISO C++ forbids declaration of ‘ao_device’ with no type
lib/ruby/audio/ao.cpp:14: error: expected ‘;’ before ‘*’ token
lib/ruby/audio/ao.cpp: In member function ‘bool ruby::pAudioAO::set(const nall::string&, const nall::any&)’:
lib/ruby/audio/ao.cpp:33: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp: In member function ‘void ruby::pAudioAO::sample(uint16_t, uint16_t)’:
lib/ruby/audio/ao.cpp:42: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:42: error: ‘ao_play’ was not declared in this scope
lib/ruby/audio/ao.cpp: In member function ‘bool ruby::pAudioAO::init()’:
lib/ruby/audio/ao.cpp:51: error: ‘ao_default_driver_id’ was not declared in this scope
lib/ruby/audio/ao.cpp:54: error: ‘driver_format’ was not declared in this scope
lib/ruby/audio/ao.cpp:57: error: ‘AO_FMT_LITTLE’ was not declared in this scope
lib/ruby/audio/ao.cpp:59: error: ‘ao_option’ was not declared in this scope
lib/ruby/audio/ao.cpp:59: error: ‘options’ was not declared in this scope
lib/ruby/audio/ao.cpp:60: error: ‘ao_info’ was not declared in this scope
lib/ruby/audio/ao.cpp:60: error: ‘di’ was not declared in this scope
lib/ruby/audio/ao.cpp:60: error: ‘ao_driver_info’ was not declared in this scope
lib/ruby/audio/ao.cpp:63: error: ‘ao_append_option’ was not declared in this scope
lib/ruby/audio/ao.cpp:66: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:66: error: ‘ao_open_live’ was not declared in this scope
lib/ruby/audio/ao.cpp: In member function ‘void ruby::pAudioAO::term()’:
lib/ruby/audio/ao.cpp:73: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:74: error: ‘ao_close’ was not declared in this scope
lib/ruby/audio/ao.cpp: In constructor ‘ruby::pAudioAO::pAudioAO()’:
lib/ruby/audio/ao.cpp:80: error: ‘audio_device’ was not declared in this scope
lib/ruby/audio/ao.cpp:81: error: ‘ao_initialize’ was not declared in this scope
In file included from lib/ruby/ruby_impl.cpp:120,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/openal.cpp: At global scope:
lib/ruby/audio/openal.cpp:20: error: ISO C++ forbids declaration of ‘ALCdevice’ with no type
lib/ruby/audio/openal.cpp:20: error: expected ‘;’ before ‘*’ token
lib/ruby/audio/openal.cpp:21: error: ISO C++ forbids declaration of ‘ALCcontext’ with no type
lib/ruby/audio/openal.cpp:21: error: expected ‘;’ before ‘*’ token
lib/ruby/audio/openal.cpp:22: error: ‘ALuint’ does not name a type
lib/ruby/audio/openal.cpp:23: error: ‘ALenum’ does not name a type
lib/ruby/audio/openal.cpp: In member function ‘void ruby::pAudioOpenAL::sample(uint16_t, uint16_t)’:
lib/ruby/audio/openal.cpp:80: error: ‘ALuint’ was not declared in this scope
lib/ruby/audio/openal.cpp:80: error: expected ‘;’ before ‘albuffer’
lib/ruby/audio/openal.cpp:83: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:83: error: ‘AL_BUFFERS_PROCESSED’ was not declared in this scope
lib/ruby/audio/openal.cpp:83: error: ‘alGetSourcei’ was not declared in this scope
lib/ruby/audio/openal.cpp:85: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:85: error: ‘albuffer’ was not declared in this scope
lib/ruby/audio/openal.cpp:85: error: ‘alSourceUnqueueBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:86: error: ‘alDeleteBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:94: error: ‘albuffer’ was not declared in this scope
lib/ruby/audio/openal.cpp:94: error: ‘alGenBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:95: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘format’
lib/ruby/audio/openal.cpp:95: error: ‘alBufferData’ was not declared in this scope
lib/ruby/audio/openal.cpp:96: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:96: error: ‘alSourceQueueBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:100: error: ‘ALint’ was not declared in this scope
lib/ruby/audio/openal.cpp:100: error: expected ‘;’ before ‘playing’
lib/ruby/audio/openal.cpp:101: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:101: error: ‘AL_SOURCE_STATE’ was not declared in this scope
lib/ruby/audio/openal.cpp:101: error: ‘playing’ was not declared in this scope
lib/ruby/audio/openal.cpp:101: error: ‘alGetSourcei’ was not declared in this scope
lib/ruby/audio/openal.cpp:102: error: ‘AL_PLAYING’ was not declared in this scope
lib/ruby/audio/openal.cpp:102: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:102: error: ‘alSourcePlay’ was not declared in this scope
lib/ruby/audio/openal.cpp: In member function ‘bool ruby::pAudioOpenAL::init()’:
lib/ruby/audio/openal.cpp:120: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:120: error: ‘alcOpenDevice’ was not declared in this scope
lib/ruby/audio/openal.cpp:121: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:121: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:121: error: ‘alcCreateContext’ was not declared in this scope
lib/ruby/audio/openal.cpp:122: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:122: error: ‘alcMakeContextCurrent’ was not declared in this scope
lib/ruby/audio/openal.cpp:123: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:123: error: ‘alGenSources’ was not declared in this scope
lib/ruby/audio/openal.cpp:133: error: ‘AL_POSITION’ was not declared in this scope
lib/ruby/audio/openal.cpp:133: error: ‘alListener3f’ was not declared in this scope
lib/ruby/audio/openal.cpp:134: error: ‘AL_VELOCITY’ was not declared in this scope
lib/ruby/audio/openal.cpp:135: error: ‘ALfloat’ was not declared in this scope
lib/ruby/audio/openal.cpp:135: error: expected ‘;’ before ‘listener_orientation’
lib/ruby/audio/openal.cpp:136: error: ‘AL_ORIENTATION’ was not declared in this scope
lib/ruby/audio/openal.cpp:136: error: ‘listener_orientation’ was not declared in this scope
lib/ruby/audio/openal.cpp:136: error: ‘alListenerfv’ was not declared in this scope
lib/ruby/audio/openal.cpp: In member function ‘void ruby::pAudioOpenAL::term()’:
lib/ruby/audio/openal.cpp:151: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:151: error: ‘alIsSource’ was not declared in this scope
lib/ruby/audio/openal.cpp:151: error: ‘AL_TRUE’ was not declared in this scope
lib/ruby/audio/openal.cpp:153: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:153: error: ‘AL_SOURCE_STATE’ was not declared in this scope
lib/ruby/audio/openal.cpp:153: error: ‘alGetSourcei’ was not declared in this scope
lib/ruby/audio/openal.cpp:154: error: ‘AL_PLAYING’ was not declared in this scope
lib/ruby/audio/openal.cpp:155: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:155: error: ‘alSourceStop’ was not declared in this scope
lib/ruby/audio/openal.cpp:157: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:157: error: ‘AL_BUFFERS_QUEUED’ was not declared in this scope
lib/ruby/audio/openal.cpp:159: error: ‘ALuint’ was not declared in this scope
lib/ruby/audio/openal.cpp:159: error: expected ‘;’ before ‘albuffer’
lib/ruby/audio/openal.cpp:160: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:160: error: ‘albuffer’ was not declared in this scope
lib/ruby/audio/openal.cpp:160: error: ‘alSourceUnqueueBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:161: error: ‘alDeleteBuffers’ was not declared in this scope
lib/ruby/audio/openal.cpp:166: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:166: error: ‘alDeleteSources’ was not declared in this scope
lib/ruby/audio/openal.cpp:167: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:170: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:171: error: ‘alcMakeContextCurrent’ was not declared in this scope
lib/ruby/audio/openal.cpp:172: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:172: error: ‘alcDestroyContext’ was not declared in this scope
lib/ruby/audio/openal.cpp:173: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:176: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:177: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:177: error: ‘alcCloseDevice’ was not declared in this scope
lib/ruby/audio/openal.cpp:178: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp: In constructor ‘ruby::pAudioOpenAL::pAudioOpenAL()’:
lib/ruby/audio/openal.cpp:188: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘source’
lib/ruby/audio/openal.cpp:189: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘handle’
lib/ruby/audio/openal.cpp:190: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘context’
lib/ruby/audio/openal.cpp:191: error: ‘struct ruby::pAudioOpenAL::<anonymous>’ has no member named ‘format’
lib/ruby/audio/openal.cpp:191: error: ‘AL_FORMAT_STEREO16’ was not declared in this scope
make: *** [obj/ruby.o] Error 1

```

9.10 64-bit

help me :(

---

### Post by tukuyomi on 2010-01-12
[http://ubuntuforums.org/showpost.php?p=7655544&postcount=12](http://ubuntuforums.org/showpost.php?p=7655544&postcount=12)

---

### Post by quequotion on 2010-01-20
> **tukuyomi said:**
> [http://ubuntuforums.org/showpost.php?p=7655544&postcount=12](http://ubuntuforums.org/showpost.php?p=7655544&postcount=12)

I have all of those, except libasound-dev (no installation candidate, outdated) which has become libasound2-dev and I have that.

Is there anything ***else***?

---

### Post by mister_playboy on 2010-02-03
> **quequotion said:**
> Hello!

I'm getting stuck with the compile at ```
In file included from lib/ruby/ruby_impl.cpp:128,
                 from lib/ruby/ruby.cpp:4:
lib/ruby/audio/pulseaudio.cpp: In member function ‘void ruby::pAudioPulseAudio::sample(uint16_t, uint16_t)’:
lib/ruby/audio/pulseaudio.cpp:68: error: ‘pa_stream_begin_write’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp: In member function ‘bool ruby::pAudioPulseAudio::init()’:
lib/ruby/audio/pulseaudio.cpp:99: error: ‘PA_CONTEXT_NOFLAGS’ was not declared in this scope
lib/ruby/audio/pulseaudio.cpp: In member function ‘void ruby::pAudioPulseAudio::term()’:
lib/ruby/audio/pulseaudio.cpp:138: error: ‘pa_stream_cancel_write’ was not declared in this scope
make: *** [obj/ruby.o] Error 1
``` but I've checked very carefully to make sure I have all of the libraries mentioned in this thread and I most certainly do. Could it be that bsnes won't compile with g++ 4.3? or is there one more library involved?

also, this is bsnes 059.

I have this same problem compiling on 9.04.

---

### Post by quequotion on 2010-02-11
> **mister_playboy said:**
> I have this same problem compiling on 9.04.

any idea what could be wrong? is there another dependency that no one bothered to write down? could it be the dependencies require a specific version of the package?

---

### Post by byuu on 2010-02-11
sudo apt-get install build-essential libqt4-dev libsdl1.2-dev
sudo apt-get install libpulse-dev libopenal-dev libao-dev libxv-dev
make
sudo make install

The errors show missing OpenAL / Pulseaudio / X-video stuff, so if you've installed the libs and it's not working, then the libs must not have installed properly :/

---

### Post by ifraser on 2010-02-14
> **Nevon said:**
> Maybe I'm dumb, but how exactly do I install this? Running *make* only gives me:
```
nevon@loltop:~/Desktop/src$ make
rcc ui_qt/resource/resource.qrc -o ui_qt/resource/resource.rcc
make: rcc: Command not found
make: *** [ui_qt/resource/resource.rcc] Error 127
```

Same here.

---

### Post by ifraser on 2010-02-14
Update: I think one of the issues is that people typing manually into the Terminal from  [byuu's compiling instructions]("http://byuu.org/bsnes/compilation-guide") are typing libsdl1.2-dev as "libsdll.2-dev" (~DLL.2 instead of ~DL1.2) because the font doesn't clearly differentiate the two....

---

### Post by quequotion on 2010-02-26
> **ifraser said:**
> Update: I think one of the issues is that people typing manually into the Terminal from  [byuu's compiling instructions]("http://byuu.org/bsnes/compilation-guide") are typing libsdl1.2-dev as "libsdll.2-dev" (~DLL.2 instead of ~DL1.2) because the font doesn't clearly differentiate the two....

ah-HA!!

I'll have to check which one I have when I get home.

---

