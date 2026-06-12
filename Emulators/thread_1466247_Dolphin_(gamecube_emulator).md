---
title: "Dolphin (gamecube emulator)"
date: 2010-04-30
forum: Emulators
---

### Post by HHx66 on 2010-04-30
How would I install it? Sorry I can only find sources and I'm a bit of a newb when it comes to compiling from source.

---

### Post by snova on 2010-04-30
Their main [download page]("http://www.dolphin-emu.com/downloads.php?cat_id=9") doesn't even offer source.

The .tar.bz2 files are binary builds; in theory you can simply extract it somewhere and run the dolphin-emu program in Binary/Linux-i686 (or Linux-x86_64 if you're so inclined).

---

### Post by del_diablo on 2010-05-01
Or you could compile, which in this case is a minor ordeal due a large mess of depenadcies.

---

### Post by snova on 2010-05-01
> **del_diablo said:**
> Or you could compile, which in this case is a minor ordeal due a large mess of depenadcies.

The main binary is dynamically linked to the following:

```

        linux-gate.so.1 =>  (0x003e6000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x00b08000)
        libbluetooth.so.3 => /usr/lib/libbluetooth.so.3 (0x00130000)
        libao.so.2 => /usr/lib/libao.so.2 (0x00bae000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00f12000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x001ea000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0x00df9000)
        libportaudio.so.2 => not found
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00808000)
        libwx_gtk2u_aui-2.8.so.0 => not found
        libwx_gtk2u_adv-2.8.so.0 => not found
        libwx_gtk2u_core-2.8.so.0 => not found
        libwx_baseu-2.8.so.0 => not found
        libz.so.1 => /lib/libz.so.1 (0x00110000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x001ee000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x0094b000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00733000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x003e7000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00125000)
        libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x00145000)
        libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00f53000)
        libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00eee000)
        /lib/ld-linux.so.2 (0x00348000)
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0x001bc000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x0078b000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x001d6000)

```

This is, I think, the following packages:

[LIST]
[*]libsdl1.2
[*]libbluetooth3
[*]libao2
[*]libasound2
[*]libportaudio2
[*]libwxgtk2.8-0
[*]libdirectfb-1.2-0
[/LIST]

And the rest will probably already be installed. I'm not sure how one arrives at the conclusion that building from svn would be easier.

---

### Post by HHx66 on 2010-05-01
I can never get the pre-compiled executable to even launch on my system, and its set as executable, so I have no idea.

---

### Post by hikaricore on 2010-05-01
Terminal output or it didn't happen.

---

### Post by robertc36 on 2010-05-01
get it from here [http://www.playdeb.net/updates/Ubuntu/all](http://www.playdeb.net/updates/Ubuntu/all)

---

### Post by HHx66 on 2010-05-02
I don't even get terminal output for it. Just will not run.

---

### Post by del_diablo on 2010-05-02
So do you use "sh ./file" or "./file"? ::P

snova: Its a few steps easier on Ubuntu..... but there is no good metapackage on build tools. On fedora or anything that does not get it in auto its a bit harder to compile since the depenacies is badly listed.

---

### Post by hikaricore on 2010-05-02
> **HHx66 said:**
> I don't even get terminal output for it. Just will not run.

Then you're not running it from a terminal.
Or you're not executing it properly as mentioned above.

---

### Post by Raiju on 2010-05-02
Anyone else trying to run the 2.0 release?

```
$ ./dolphin-emu 
./dolphin-emu: relocation error: ./dolphin-emu: symbol _ZN12wxAuiToolBar12ms_classInfoE, version WXU_2.8 not defined in file libwx_gtk2u_aui-2.8.so.0 with link time reference

```

---

### Post by otoris on 2010-05-02
**Edit:**
Just noticed that [http://www.playdeb.net/updates/ubuntu/all/](http://www.playdeb.net/updates/ubuntu/all/) version of dolphin is already 10.04 compatible, and works. :D

[http://code.google.com/p/dolphin-emu/wiki/DolphinUbuntuPackages](http://code.google.com/p/dolphin-emu/wiki/DolphinUbuntuPackages)

This source has been kept up with and gets weekly (almost) builds from the svn. They haven't set up dolphin emu for 10.04 yet. Hopefully 10.04 support will arrive soon. Until then, best thing to do would be to use the svn builds from googlecode.

---

### Post by brantpadams on 2010-05-03
I've tried downloading from the above link and from the terminal, but I still get the same prompt "cannot find dolphin-emu." Am I missing a step?

---

### Post by del_diablo on 2010-05-04
What about ./ as in "file located in folder"?

---

### Post by brantpadams on 2010-05-04
So I'm gathering that I have to build this thing before downloading it? If there's some step by step guide out there I'd love to see it. I haven't been very well educated in it.

---

### Post by MC_Sketch on 2010-05-24
it's actually a lot simpler than that. simply type these commands into Terminal and it's yours. :)

> $ sudo add-apt-repository ppa:glennric/dolphin-emu
$ sudo apt-get update
$ sudo apt-get install dolphin-emu

---

### Post by brantpadams on 2010-05-26
Thanks. That definitely did it. My only concern now (which I'm pretty sure I already resolved) is can it work on a X3100 Media Accelerator card? It's 32-bit so I'm pretty sure the answer is no.

---

### Post by retry32 on 2010-06-03
thanx

---

### Post by del_diablo on 2010-06-03
> **brantpadams said:**
> Thanks. That definitely did it. My only concern now (which I'm pretty sure I already resolved) is can it work on a X3100 Media Accelerator card? It's 32-bit so I'm pretty sure the answer is no.

X3100? Is that ATI RADEON? If yes, then yes. Wii is more CPU bound, which is fixed by having a dualcore.
If no, how old?

---

### Post by brantpadams on 2011-09-08
> **del_diablo said:**
> X3100? Is that ATI RADEON? If yes, then yes. Wii is more CPU bound, which is fixed by having a dualcore.
If no, how old?
Wow. Sorry for the extremely delayed response. I just reinstalled dolphin on 11.04 after not having much luck with it in the past. Was wondering if anyone had some pointers. 

I can run the iso's easy enough, but the only way they'll run is if I create a path for them through configuration. Is this standard? Because my understanding was that it could detect iso's and you could select from them on the screen. It still works, it's just not how I pictured it working. 

Also, the framerate on my particular machine is lagging like crazy. It may depend on the game, but Super Smash Bros. Melee runs extremely slow. The menus are fine, but the game itself lags. I haven't figured out if there's any way to work around it, but if there is I'd love to know. 

Again, extremely delayed response. I was browsing through the threads and I completely forgot I had subscribed to this one.

---

