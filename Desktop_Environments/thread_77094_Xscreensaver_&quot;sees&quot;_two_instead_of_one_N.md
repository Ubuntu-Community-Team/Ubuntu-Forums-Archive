---
title: "Xscreensaver &quot;sees&quot; two instead of one Nvidia Twinview display and is painfully slow."
date: 2005-10-16
forum: Desktop Environments
---

### Post by netztier on 2005-10-16
Hi all!

I moved from Hoary to Breezy yesterday (added breezy to /etc/apt/sources.list and went throug **aptitude dist-upgrade**).

After some fiddling with wrong kernel-images being installed (-i386 instead of -k7) and fixing the following nvidia-issue (wrong driver), I was happy having my X.org back on the screens.

I had left the xorg.conf with the handcrafted screen and TwinView setting untouched. Everything looked fine, until Xscreensaver came up. It filled the two screens independently instead of spanning the whole "picture" across the two screens - and it was unbelievably slow, less than 3 fps - and that on and AMD 64 3000+ (Venice) and an Nvidia FX5200.

For the sake of experimentation, I added a  **Option "Xinerama" "On"** to the ServerLayout option of xorg.conf. Guess what - Xscreensaver now spans across the two screens and runs at ~60fps.

Where is the mistake here? 

Xscreensaver not understanding what the nvidia module tells the X server about the screen layout? 

No proper OpenGL support in Nvidias TwinView mode? 

(GLX modules & stuff all properly loaded, DRI and GLcore deactivated, not a single "EE" line in Xorg.0.log)

I am a bit at a loss, here.

Any help appreciated.

Marc

---

### Post by netztier on 2005-10-20
I've been doing some reading-up in FAQs and stuff, and learned about things like
xwininfo and other "tricks". Now see this:

```

marc@cube:~$ **xwininfo -root**

xwininfo: Window id: 0x113 (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 2560
  Height: 1024
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
[COLOR="Red"]  -geometry 2560x1024+0+0[/COLOR]
```

So we do have a 2560x1024 screen, after all.

Do we? xscreensaver begs to differ, as it appears:

```
marc@cube:~$ **xscreensaver -verbose**
xscreensaver 4.21, copyright (c) 1991-2005 by Jamie Zawinski <jwz@jwz.org>.
xscreensaver: running as marc/users (1000/100)
xscreensaver: in process 8663.
xscreensaver: 22:04:24: 0: xscreensaver-gl-helper: GL visual is 0x21 (default).
xscreensaver: 22:04:24: 1: xscreensaver-gl-helper: GL visual is 0x21 (default).
xscreensaver: 22:04:24: running on display ":0.0" (2 Xinerama screens).
xscreensaver: 22:04:24: vendor is The X.Org Foundation, 60802000.
xscreensaver: 22:04:24: useful extensions:
xscreensaver: 22:04:24:   MIT Screen-Saver  <-- not supported at compile time!
xscreensaver: 22:04:24:   Shared Memory
xscreensaver: 22:04:24:   Double-Buffering
xscreensaver: 22:04:24:   Power Management
xscreensaver: 22:04:24:   GLX
xscreensaver: 22:04:24:   XF86 Video-Mode
xscreensaver: 22:04:24:   Xinerama
xscreensaver: 22:04:24:   Resize-and-Rotate
xscreensaver: 22:04:24: screen 0 non-colormapped depths: 24.
[COLOR="Red"]xscreensaver: 22:04:24: Xinerama layout:
xscreensaver: 22:04:24:   + 0/0: 1280x1024+0+0
xscreensaver: 22:04:24:     1/0: 1280x1024+1280+0[/COLOR]
xscreensaver: 22:04:24: selecting RANDR events
xscreensaver: 22:04:24: consulting /proc/interrupts for keyboard activity.
xscreensaver: 22:04:24: 0: xinerama vp: 1280x1024+0+0.
xscreensaver: 22:04:24: 0: visual 0x21 (TrueColor,   depth: 24, cmap: default)
xscreensaver: 22:04:24: 0: saver window is 0xa00001.
xscreensaver: 22:04:24: 1: xinerama vp: 1280x1024+1280+0.
xscreensaver: 22:04:24: 1: saver window is 0xa00005.
xscreensaver: 22:04:24: selecting events on extant windows... done.
xscreensaver: 22:04:24: mouse is on screen 0 of 2
xscreensaver: 22:04:24: awaiting idleness.

```

Now what? Are there any kown "TwinView" tweaks to xorg.conf ?

Who is providing the (incorrect) Information  about a Xinerama Dualscreen layout that
actually should not be there (we're not actually running Xinerama, but TwinView).

*scratches beard* 


regards

Marc

---

### Post by netztier on 2005-10-24
Hi all

I have some updated information on this issue:

In the forums on nvnews.net, I had started a thread for the same problem:

[http://www.nvnews.net/vbulletin/showthread.php?t=58237](http://www.nvnews.net/vbulletin/showthread.php?t=58237)

and what I have found can be summarized like this:

Running two OpenGL apps (from the 'hacks' in /usr/lib/xscreensaver) at the same time is detrimental to OpenGL performance. A single instance of glxgears runs at ~2400 fps, while two only get ~15fps each. I have no further info why this is so. Same goes for the other  OpenGL 'hacks': One is good, a second one - even in a small window - brings the whole system to it's knees.

However, a  'hack' launched from command line and then enlarged to fill the whole desktop stays fluid and fast and shows acceptable performance. 'flurry' for instance runs at 40-60fps in with the window size maxed out all over the desktop.

On the other hand, xscreensaver has changed it's behaviour on xinerama systems. From the release notes:

> 
[http://www.jwz.org/xscreensaver/changelog.html]("http://www.jwz.org/xscreensaver/changelog.html")

4.13 07-Sep-2003
On Xinerama systems, xscreensaver now runs one hack on each monitor (just like in ``real'' multi-head mode) instead of running one hack stretching across all the screens. Note that for this to work with any 3rd party screensavers, they must update their ``vroot.h'' file. 

I do not know what version xscreensaver was in hoary, but the version in breezy shows exactly this behaviour. This of course has the consequences of the miserable OpenGL performance, because it runs two 'hacks' instead of one.

Now why the performance is low with two OpenGL programs running, and why xscreensaver has been changed to run one 'hack' per screen are things i do not really know. Yet. :-). It might be simply the hardware limit imposed by the FX5200 which is known not to be *really* fast.

regards

Marc

---

