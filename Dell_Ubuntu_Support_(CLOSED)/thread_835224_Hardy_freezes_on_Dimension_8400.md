---
title: "Hardy freezes on Dimension 8400"
date: 2008-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by beefyco on 2008-06-20
I'm new to Ubuntu. I had this problem with the last release of ubuntu on my computer, so I uninstalled and gave up for a while. However, with 8.04, I thought I'd give it another shot. Same problem. I have a dual-boot set up with XP home as my other OS. When using, all of the sudden (it does it no matter what I'm doing seemingly out of nowhere) it just freezes. My mouse still moves, but clicks, keyboard commands, nothing does anything. I'm not sure if it's a dell compatibility issue or what the heck it is, but man it's annoying. Also, I didn't get a chance to try it yet, but with the last release, my suspend never came back from suspend ever. Not sure if those are related, though I doubt it. I really want to make the switch from Windows, but it keeps calling me back with this stupid error in Ubuntu. anybody else having this problem or is it just me? Or does anybody have any ideas? it's a fresh install, all I did was start to download the updates that automatically start with a fresh install. Is there maybe a package that's downloading that's making it freak out? Anyway, that's all. Please help me successfully make the jump!

---

### Post by Luobo on 2009-01-12
I'm in exactly the same boat, except I'm not trying to dual boot.  I've clean installed Ubuntu and Kubuntu on my Dell Dimension 8400.  After a while, usually when exiting some app, the desktop "freezes":  The mouse cursor still moves, but keyboard and mouse presses don't do anything.  I've not been able to do anything but power off the computer.  

Please save me from Windows.

---

### Post by shamael on 2009-01-22
Same problem here! I am an ubuntu user since 5.10 and I just switched to this dell dimension 8400 with a fresh install (8.10 though): I had never seen such a thing!
The only thing that moves is the cursor, I can't even kill X or switch to another terminal. I have a dmesg screenlet open, hopefully I'll see some meaningful error next time it happens. This is an awful issue!

On a sidenote, suspend and hibernate seem to work for me. They didn't on my previous pc (athlonXP).

---

### Post by shamael on 2009-01-22
Ok, I think it is related to samba/cifs, in fact I can replicate the lockup by mounting and unmounting a samba share from the terminal (X seems to have nothing to do with this issue).
Also, take a look at [this]("http://ubuntuforums.org/showthread.php?t=1001876") thread.
Can any of you confirm that the same happens on your 8400s?

---

