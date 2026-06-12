---
title: "Unresolved issue with keyboard/mouse sharing 11.04/10.04"
date: 2011-07-15
forum: Desktop Environments
---

### Post by aspidistra on 2011-07-15
Problem with x2x - bug 385357 raised in 2009 doesn't seem to have been addressed

x2x is a facility which runs over ssh example:
"ssh -X dan@main -C "x2x -east -to :0" <- allows you to control the mouse/keyboard on the machine to the right of you (as long as x2x is installed on it).

I looked around when I got sick of this bug happening -- found the bug has been registered before

surprised that the bug reports only 3 people effected -- this bug with the use of x2x on 11.04/10.04 means that if you use x2x you will get spurious repeats of characters from x2x client to the machine it controls.  This I have found is a lot worse in 11.04 which renders x2x unuseable.  

There is another way of multiple desktops this is synergy with the gui interface 'quicksynergy' available from synaptic.  Probably uses the same underlying mechanism -- fault is still extant with that.  Pretty basic problem.  Maybe there is a basic  work-around.  

[https://bugs.launchpad.net/ubuntu/+source/x2x/+bug/385357](https://bugs.launchpad.net/ubuntu/+source/x2x/+bug/385357)

Bug registered 2009 --- nothing done about it.  Why not?  I have only just got around to registering for this forum -- long term ubuntu user and also do much support. 

paste of bug report from site above below.

.... minutes later:  just found this 

[http://synergy-foss.org/pm/issues/1902](http://synergy-foss.org/pm/issues/1902)

"fixed in 1.0.7. key repeat is disabled while the mouse is
on an X11 client and restored when off the client. also
suppressing key repeat on any key configured on the client's
X11 display to not auto-repeat, which prevents win32 from
causing modifier key auto-repeat on X11 (win32 auto-repeats
modifiers but X11 does not)."

but I'm not sure exactly what this means.  So the problem is "key repeat"

Right (later again):

SOLUTION:  go to system > preferences > keyboard on machine you are 
controlling with x2x or synergy.  Untick the box [x] key presses 
repeat when key is held down.  The repeat facility will still work
on the machine you are controlling -- it just seemed that it is a 
keyboard facility which over-rides x2x - both the controlling and 
controlled machine are issuing repeats which means you get too many
(over-sensitized) on the controlled machine.

Can somebody update the bug reports above to clarify this (it's not
really a bug).

> 

BUG REPORT:

[https://bugs.launchpad.net/ubuntu/+source/x2x/+bug/385357](https://bugs.launchpad.net/ubuntu/+source/x2x/+bug/385357)


Binary package hint: x2x

I use 'ssh -X othermachine x2x -north -from :0' to have my laptop's keyboard and mouse control two computers. Usually this works pretty well. Sometimes, and especially if the network is busy with other traffic, x2x starts

Sometimes (and especially if the network is loaded), x2x starts repeating the last keyboard event several times. Usually this is Enter, resulting in extra blank lines in the editor or shell; sometimes it's a letter resulting in wordddddddddddddds liiiiiiiiiiiike thissssssssssssss. On a couple of occasions the repetition never let up leaving me with two unusable computers until I pressed ctrl+alt+f1 and killed the ssh process, terminating x2x.

This last has just happened to me again, prompting this bug report. Both machines are running Ubuntu Jaunty.

ProblemType: Bug
Architecture: i386
DistroRelease: Ubuntu 9.04
Package: x2x 1.27.svn.20060501-4
ProcEnviron:
 LC_CTYPE=lt_LT.UTF-8
 PATH=(custom, user)
 LANG=lt_LT.UTF-8
 SHELL=/bin/bash
SourcePackage: x2x
Uname: Linux 2.6.28-12-generic i686

report #2 :

This happens to me also. I experience the exact behavior as described by the bug report, in every detail (repeated characters occasionally, Enter often repeats, sometimes it repeats a character and x2x has to be killed to stop it). I also notice that the mouse pointer becomes sluggish. This is when I am at home on my wired network. When I am using a wireless network at work, the problem DOESN'T occur (which seems backwards to me).

The laptop running x2x is using Ubuntu Jaunty x86.

At home, the computer ssh'ed into the laptop via a wired ethernet connection is x86_64, and running Ubuntu Karmic (this is the problem configuration).

At work, the computer ssh'ed into the laptop via wireless is x64, and running Debian Squeeze (this is the configuration that seems flawless).

---

