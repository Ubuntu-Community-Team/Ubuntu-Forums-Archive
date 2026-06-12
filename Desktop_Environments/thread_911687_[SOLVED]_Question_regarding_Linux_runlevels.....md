---
title: "[SOLVED] Question regarding Linux runlevels...."
date: 2008-09-05
forum: Desktop Environments
---

### Post by Predator106 on 2008-09-05
Hello, I'm a bit confused on runlevels, using the tool 'sysv-rc-conf' I can see multiple "daemons", but there are a lot of them (almost all) that have multiple runlevels. My real question is, what is the difference, and the point of using multiple runlevels, wouldn't the first one make the most difference. I thought it was to set which order it would boot in, why would you have it boot at runlevel S, and then 1, and then 3, etc. I don't understand this concept... do they get... skipped on occasions or something, does this mean it can be pushed back or something? I figured it would be like a kind of priority, setting up which exact order they start up in....Is it actually starting the daemon AGAIN? I find that doubtful, but hey, just trying to figure it out...

---

### Post by jpkotta on 2008-09-05
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html).  

Some of it is obsolete.  Ubuntu no longer has a /etc/inittab, now it is /etc/event/.

Generally, on boot, you enter a "pseudo runlevel" (/etc/rc.S), then enter 2.  "Rescue mode" boots into level 1.  

The reason behind them is you can put the machine in a different mode.  Maybe you want to have a "no network" mode, you can configure level 3 to do that.  Personally, I think they are way too complicated and weird for the job that they do, but that's the way things are until something better comes along.

---

### Post by Pelham123 on 2008-09-05
Are you thinking that the bootup process runs through all the runlevels in order? Because only 1 runlevel is ever *active*

Have a look at the first couple of paragraphs here, which might makes things clearer...

[http://www.linfo.org/runlevel_command.html](http://www.linfo.org/runlevel_command.html)

Although Ubuntu usually runs in level 2, not 5. Different Linux distros have different default runlevels.

---

### Post by david_lynch on 2008-09-06
Yes I was surprised to find that ubuntu departed from old standards in their runlevel scheme. Most unixes including solaris, irix, hpux, redhat, suse etc use the classic sysv runelevels:

0 = halt (poweroff)
1 = single user (maint mode)
2 = non-networed mode (terminal)
3 = networked multiuser mode (terminal)
4 = not normally used
5 = multiuser, networked, with xdm
6 = reboot

aix uses some weird scheme with 9 runlevels, while bsd and some linux distros e.g. slackware use a limited runlevel scheme like ubuntu. I guess it works but it takes some getting used to
:guitar:

---

### Post by Predator106 on 2008-09-06
> **Pelham123 said:**
> Are you thinking that the bootup process runs through all the runlevels in order? Because only 1 runlevel is ever *active*

Have a look at the first couple of paragraphs here, which might makes things clearer...

[http://www.linfo.org/runlevel_command.html](http://www.linfo.org/runlevel_command.html)

Although Ubuntu usually runs in level 2, not 5. Different Linux distros have different default runlevels.

Yeah, I was thinking that it was a way to kind of prioritize the OS, and that you could then boot into each different one if you wanted, kind of like different flavors of windows 'safe mode'.

Man, the sysv-rc-conf utility, should have a man page or runlevels have a man page to list them all and explain it, it doesn't look like there is a whole lot of info for it on Ubuntu, from what I've seen.

---

