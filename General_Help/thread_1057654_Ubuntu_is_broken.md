---
title: "Ubuntu is broken?"
date: 2009-02-02
forum: General Help
---

### Post by LeboyX on 2009-02-02
I'm running Ubuntu Intrepid, 32-bit.

Most of this began when I updated to Intrepid from Hardy. I can't understand why, but the GUI will suddenly freeze up for no reason. Sometimes just the mouse will go dead, while during others the entire system will just lock up and I'll have to shut if off by holding down the power key. The freeze-up seems independent of any of my actions, as it's occurred during random processes.

EDIT: I'm using an NVIDIA graphics card (am unsure as to how to tell exactly what...help?), with the "NVIDIA accelerated graphics driver (version 177) [Recommended]". I have Desktop affects turned on only when I'm running the single monitor on my laptop. When I run dual monitors, said affects seem to be automatically disabled.

---

### Post by sanemanmad on 2009-02-02
Well the good news is that you make backups before each kernel update right?

---

### Post by jespdj on 2009-02-02
Random freezes can indicate that there's a hardware problem.

Try
```
dmesg | more
```
to see if there are any error messages (press space to see the next page of messages, press q to quit).

Try running the memory test program (reboot, and in the GRUB menu choose the memory test program). Let it run for a few hours to see if it finds any problem with the memory in your computer.

---

### Post by simion314 on 2009-02-02
> **LeboyX said:**
> I'm running Ubuntu Intrepid, 32-bit.

Most of this began when I updated to Intrepid from Hardy. I can't understand why, but the GUI will suddenly freeze up for no reason. Sometimes just the mouse will go dead, while during others the entire system will just lock up and I'll have to shut if off by holding down the power key. The freeze-up seems independent of any of my actions, as it's occurred during random processes.

Please edit your post and give more details like what video card do you have, if you use the restricted or free driver and if you have
desktop effects turn on. You can read the X11 log file in /var/log/X11.0.log and /var/log/X11.0.log.old(look for errors messages(EE) at the end of the logs)

---

### Post by 3rdalbum on 2009-02-02
Try turning the restricted driver off, if you have one.

I feel your pain - Ubuntu has suddenly become unstable at certain times for me too and I'm still trying to figure out why.

---

### Post by muteXe on 2009-02-02
I always tend to do a fresh install, rather than an upgrade, after a very messy experience trying to get from feisty to gutsy :(  (i think that's what the versions were)

---

### Post by LeboyX on 2009-02-02
@sanemanmad: I've got all my files backed up to an external. If worse comes to worse, my data's safe.

I've taken a look at said files/logs, checking for errors. Despite being swamped with stuff I really don't know about, I couldn't discern any akin to an error/warning. I AM running a proprietary driver for my NVIDIA graphics card (details in my original post)...should I just disable that?

---

