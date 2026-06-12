---
title: "fglrx driver issue with Unity3D games"
date: 2014-05-05
forum: Gaming &amp; Leisure
---

### Post by DeKugelschieber on 2014-05-05
Hi,

I'm experiencing some issues with Unity3D games (the game engine, not the desktop environment).
The games freeze my whole desktop and block input (I have to hard reset).

These are the errors I found in the Xorg log:

```

[    25.979] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    25.980] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    25.980] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]

```

I tried to link the fglrx_dri.so that I found to the desired locations (which I had to set up).
The first and second error were linked to the 64bit version and the last one to the 32bit (or at least I think I did that).
I also tried to use a different driver (currently it's the default stable driver delivered with 14.04), catalyst 14.4, 14.3, 14.1 and the ubuntu 14.04 fglrx-updates...

But I still get desktop freezes and these errors.
Any solutions?

---

### Post by DeKugelschieber on 2014-05-06
Ok it seems like I fixed that errors by linking like before, except that I hard linked now.
But I still get this error early in the log file:

```
[    22.357] Markers: (--) probed, (**) from config file, (==) default setting,	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
```

Nekro runns smoothly now... but KSP still crashes.

---

### Post by JoZ3 on 2014-07-13
Same error here, crashed games: Rust, Planet Explorer and Fight the dragons... Using the lates catalyst drivers and i don have errors in my xorg, only a few warning message

---

### Post by oldrocker99 on 2014-07-13
I had a similar crash, trying to play native X-COM with the **nVidia** drivers, until I installed a beta 3.40 from nVidia. For what it's worth.

I do know that a number of games appear to run better with the open-source radeon driver than with fglrx, which has problematical since 9.04 for we users. It might be worth a try if you completely removed fglrx and installed the radeon drivers, which are in the repos. Synaptic is great for that. You may be pleasantly surprised, or disappointed. Only one way to find out. 

You can always reinstall fglrx, or you can go to their site. Their current version number is 9.3.

---

### Post by manofwar95 on 2014-10-28
Hate to dig up old dirt. But this is still a relevant issue, not just on Ubuntu. It appears to be a problem with FGLRX and the unity3d engine 

Also, want to mention that 

```

[    22.357] Markers: (--) probed, (**) from config file, (==) default setting,	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```

Is a legend, for the what those markers mean in your Xorg.0.log

---

