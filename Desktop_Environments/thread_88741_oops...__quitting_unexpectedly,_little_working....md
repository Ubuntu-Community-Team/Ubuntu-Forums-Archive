---
title: "oops...  quitting unexpectedly, little working..."
date: 2005-11-10
forum: Desktop Environments
---

### Post by hunteramor on 2005-11-10
Uhoh.... big problem.

Whenever I log into X, I nearly immediately get errors that gnome-terminal and update-notifier have quit unexpectedly.  Then, nothing seems to be working right.  Gaim, for example, loads up my buddy list before disappearing entirely.  Synaptic and Firefox won't even start at all.  I can't open a terminal, either.

The same problem happens when I boot up in recovery mode.

I think the problem started after I did a hard restart.  I'd just gotten wireless working in Linux today, and it's frustrating to see things fall apart right when I thought I had *everything* working just the way I wanted it to...

I'm in Windows now.  Let me know what information I can provide that would help in resolving this.  I'm downloading the Breezy install .iso just in case.  *Hopefully* it won't be necessary...

---

### Post by Trab on 2005-11-11
so yeah, i dunno how many else would agree with me, but last time i had a major issue that i couldnt just fresh reinstall, doing a
```
 
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
 but that was after reverting it back to hoary, then finally back to breezy...
i dunno, it might work, it might not...
try to get as much info as you can on it... not being able to run terminal is a problem... 
this is why /home should be on a seperate partion... easier to recover :-P

---

### Post by RAOF on 2005-11-11
If you've got a live-cd handy, you could run a filesystem check (using fsck) on your root partition.  It's possible that some part of the filesystem got broken when you hard-reset.

You'd want to boot the live-cd, and then run fsck /dev/whateveryourdriveis (for example, fsck /dev/hda1) without mounting the partition.

---

### Post by hunteramor on 2005-11-11
thanks for the suggestions.

i wound up using root in recovery mode to remove and the install gnome-terminal and update-notifier.  for some reason that fixed most of the problems.  do a lot of applications depend on gnome-terminal  to open up additional windows or something?

weird and scary.

---

