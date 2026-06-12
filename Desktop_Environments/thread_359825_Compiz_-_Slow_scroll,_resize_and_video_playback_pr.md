---
title: "Compiz - Slow scroll, resize and video playback problem"
date: 2007-02-12
forum: Desktop Environments
---

### Post by Blueshift on 2007-02-12
I finally got compiz working on my IBM - X31 featuring the ATI Radeon 7000 (Model M6). I have however a few questions on improving the speed and usability of the compiz add-on. 

First off I was wondering if anyone have the slow resize of window problem and the slow scrolling problem? And is there any way of optimizing this issue? Another big problem I have is when I'm watching a video or playing a videostream over the Internet. There is a lot of flickering going on and after some time the image totally disappears! A similar effect occurs when using Google Earth, as you zoom in a lot of flickering occurs!

I have installed Compiz version 0.3.6 from gandalfn: [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy)

I have edited the xorg.conf file in light of:
[http://www.ubuntuforums.org/showthread.php?t=246746&highlight=ati+radeon+aiglx](http://www.ubuntuforums.org/showthread.php?t=246746&highlight=ati+radeon+aiglx)
[http://www.die.net/doc/linux/man/man4/radeon.4.html](http://www.die.net/doc/linux/man/man4/radeon.4.html)
[http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver](http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver)

Any tips or help on this would be much appreciated! :)

---

### Post by fuoco on 2007-02-20
I seem to have a similar problem - did you find a solution?

---

### Post by Blueshift on 2007-02-21
There is a follow up at

[http://forum.go-compiz.org/viewtopic.php?t=549&highlight=slow+scroll](http://forum.go-compiz.org/viewtopic.php?t=549&highlight=slow+scroll)

but didn't help me much I'm afraid...

---

### Post by Christian Neumair on 2007-02-23
> **Blueshift said:**
> There is a follow up at

[http://forum.go-compiz.org/viewtopic.php?t=549&highlight=slow+scroll](http://forum.go-compiz.org/viewtopic.php?t=549&highlight=slow+scroll)

but didn't help me much I'm afraid...

I recompiled the xserver-xgl with the [XGL speedup patch]("http://www.go-compiz.org/index.php?title=Patch_to_make_XGL_faster") referenced in the URL you mention.

Suddently, Xgl / Compiz played back fullscreen videos flawlessly :). I'm using X300 (M22 5460) + fglrx.

I will not provide a package as I don't think it's best practice to randomly spread hacky packages in the web for beta software, and once people start trusting everybody this can yield much damage because you'll potentially download virii.

A little howto, though:

Copy the code from the URI above and paste it in a local file located wherever you want (let's assume ~/foo.patch).

Install fakeroot if it isn't installed yet. It's in the "fakeroot" package.
Now, download and build the xserver-xgl package, applying the patch you downloaded:

```

mkdir ~/packages
cd ~/packages
sudo apt-get build-dep xserver-xgl
apt-get source xserver-xgl
cd x*/
patch -p1 < ~/foo.patch
fakeroot dpkg-buildpackage -us -uc
sudo dpkg -i ../x*.deb

```

And voila, your performance should be acceptable. I haven't spotted any bad side effects yet, but don't nail me on that since I don't understand precisely what the patch does.

The old code that has been commented out seems to ensure that pixmaps inherit the onscreen contents of their parents, to display something reasonable in case they have no background set. This sounds a lot like putpixel and doesn't seem to be neccessary in the offscreen/composited case. I don't know why, but it is probably very expensive when compositing is active.

---

### Post by Christian Neumair on 2007-02-23
Sorry, the video playback isn't flawless after rebuilding with the patch. My test case just wasn't representative as it had a low resolution (Louis Armstrong at Ed Sullivan).

---

### Post by Christian Neumair on 2007-02-24
OK, a bit more patchery to totem made video playback run flawlessly! :) The culprit is XV, which seems to interfere with compositing.

Here is a little HOWTO for a smooth video player experience. I haven't tested whether this only works properly after patching the xgl package, but unrelated speedups shouldn't hurt.

As with xegl, download the totem sources, and apply another patch:

```

--- totem-2.16.2.orig/configure.in
+++ totem-2.16.2/configure.in
@@ -571,10 +571,10 @@
 AC_SUBST(XTEST_LIBS)

 have_xvidmode=no
-AC_CHECK_LIB(Xxf86vm, XF86VidModeQueryExtension,
-       XVIDMODE_LIBS="-lXxf86vm"
-       have_xvidmode=yes,,
-       $X_LIBRARIES -lXext)
+#AC_CHECK_LIB(Xxf86vm, XF86VidModeQueryExtension,
+#      XVIDMODE_LIBS="-lXxf86vm"
+#      have_xvidmode=yes,,
+#      $X_LIBRARIES -lXext)

 have_randr=no
 AC_CHECK_LIB(Xrandr, XRRUpdateConfiguration,

```

The precise order of commands is:
```

cd ~/packages
sudo apt-get build-dep totem
apt-get source totem
patch -p1 < wherethepatchresides.diff
fakeroot dpkg-buildpackage -us -uc

```

So, now you have shiny totem packages without XV, install the correct package using

```

sudo dpkg -i ../totem-gstreamer*.deb

```

or

```

sudo dpkg -i ../totem-xine*.deb

```

Depending on which one is have installed already.

Note that for Totem/Gstreamer, you'll additionally have to bring up "gstreamer-properties" (or add "Multimedia System" to the control panel using the menu editor and click this launcher) and set the video output to "X Window System (no Xv)".


Regarding MPlayer: Neither vo=sdl nor vo=sdl:nohwaccel [which I use for proper fullscreen toggling support] run smooth, and while vo=x11 runs smooth it doesn't adapt its size to the MPlayer window. So you'll have to live without MPlayer, manually zoom in with compiz, wait until I'll have some time to figure out whether compiling MPlayer without Xv support helps (is possible at all), or figure out yourself what's making playback slow here.

---

### Post by fuoco on 2007-02-24
I don't understand why you need the patch. XV really doesn't work very well, but when I use 'gstreamer-properties' to select 'no XV' video works fine (without any patches to any software) - but it's really slow and resources hungry, hardly usable...

Don't we have another option? ultimately shouldn't XV be fixed so it works with composite? are there any such efforts?

---

### Post by chris.mccauley on 2007-09-03
Have to backup that last comment. Turning off xv and using totem fixed this problem for me. Previously I had been switching off xserver-xgl to watch DVD's and then enabling for nomral work - a pain even though it only involves logging in again. Performance with xv off is pretty acceptable even on my four year old Inspiron 8600. Definitely safer than patching an evolving package.

---

### Post by LouisChappell on 2008-01-02
Sorry to bring back a deceased post but the links provided in the 3rd post don't seem to be working, could someone provide a fresh one please?

---

### Post by kalmi on 2008-04-26
[http://compiz.org/Patch_to_make_XGL_faster](http://compiz.org/Patch_to_make_XGL_faster)

btw according to this( [http://forum.compiz-fusion.org/archive/index.php/t-246.html](http://forum.compiz-fusion.org/archive/index.php/t-246.html) ) the patch is in xgl by default.

---

