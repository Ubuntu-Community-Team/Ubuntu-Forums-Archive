---
title: "Still having a problem with video playback."
date: 2005-08-14
forum: Desktop Environments
---

### Post by Dolphin on 2005-08-14
So I figured out how to enable DMA, that's not the problem.
While enabling DMA did with this issue, it did not correct it.

If I play any video in xine, be it on my HD or on DVD, it looks okay for a bit then it starts dropping frames.  Nothing major, but noticable and irritating.  If I go to full-screen mode, though, the frame loss is major and I can't do anything after that.  (Close the program, take it out of fullscreen, stop it, anything)

Can someone please help?  This is getting frustrating.

Thanks.

---

### Post by Hairy_Palms on 2005-08-14
i dont know about xine but i had the same problem in mplayer and the way to solve it is to change the video driver in the program (xine) to x11/xv

---

### Post by Dolphin on 2005-08-14
I see.  How would I do that?

---

### Post by chruesu on 2005-08-14
Hi Dolphin

The first time I tried to use xine, I had similar probs like you. So, maybe I can help 'coz xine is running like a charm now:

what does "xine-check" said?

it should look like this:
```
$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.10-5-686)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/bin/xine-config in your PATH
[ good ] plugin directory /usr/lib/xine/plugins/1.0.0 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hda
[ good ] /dev/dvd points to /dev/hda
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 UYVY YV12 I420
:~$

```

In order to change the video driver:
run xine
right click on the window
choose settings
choose register gui
change experience-level to advanced
press aply
choose register video
choose the driver

---

### Post by Dolphin on 2005-08-14
```
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.10-5-386)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ hint ] No xine-config found. Assuming xine from Debian package
         The xine-config script can be used to deternime some file locations
         used by xine-lib, but you don't have such a script on your system.
         However, it looks like you installed xine from the Debian packages.
         So I'll just guess that you are using the standard locations.
         If you want me to be sure about those file locations, you can install
         the 'libxine-dev' package, which contains xine-config. However, this
         package is not really needed to run xine...
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins exists.
[ good ] found unknown plugin: *.so
[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to to color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)
         press <enter> to continue...

[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to to color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)
         press <enter> to continue...

[ hint ] Your X server doesn't have any XVideo support...
         XVideo is an X server extension introduced by XFree86 4.x. This
         extension provides access to hardware accelerated color space
         conversion and scaling, which gives a great performance boost.
         If you have a fast (>1GHz) machine, you may be able to watch all
         kinds of video, anyway. You will waste lots of CPU cycles, though...
         press <enter> to continue...

```

Why is there so many "OUCH's"?  How do I fix this?

---

### Post by chruesu on 2005-08-15
okey, #1 try to re-install libxine1 and libxine-dev

```
sudo apt-get install libxine1 libxine-dev
```

in regard to the "Your X server doesn't support YV12 overlays"-issue:

I had the same prob. Then, somebody told be to configure my X-server (xorg.conf) correctly with all accurate drivers properly installed
...very helpful :-|

In fact, I downloaded the ATI-Driver-Installer ('coz I have a ATI-Video-Card)
look at [this HowTo](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=ati+radeon+mobility+x600)  written by Jesus

Due to a complete reset of my OS I don't have the ATI-Driver installed currently.
I just have Ubuntu as it comes out of the box plus the fglrx-packages
If I type glxgears I have only about 200-300 FPS - this is terribly bad but still enough to watch DVD's

---

### Post by Dolphin on 2005-08-15
[QUOTE=chruesu]okey, #1 try to re-install libxine1 and libxine-dev

```
sudo apt-get install libxine1 libxine-dev
```

in regard to the "Your X server doesn't support YV12 overlays"-issue:

I had the same prob. Then, somebody told be to configure my X-server (xorg.conf) correctly with all accurate drivers properly installed
...very helpful :-|

In fact, I downloaded the ATI-Driver-Installer ('coz I have a ATI-Video-Card)
look at [this HowTo](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=ati+radeon+mobility+x600)  written by Jesus

Due to a complete reset of my OS I don't have the ATI-Driver installed currently.
I just have Ubuntu as it comes out of the box plus the fglrx-packages
If I type glxgears I have only about 200-300 FPS - this is terribly bad but still enough to watch DVD's[/QUOTE]

Thanks, that got rid of all my "OUCH's" but I still have the "HINT's" I have to take care of.

My ATI drivers are the latest already.  fglrx 8.14.13.  Do I still edit xorg.conf to fix the "HINT's"?  If so, what do I change?

Thanks.

---

### Post by Dolphin on 2005-08-15
Bump

---

