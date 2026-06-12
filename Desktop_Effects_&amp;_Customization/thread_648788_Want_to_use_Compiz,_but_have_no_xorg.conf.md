---
title: "Want to use Compiz, but have no xorg.conf"
date: 2007-12-24
forum: Desktop Effects &amp; Customization
---

### Post by FxL on 2007-12-24
Hi... I just installed ubuntu (though I'm not a first time user), and I want to use Compiz and I have no xorg.conf file.

I tried 
```
sudo Xorg -configure
```

and this is what happened

```
Fatal server error:
Cannot move old log file ("/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"

fxl@fxl-desktop:/tmp$ cd
fxl@fxl-desktop:~$ sudo Xorg -configure

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux fxl-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 23 22:19:48 2007
List of video drivers:
        trident
        i740
        r128
        via
        ati
        chips
        tga
        i810
        s3virge
        nv
        dummy
        glint
        v4l
        apm
        psb
        cirrus
        nsc
        intel
        newport
        vmware
        tseng
        neomagic
        siliconmotion
        ztv
        tdfx
        voodoo
        sisusb
        radeon
        rendition
        cyrix
        s3
        imstt
        fglrx
        i128
        ark
        mga
        savage
        sis
        atimisc
        amd
        fbdev
        vesa
        vga

(EE) LoadModule: Module ztv does not have a ztvModuleData data object.
(EE) Failed to load module "ztv" (invalid module, 0)


Backtrace:
0: Xorg(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxProbeMain+0x13d) [0xb769d3ed]
3: Xorg(DoConfigure+0x228) [0x80ba7c8]
4: Xorg(InitOutput+0x655) [0x80a8b05]
5: Xorg(main+0x27b) [0x8076ceb]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d25050]
7: Xorg(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting





























Aborted (core dumped)
```

Any solutions/ideas??

---

### Post by Ub1476 on 2007-12-24
I think you have a xorg.conf, else you wouldn't be able to log into Ubuntu. Post the outpout of:

```
cd /etc/X11
dir
```

You'll find xorg.conf when typing "dir". If you have any issues with Visual Effects, please post the output of this:

```
compiz --replace

lspci | grep VGA
```

---

### Post by FxL on 2007-12-24
Ok, thanks... I got it all figured out.

I found a different thread and followed everything it said.

---

### Post by ~LoKe on 2007-12-24
Just for the record, Gutsy, as far as I know, has implemented bulletproof X.  That would mean that you could use an xserver without /etc/X11/xorg.conf.

---

### Post by MaX on 2008-03-14
> **FxL said:**
> Ok, thanks... I got it all figured out.

I found a different thread and followed everything it said.

It would be great if you could post a link to that thread...:confused:

---

