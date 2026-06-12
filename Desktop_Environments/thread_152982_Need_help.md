---
title: "Need help"
date: 2006-03-31
forum: Desktop Environments
---

### Post by Uwais on 2006-03-31
Last night I ve installed Ubuntu on my machine - dual boot with Win xp - using GRUB, sucess...

What I have to do to get the KDE work on my current installation - is there any seperate KDE installations for Ubuntu or I have to get entire Kubuntu?

Please reply

Uwais

---

### Post by dermotti on 2006-03-31
[B]sudo apt-get install kubuntu-desktop
[/B]
I think you can also just do **sudo apt-get install kde-base** also...

---

### Post by aysiu on 2006-03-31
I would advise using aptitude instead of apt-get, for easier removal in case you later decide you don't want KDE on your system any more: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by dermotti on 2006-03-31
Hmm, ive never used aptitude, just apt-get and synaptic.

What does aptitude do that makes it easier to uninstall?

---

### Post by aysiu on 2006-03-31
[QUOTE=dermotti]Hmm, ive never used aptitude, just apt-get and synaptic.

What does aptitude do that makes it easier to uninstall?[/QUOTE] Have you ever tried the command ```
sudo apt-get remove kubuntu-desktop
```? Do you know what it does... or what it *doesn't* do?

See posts #6 and #19 of [this thread](http://www.ubuntuforums.org/showthread.php?t=96048) for more details.

---

