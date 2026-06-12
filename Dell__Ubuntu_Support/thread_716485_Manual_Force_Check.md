---
title: "Manual Force Check?"
date: 2008-03-06
forum: Dell  Ubuntu Support
---

### Post by Humanities Major on 2008-03-06
I have a pretty new Inspiron 1420 running on Gutsy Gibbon and today when I went to turn it on it started a force check, which is fine it's done that before, but after 42% it freezes then says the check has failed.  Specifically it says:
os_part:UNEXPECTED INCONSISTENCEY; RUN fsck MANUALLY.
             (i.e., without -a or-p options)
fsck died with exit status 4

*An automatic file system check (fsck) of the root file system failed. a manual fsck must be preformed, then the system restarted.  The fsck should be performed in maintenance mode with the root file system mounted in read-only mode.
*The root filesystem is currently mounted in read only mode.  A maintenance shell will now be started.  After performing system maintenance press CONTROL_D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found [that one's my favorite]
bash: The: command not found
bash: dircolors: command not found



So how do I do that.  I tried punching in the obvious command fsck, which does nothing.  Am I just screwed and need to make dell send me a new laptop?  I can't get beyond this screen so from here all I can do is turn it off.

To anyone who can help:  Thank you so, so much I am trying to be less than completely useless on this thing, mostly because a good part of my life and livelihood is on my laptop, and sorry this was such a long post I just figure it always helps to be precise.

---

### Post by natehall on 2008-03-06
Have you tried booting up from a live cd? If nothing else you can then save any data you want and then do a fresh install with the [DELL dvd]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").

---

### Post by jimv on 2008-03-06
This has happened to me.

Boot from an Ubuntu cd, any Ubuntu cd.  Open a terminal and

sudo fsck -py hda1

(hda1 can be replaced by whatever your partition is)
Make sure that your drive is not mounted (sudo umount /dev/hda1)

---

