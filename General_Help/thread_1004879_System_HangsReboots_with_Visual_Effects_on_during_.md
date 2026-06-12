---
title: "System Hangs/Reboots with Visual Effects on during video playback"
date: 2008-12-07
forum: General Help
---

### Post by p314i on 2008-12-07
Hello all.

I have stumbled across a problem that I have not been able to find an answer for.  I am relatively new to Ubuntu, but cut my teeth on various flavors of Unix as a kid and ran Red Hat on my machine a decade ago.  To some extent, I'm returning home, and it is very nice.  However, I have run into a pernicious problem that I cannot find an answer for.  Any help or suggestions where to turn would be much appreciated

The terse explanation is when my Visual Effects are set to None, my system is rock solid stable.  When I turn my Visual Effects to Normal with Desktop Cube and Rotate Cube turned on, my system will hang when watching video with either VLC or Totem and requires a physical power down.  I am running Hardy 8.04 on a AMD 64 quad core with an ATI 4850 video card using the ATI drivers.

The longer explanation:
I built my box a couple months ago.
Installed Hardy Heron - Raid 1 setup.
Installed the ATI drivers following the instructions here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
Installed Wine to play a windows game.
Had some problems with Wine.
Read some web pages and found that I should disable Visual Effects to make Wine happy.  Did so.
Quit playing said game.
System was stable for months - I fell in love.

Decided I should get some use out of my graphics card.
Enabled Visual Effects.
Enabled Desktop Cube and Rotate Cube.
Watched some videos in VLC.  VLC froze.  In my case this means the screen froze and the audio repeated a very short clip over and over, so it sounded like tick-tick-tick-tick...
Nothing would unfreeze it.  Tried everything I knew of.  alt-backspace, nothing.  alt-sysrq-b, nothing.  Had to power down to restart.

Looked into the problem.
Looked at my logs, found a weird audio error.
Stumbled across this post on pulse audio:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=protocol-native.c%3A+Failed+push](http://ubuntuforums.org/showthread.php?t=789578&highlight=protocol-native.c%3A+Failed+push)
Followed the instructions there.
That seemed to change my hanging video problem to a rebooting problem.  Specifically, when playing a video in VLC my machine would behave well for a couple hours and then just mystically reboot in the middle of a video.
Tried using Totem instead of VLC.  That took the reboot behavior back to the hang behavior - not helpful.

Switched back to VLC.  Random unresponsive hangs when playing video.
I have tried running VLC from a terminal and piping the output to a file.  When it hangs and requires a reboot, nothing in the file indicates any errors.  
I have looked through my system logs and there are no error messages associated with the system hang.

To summarize, the system is stable and will play hours of video if Visual Effects are set to None.  The system is seemingly stable, but will crash randomly (after an hour or two) during video playback (in VLC or Totem) while Visual Effects are turned on.

If there is any other information that I can provide, please let me know.

Thanks for any help or direction you can give me.

---

### Post by p314i on 2008-12-07
I tried playing a video with Visual Effects set to Normal but the Cube turned off.  After a couple hours, the reboot effect happened.

The cube does not seem to be the issue, regrettably.  The Visual Effects seem to be the issue.

Any suggestions?

---

### Post by matteojg on 2009-01-03
I have a conflict between the cube desktop and video as well. If I have the cube enabled the VLM player just shows a black screen (audio still works) and/or freezes. The cube has also "collapsed" on me if I had many open windows...Gnome seems to automatically set visual effects to none and 1 workspace.

I ran the hardware test with the cube enabled and the video test fails (no static and no color bars), but it still works with advanced effects as long as the cube is not enabled.

My best guess is that this is a driver related issue.

Dell Inspiron 600m
Ubuntu 8.10 (Intrepid Ibex)
Gnome 2.24.1
Memory 250 MiB
Intel Pentium 1.5 Ghz

And according to the compiz-check applet:

 Graphics chip:         ATI Technologies Inc Radeon RV250 [Mobility  FireGL 9000] (rev 02)
 Driver in use:         radeon
 Rendering method:      AIGLX

---

### Post by Forlong on 2009-01-03
**matteojg**, I think there is no way to run a video while spinning the cube for you. First of all, I think the graphics chip is not powerful enough, but it's also not supported by the official ATI driver anymore, which is from my experience the only way to provide this on ATI cards.

---

### Post by matteojg on 2009-01-03
Being able to play videos with the cube would have been neat, but not being able to is hardly a problem.

I'm confused about Ubuntu and drivers though Forlong...your compiz-check (thanks for the handy script) says radeon is the driver in use by my system, but when I run the 3rd party hardware configuration (System>Hardware Drivers) it says "No proprietary drivers are in use on this system". What do I make of this? Is your script right, and my system is still using radeon as it was under windows?, Or is hardware config. right, and my system is using some open source driver that came with the Intrepid install?

Ahh..radeon IS an open source driver, I just assumed it was proprietary.

---

### Post by Forlong on 2009-01-03
> **matteojg said:**
> Ahh..radeon IS an open source driver, I just assumed it was proprietary.
That's right, the proprietary one is **fglrx**.

---

### Post by matteojg on 2009-01-03
Might it be possible to tweak the driver enough Forlong? 
I opened xorg.config but all I see is:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Is this normal?

---

### Post by alidm on 2009-02-22
I came across the same problem when I tried to play videos with my desktop-effects on. I'm running kubuntu 8.10, with AMD/ATI proprietary driver, fglrx, installed. I tried Dragon Player, VLC, and MPlayer. All turned to a frozen desktop, and nothing would get it back to work but a hardware power down. I don't use compiz, emerald, or any other external desktop management packages. The basic kwin component coming out with standard KDE package is the only thing controlling my desktop. If I turn desktop-effects off, everything gets fine, and I can play video without any problems.

---

