---
title: "random xorg crashes with composing managers"
date: 2007-02-06
forum: Desktop Environments
---

### Post by aph216 on 2007-02-06
Hi.
I'm using amd64 version of Kubuntu 6.10. When i use composing (with beryl, compiz or even xcompmgr) i experience random crashes. It usually happens when there are lot of applications (opera, amarok, mplayer...), about one crash per hour. using diffrent versions of managers doesn't make any diffrence. i tried to change my nvidia drivers (i'm using gf4mx) from 9631 to 9629 but it's still the same.

the last entry before crash in /var/log/Xorg.0.log is:
```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x71) [0x480b81]
1: /lib/libc.so.6 [0x2ae862da3510]
2: /usr/bin/X [0x50f40c]
3: /usr/bin/X [0x50f773]
4: /usr/bin/X [0x50b8cc]
5: /usr/bin/X [0x5014eb]
6: /usr/bin/X(Dispatch+0x1ba) [0x4483aa]
7: /usr/bin/X(main+0x455) [0x431035]
8: /lib/libc.so.6(__libc_start_main+0xf4) [0x2ae862d900c4]
9: /usr/bin/X(FontFileCompleteXLFD+0xa1) [0x430339]

Fatal server error:
Caught signal 11.  Server aborting
```

beryl-manager gives just:
```
The application 'beryl-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
```

interesting parts of xorg.conf:
```

(...)
Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
(...)
Section "Monitor"
    Identifier     "NEC V730"
    Option         "DPMS"
    Modeline    "1024x768" 95.65  1024 1072 1192 1408   768  768  771  808
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Driver          "nvidia"
    BusID          "PCI:1:0:0"
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Monitor        "NEC V730"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by julakali on 2007-02-09
Same here on a gentoo system.

I experience random crashes (not as frequently as you, but once a day maybe), especially when running some more tasks, when a compositing manager is running.
With composite disabled in xorg.conf, everything is running fine.

I'm using nvidia-drivers-1.0.9746 on a Geforce 6600GT AGP and Xorg 7.1.

I didn't keep a logfile from the crash, but I remember the 
"Fatal server error:
Caught signal 11.  Server aborting"

kdm just restarted after the crash. No useful log information.


----

here's my last log info:

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x85) [0x80cde75]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by PhinnFort on 2007-02-26
Exactly the same error (backtrace, etc.)
Lots of apps open, some running in the background, and random crashes.
Konqueror is always loading a webpage when it happens, btw.

The only difference is that I use the open source radeon driver.

-PhinnFort

---

### Post by PhinnFort on 2007-02-28
I'm no good with german, but apparently someone is having the same problem here:
[http://translate.google.com/translate?hl=en&sl=de&u=http://forum.beryl-project.org/viewtopic.php%3Ff%3D47%26t%3D2258&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3D/usr/bin/X(FontFileCompleteXLFD%252B0xa1)%2B%255B0x430339%255D%26hl%3Den%26ie%3DUTF-8%26oe%3DUTF-8%26sa%3DG](http://translate.google.com/translate?hl=en&sl=de&u=http://forum.beryl-project.org/viewtopic.php%3Ff%3D47%26t%3D2258&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3D/usr/bin/X(FontFileCompleteXLFD%252B0xa1)%2B%255B0x430339%255D%26hl%3Den%26ie%3DUTF-8%26oe%3DUTF-8%26sa%3DG)

-PhinnFort

---

### Post by julakali on 2007-03-07
I think his problem differs.
He can't even start beryl-manager, while I can.
X just happens to crash randomly with a compositing window manager enabled.

I'll try the --force-nvidia option...

---

### Post by Magnes on 2007-03-07
[https://launchpad.net/ubuntu/+source/xorg-server/+bug/60288](https://launchpad.net/ubuntu/+source/xorg-server/+bug/60288)
- maybe you have this problem?

Try the patch which is here: [http://tormod.freeshell.org/linux/xorg-server/](http://tormod.freeshell.org/linux/xorg-server/)
it works great for me. Install this file: [http://tormod.freeshell.org/linux/xorg-server/xserver-xorg-core_1.1.1-0ubuntu12.1tormod_i386.deb](http://tormod.freeshell.org/linux/xorg-server/xserver-xorg-core_1.1.1-0ubuntu12.1tormod_i386.deb). I had to reinstall my NVIDIA drivers afterwards.

---

### Post by julakali on 2007-03-08
Not the same problem.
I have another Backtrace info and it doesn't happen when doing nothing.
Instead, it happens when doing much (more or less).

---

### Post by PhinnFort on 2007-03-08
> **julakali said:**
> Not the same problem.
I have another Backtrace info and it doesn't happen when doing nothing.
Instead, it happens when doing much (more or less).
Second that. What's changed from my last post, though, is that I switched to Feisty, and the problem still persists.

-PhinnFort

---

### Post by freebird54 on 2007-03-08
I am posting from an old Laptop (shipped with dual Win96/Win98! ) so I can't show you my xorg.conf - but where is the 
load dri
line gone?

I get about 2 days between crashes currently - and usually can just 'reload window manager' to recover from the drop-back to Metacity...

I suspect the more video card and RAM you have, the better it runs with Beryl...

---

### Post by julakali on 2007-03-23
It's not only beryl or emerald crashing, it's the whole X thing.
the screen goes back to console login and kdm immediatly restarts the graphical login, so everything you did in X is gone.

I experienced those crashes often when working with yakuake...
I'll try to live without it a while to see if yakuake is the cause...

---

### Post by PhinnFort on 2007-03-23
I also used Yakuake when Xorg crashed, in fact I think I was "pulling it down" when Xorg crashed.
Maybe the fast, incremental changes in the window size is making it crash? I'll try turning off animation. I'll never be able to live without yakuake, though.

-PhinnFort

---

### Post by mfarley on 2007-11-21
I'm experiencing these exact symptoms.. Latest gutsy everything..

Anyone ever find a fix?

---

### Post by mfarley on 2007-11-23
Anyone??  This is driving me nuts..

(shameless bump)

---

### Post by lexxonnet on 2007-12-05
Hmm... I've been having this problem on both an upgrade from feisty and a fresh install of gutsy. Usually happens when yakuake is rolled up (I disabled animation) with any sort of composite manager running (both kwin-composite(kde3) and compiz-fusion). 

Here is the backtrace
```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/bin/X [0x817e39d]
3: /usr/bin/X [0x817a9ef]
4: /usr/bin/X(CompositeGlyphs+0x9a) [0x816129a]
5: /usr/bin/X [0x8168f19]
6: /usr/bin/X [0x8164315]
7: /usr/bin/X [0x815754e]
8: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
9: /usr/bin/X(main+0x495) [0x8076f05]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d4a050]
11: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting

