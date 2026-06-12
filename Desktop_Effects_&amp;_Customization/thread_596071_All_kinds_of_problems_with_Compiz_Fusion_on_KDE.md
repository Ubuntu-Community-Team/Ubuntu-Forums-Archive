---
title: "All kinds of problems with Compiz Fusion on KDE"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by rocketman768 on 2007-10-29
I can't get compiz fusion to work with KDE. I installed all the packages I was supposed to (I think), then went to Setting->Advanced Desktop Effects Settings and saw all the plugins and crap. However, none of the fancy stuff was happening. Here is a list of the packages I have installed:

```
compiz
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-kde
compiz-plugins
compizconfig-settings-manager
libcompizconfig-backend-gconf
libcompizconfig-backend-kconfig
libcompizconfig0
python-compizconfig
```

I saw somewhere that you have to do "compiz --replace" to get things up and running. Is that right?
When I type "compiz --replace" First thing that comes up is the kde crash screen with this report: "The application KWD (kde-window-decorator) crashed and caused the signal 11 (SIGSEGV)..."

Now, none of my windows have borders, so I can't move them. Here is the output of "compiz --replace":

```
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting kde-window-decorator
KCrash: Application 'kde-window-decorator' crashing...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

I saw that it did not find Xgl, so I tried installing that. However, when I did that, for some reason I no longer have direct rendering capability for OpenGL. WTF?

---

### Post by Zorael on 2007-10-29
Yes, I experience this as well.

The easy way out is to switch to Emerald. If you want to keep the theme there is a Kubuntu kwin theme copy over at kde-look.org somewhere. I grabbed Ardonis and mixed it up a bit, darkening the colors. :> It's all blue and purdy!

Then just either use fusion-icon to start them both, or
```
$ compiz --replace --ignore-desktop-hints &
$ emerald --replace &
```

--ignore-desktop-hints makes it work better with KDE's workspaces/desktops/viewports, but I still end up disabling that applet from my panel and just use Expo to get an overview.

And I've no idea about the xgl thing, I've got an Nvidia card.

---

### Post by jonray74 on 2007-10-29
the KDE doesn't seem to like Compiz-Fusion well at least for me cause I did have problems installing Compiz-Fusion on KDE, and I finally gave up and now i'm using GNOME. 

Before, KDE was home to me because of the MS Windows look alike personality, but when I had problems running Compiz-Fusion on it, I put GNOME and GNOME is now much better for me.

I do like KDE but for now, i'll stick with GNOME.

John

---

### Post by Zorael on 2007-10-29
I believe both kde-window-decorator and emerald are sort of old-ish and perhaps bug-ridden, but don't quote me on that.

Kubuntu certainly has been given less priority when it comes to integrating the desktop environment with Compiz-Fusion, but after a bit of tweaking I have it running fairly smoothly. Emerald crashes now and then, making me have to restart it, so I'm thinking about putting a script in ~/.kde/Autostart to load it (instead of fusion-icon, I guess).

Something like
```
#!/bin/bash

while true; do emerald --replace; sleep 2; done
```

I'm not sure that will work, but I *think* the script will wait after emerald --replace until Emerald exits/is replaced/crashes, then wait for two seconds and restart it. To end the cycle I just have to kill the process (killall [filename].

---

