---
title: "Wine/Steam took all my free disc space"
date: 2006-06-15
forum: Gaming &amp; Leisure
---

### Post by chrism66 on 2006-06-15
Hi all a real newbie question here. I installed wine/steam into my home directory, then I installed Half-Life 2 (don't know where steam downloaded it to). So I tried to run Half-Life 2 and the computer actually froze I could not do anything but hit the reset button. Now when I try to log in I can't as my whole 10GB / directory is full. Any clues on what happen and how to remedy this? Thanks in advance for any help that can be provided.

Chris

---

### Post by NoUse on 2006-06-15
Wine stores things in /home/username/.wine/

I would start the machine in recovery mode via the boot menu.  You'll see a prompt something like "Press esc for boot menu" when the computer starts.  

That will give you a prompt with root access. 
Run:
```

cd /home/username/.wine/
du -ch

```
 to show how much space is being used in that directory.

You can remove whats inside of .wine and you can reinstall steam/halflife after you make sure you have enough space.

---

### Post by eqisow on 2006-06-15
To remove Steam boot into recovery mode as suggested, then do the following:

```
rm -R /home/eqisow/.wine/drive_c/Program\ Files/Steam
```

---

### Post by chrism66 on 2006-06-15
Hi all, Well I did some work and it seems that there was a directory in /media/cdrom0 that was 7GB in size that took up all that was left on my root drive. Deleted it and i am back up an running. Thanks all for your time and help!!

---

### Post by NoUse on 2006-06-15
That will probably break your ability to mount your CD-ROM drive.

I would recreate /media/cdrom0

---

