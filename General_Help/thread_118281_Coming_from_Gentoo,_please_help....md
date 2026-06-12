---
title: "Coming from Gentoo, please help..."
date: 2006-01-16
forum: General Help
---

### Post by ioannis.th on 2006-01-16
Hi! I recently moved from Gentoo, because I accidentally messed up my portage cache and my system was heavily customized so having to redo it all from the beginning was not an option for me. Fortunately Kubuntu has all the features I need right out of the box. There are just a few more quick answers I want to really get going.

(I know some of these have been answered elsewhere but I am extremely low on spare time since I am a post-graduate student. RTFM answers and the like will be completely ignored.)

1. In Gentoo placing scripts to be run onm startup/shutdown were in /etc/conf.d/local.start and /etc/conf.d/local.stop accordingly. Is there such a thing in Kubuntu? I really need this one to place an asfxload command to have midi playback on my SB live!

2. What is the S runlevel? (No offense guys but Gentoo style runlevels are much more intuitive.)

3. Is there any "Global" preferences file like /et/rc.conf that I could tweak?

---

### Post by sharke on 2006-01-17
I think the file your looking for maybe /etc/init.d/boot. misc
Regards
Sharke

---

### Post by ioannis.th on 2006-01-17
that's it, thanks!

---

### Post by firehead on 2006-01-18
[QUOTE=ioannis.th]2. What is the S runlevel? (No offense guys but Gentoo style runlevels are much more intuitive.)
[/QUOTE]
i found this small runlevel explanation in a different thread on this forum, namely [here]("http://ubuntuforums.org/showthread.php?t=89491")
> Throw a littel bit of runlevel knowledge here before we start messing them up.... All the boot processes are executed in sequence as following:
runlevel S: the first runlevel in boot process. /etc/init.d/rcS script will be invoked to start and all the processes underneath /etc/rcS.d will be executed.
runlevel 1: the single user mode. All processes underneath /etc/rc1.d will be executed.
runlevel 2,3,4,5: in debain system, the multi-user env, may not may not include GUI. The same, processes under each of the corresponding dirs will be run. **Note** this is different than RedHat, SuSE, and other RPM based systems.
runlevel 0: computer shutdown.
runlevel 6: computer reboot.

i hope that's what you wanted to know...

---

