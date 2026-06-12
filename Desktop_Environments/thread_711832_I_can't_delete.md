---
title: "I can't delete"
date: 2008-03-01
forum: Desktop Environments
---

### Post by srkelley on 2008-03-01
I can't delete or save any files, the hdd is full. I'm running Xubuntu 7.10. I was installing packages from the add/remove packages page/tool. It kept downloading them until they filled the disk space to the brim. I never checked to see if there was enough room, but I can't even delete a 4kb file to gain room. The only reason I didn't have the room I thought I had was that I never deleted my xubuntu iso from the desktop. Is there any command to absolutely delete something with having it moved to trash?

And I got this error earlier: Anyway to fix that after fixing the above error or are they related?

Could not look up internet address for shirondale-desktop.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
shirondale-desktop to the file /etc/hosts on your system.

---

### Post by tubasoldier on 2008-03-01
try cleaning the apt-get cache to get more room:

```
sudo apt-get clean
```

That should at least get you on the right track.

---

### Post by srkelley on 2008-03-01
Thanks a lot. Right after I copied the line and opened the terminal it logged me out. Then it wouldn't even let me enter the terminal in fail safe mode. i restarted the pc, loged in normally and tried the terminal, but it failed again. I went for a safe og-in via the terminal and it worked, i typed the line sudo apt-get clean and it let me back on. I completely erased the iso along with some vids I no longer watch.

What does that line do? I just assumed (wrong, I might add) that it erased all programs or or all programs being prepped to install. I checked the pc and I havn't noticed anythingmissing so I'm guessing it's something close to the latter.

Once again, thanks a lot.

---

### Post by Jussi01 on 2008-03-01
SImply that line just deletes the all packages (install files)you have ever downloaded that were stored on your system. so all of your programs are still there, just the install files are gone :)

---

### Post by srkelley on 2008-03-28
Okay, I thank you a lot for your help before, but I can't install any new programs now and I don't know the commands for getting it back. I'v been searching, but everything still looks foreign to me and my book on ubuntu hasn't come yet. Ya, I'm still a noob.

---