```
It seems even more frequent when yakuake has multiple tabs open, and especially if its running apt in one of them.

---

### Post by mfarley on 2007-12-05
> **lexxonnet said:**
> Hmm... I've been having this problem on both an upgrade from feisty and a fresh install of gutsy. Usually happens when yakuake is rolled up (I disabled animation) with any sort of composite manager running (both kwin-composite(kde3) and compiz-fusion). 

Here is the backtrace
```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/bin/X [0x817e39d]
3: /usr/bin/X [0x817a9ef]
4: /usr/bin/X(CompositeGlyphs+0x9a) [0x816129a]
5: /usr/bin/X [0x8168f19]
6: /usr/bin/X [0x8164315]
7: /usr/bin/X [0x815754e]
8: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
9: /usr/bin/X(main+0x495) [0x8076f05]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d4a050]
11: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting

```
It seems even more frequent when yakuake has multiple tabs open, and especially if its running apt in one of them.


Same here concerning yakuake and apt-get...

---

### Post by lexxonnet on 2007-12-06
Hmm... it seems to be quite a common problem... time to go bug hunting on launchpad

---

### Post by lexxonnet on 2007-12-06
Bug report is here :)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/165093](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/165093)

I think a couple more people should confirm the bug, since it is currently listed as an nvidia bug, but definitely seems to be Xorg related

---

