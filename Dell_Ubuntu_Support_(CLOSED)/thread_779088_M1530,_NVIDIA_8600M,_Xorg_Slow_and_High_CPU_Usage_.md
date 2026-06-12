---
title: "M1530, NVIDIA 8600M, Xorg: Slow and High CPU Usage (8.04)"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mattyp123 on 2008-05-02
Hey All,

I've got an M1530 which ran very well with 7.10 - after upgrading to 8.04 (I tried the upgrade first, then wiped and did a clean install - this problem happened with both installs) I have some big performance issues.

First - some stats (in a code block for clarity):
```

/proc/cpuinfo: ... Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz

uname  -a: Linux thoth 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

NVIDIA settings: NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008

relevant xorg.conf line: Driver		"nvidia"

free:
total       used       free
3114548    1927724    1186824 

```

So here's a bit of what I'm experiencing:

High CPU usage:
[LIST]
[*]When using Compiz effects (sure I can turn them off, but they worked in 7.10) - such as rotate desktop cube - the CPU spikes to 50% for a split second
[*]When running glxgears (just for testing), Xorg rockets from 4% CPU to 36% CPU
[*]When switching tabs in Firefox, CPU spikes (and it is very slow)
[*]When switching desktops the CPU spikes briefly and it takes a second for the windows to come into focus
[*]Lag when typing in OpenOffice - coinciding with occasional CPU spikes
[/LIST]
... the list goes on

None of this happened in 7.10 (and I *could* downgrade, but I'd rather not). Hardware hasn't changed.

Anyone have any clues on what could be causing this?

Thanks in advance
-Matt

---

### Post by mattyp123 on 2008-05-04
Hrm - so I take it I somehow have a singular problem, eh?

---

### Post by LeoSolaris on 2008-05-04
I've noticed that when I activate my widget layer, the cpu jumps to 99% for just a heartbeat, then back down to 5-7%. Thats with a Core 2 Duo 5250. It hasn't impaired anything yet...

---

### Post by mattyp123 on 2008-05-05
Yeah, I don't have the widget layer turned on... it's one of those really odd situations. I think I might downgrade back to 7.10 at this point - I can't have every 500th character I type in openoffice not show on the screen until about 2 seconds after I type it... hrmph.

---

### Post by j3no on 2008-05-21
I have the same problem.. expecially when I change the 
workspace on Xfce

---

### Post by raphoun on 2008-05-25
On my M1530 ubuntu is quite slow too, I think it the fault of the poor nvidia driver with a 8600gt.
I have micro freeze with compiz, it's not smooth.
For me it's unusable, my other computer with a 6600gt works so better.

---

### Post by mattyp123 on 2008-05-27
Yeah, it is likely the 8600GT. I sold my Dell and bought a Sager (Compal JFL92) which also has an 8600GT - same problem.

It appears something with NVIDIA is bustificated.

---

### Post by raphoun on 2008-05-27
If I use XGL it's working o lot better you should all try

---

### Post by mattyp123 on 2008-05-29
> **raphoun said:**
> If I use XGL it's working o lot better you should all try

Yeah, XGL helps... dunno why the "new" version is so much worse on a new chipset, but hey - good suggestion, thanks!

---

### Post by raphoun on 2008-05-29
Hello all,

Today new nvidia drivers has been released, I just installed it and it works faster.
[http://www.nvidia.com/object/linux_display_ia32_173.14.05.html]("http://www.nvidia.com/object/linux_display_ia32_173.14.05.html")

And this is the option I putted in my xorg.conf:

Option "PixmapCacheSize" "200000" 
 Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "True" # Experimental
    Option         "BackingStore" "True" # Experimental

And i wrote  sudo nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1 in a terminal 
*As was mentioned in the 173.08 beta release, 173.14.05 contains support for an experimental glyph cache on the GeForce 8 and 9 series that may improve anti-aliased font rendering performance. This support can be enabled by running nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1.*

---

### Post by Jeanpaul145 on 2008-06-20
> **raphoun said:**
> If I use XGL it's working o lot better you should all try

Hey thanx, I hadn't thought of installing XGL, but you're absolutely right!
The framerate seems to be quite satisfactory after installing it and rebooting :guitar:

---

### Post by raphoun on 2008-06-20
yes and with the new nvidia beta driver (177.13) it's work better without xgl :guitar:

---

### Post by sdennie on 2008-06-20
If you'd prefer not to use XGL, it's possible that you are just running into problems with PowerMizer not scaling up fast enough (this is especially obvious when using compiz).  I've written a small tutorial on how to keep the card running at full speed on AC power and the default power settings on battery power here: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

---

