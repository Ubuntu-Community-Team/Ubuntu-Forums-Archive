---
title: "mplayer with -vo xv crashes X"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Minilek on 2006-09-03
I'm using the ATI proprietary drivers (version 8.28.8) on dapper, and when using xvideo video output on mplayer (mplayer -vo xv), X crashes and restarts itself.  Using -vo x11 doesn't cause any problems.  The output on stderr is as follows:

```

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.


MPlayer interrupted by signal 13 in module: flip_page
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 99 requests (93 known processed) with 0 events remaining.

```

Has anyone experienced this?

---

### Post by Ranime on 2006-09-07
I have the same sort of problem...

I installed some Bluetooth apps that didn't work for me, so I uninstalled them using Synaptic.

After that, my mplayer, totem and xine are messed up! Every time I want to play a video file, X is resetted and I'm facing the Gnome login screen...

Any insight would be greatly apreaciated. (sorry for my bad English!)

](*,)

---

### Post by tassou on 2006-09-08
Hello,

I'm facing the same problem on a AMD64 arch with an X1800 and up to date fglrx drivers. If XV is used, X crash. When using xinerama, there is no Xv at all. Any help would be much appreciated, thank you.

---

### Post by Minilek on 2006-09-09
> **tassou said:**
> Hello,

I'm facing the same problem on a AMD64 arch with an X1800 and up to date fglrx drivers. If XV is used, X crash. When using xinerama, there is no Xv at all. Any help would be much appreciated, thank you.

Actually, it's the same for me.  An X1800 on an amd64 with up-to-date fglrx drivers.  Using older drivers still doesn't help my problems (X1800 began being supported with 8.24.8 ).  I never had this problem in Breezy, so I'm guessing maybe the issue has to do with X 7.0.

---

