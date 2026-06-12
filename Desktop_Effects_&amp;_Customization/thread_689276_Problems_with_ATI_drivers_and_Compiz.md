---
title: "Problems with ATI drivers and Compiz"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by Raum on 2008-02-06
Hello,

My problems are not related to performance... I've installed lastest ATI Driver, have a look to this post : [http://ubuntuforums.org/showthread.php?t=676704](http://ubuntuforums.org/showthread.php?t=676704)

But it's seem that I can't play a video, just like I can't play WoW with compiz activated.

[[img]http://graagb.free.fr/prob-compiz-mini.jpg[/img]](http://graagb.free.fr/prob-compiz.jpg)

Ehm... I think an OpenGL window is displayed above compiz layer... I see "flashing" effect (desktop / opengl window) with my video or 3D Window (World of Warcraft for example). 

As you can see on my capture, I've rotated my desktop but the video did'nt (and flashed or clipped with desktop).

I think ATI driver and Compiz are'nt compatible, or there is, somewhere, a misconfiguration ?

Do you ave any idea ?

I've tried :
```
aticonfig --overlay-type=opengl
```
and

```
aticonfig --overlay-type=Xv
```

unsuccessfully.... there is some parts of my xorg.conf :

```

Section "Module"
        Load  "glx"
        Load  "dbe"
        Load  "v4l"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BoardName   "ati"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "on"
        BusID       "PCI:1:0:0"
EndSection
```

(actually, I'm configured with "opengl" overlay)

Thanks

Raum

Merci

---

### Post by Raum on 2008-02-08
Well, welll, welll....... not so simple...

[http://bugs.freedesktop.org/show_bug.cgi?id=8732](http://bugs.freedesktop.org/show_bug.cgi?id=8732)


[http://dri.freedesktop.org/wiki/DirectRenderingToRedirectedWindows](http://dri.freedesktop.org/wiki/DirectRenderingToRedirectedWindows)

---

### Post by kelvin spratt on 2008-02-08
It would help if you posted your system specs first then people can try to help

---

### Post by linuxferret on 2008-02-08
> **Raum said:**
> Hello,

My problems are not related to performance... I've installed lastest ATI Driver, have a look to this post : [http://ubuntuforums.org/showthread.php?t=676704](http://ubuntuforums.org/showthread.php?t=676704)

But it's seem that I can't play a video, just like I can't play WoW with compiz activated.

[[img]http://graagb.free.fr/prob-compiz-mini.jpg[/img]](http://graagb.free.fr/prob-compiz.jpg)

Ehm... I think an OpenGL window is displayed above compiz layer... I see "flashing" effect (desktop / opengl window) with my video or 3D Window (World of Warcraft for example). 

As you can see on my capture, I've rotated my desktop but the video did'nt (and flashed or clipped with desktop).

I think ATI driver and Compiz are'nt compatible, or there is, somewhere, a misconfiguration ?

Do you ave any idea ?

I've tried :
```
aticonfig --overlay-type=opengl
```
and

```
aticonfig --overlay-type=Xv
```

unsuccessfully.... there is some parts of my xorg.conf :

```

Section "Module"
        Load  "glx"
        Load  "dbe"
        Load  "v4l"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BoardName   "ati"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "on"
        BusID       "PCI:1:0:0"
EndSection
```

(actually, I'm configured with "opengl" overlay)

Thanks

Raum

Merci

my advice, just get rid of compiz - more trouble than its worth.  i too have an ati graphics card and with compiz installed i had all sorts of problems - windows tearing, jerky scrolling, screen corruption.  uninstalled compiz and not had a problem since.  who needs wobbly windows anyway?

---

### Post by Raum on 2008-02-08
Hello,

Kevin, you could follow my link [http://ubuntuforums.org/showthread.php?t=676704](http://ubuntuforums.org/showthread.php?t=676704) where I've described all my specs. But quickly Ubuntu 7.10, ATI Radeon HD 3850, ATI Catalyst 8.10.

@Linuxferret, hey it's funny !!! :)

---

