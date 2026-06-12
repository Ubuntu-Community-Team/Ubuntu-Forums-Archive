---
title: "Whoopsies!"
date: 2005-10-24
forum: Desktop Environments
---

### Post by the_real_lazerman on 2005-10-24
Okay so I am still trying to get my nvidia drivers installed. I have gotten very far from where I have started. I got an error saying that it was using gcc-4.0, while the kernel was compiled with gcc-3.4. So me being the dumbass that I am decides to remove the gcc-4.0 and gcc-4.0 base packages from Kubuntu using Adept. So i commit changes and it effectively uninstalls all my programs I had on Linux, I can't even get into KDE any more, I am missing a .xsession file or something. How do I reinstall the gcc-4.0 and gcc-4.0 base packages?

I have been reading the How To NVIDIA driver install here: 
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

This is the part that messed me up:

```
sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd “directory where you have the nvidia installer”

CC=gcc-3.4

export CC

sudo sh NVIDIA-Linux-x86-1.0-7667-pkg1.run
```

I couldn't get that to work (newb to Linux).

What is the exact command I would enter into Konsol to change cc to gcc-3.4 once I get my gcc-4.0 installed again?

---

### Post by the_real_lazerman on 2005-10-24
Not meaning to be annoying but I really need help!

I tried going into recovery mode and using

sudo apt-get install gcc-4.0 but that didn't work... Please help the newbie :(.

---

### Post by ltmon on 2005-10-25
When you do:

CC=gcc-3.4
export CC

instead do

CC=gcc-4.0
export CC

L.

EDIT:  Ok I'll read your post properly now and give a coherent answer :) ... sorry

Have you tried:

sudo apt-get install kubuntu-desktop

(or reinstalling the kubuntu-desktop package from adept)

?

---

### Post by the_real_lazerman on 2005-10-25
But is that all one command? Like do I type CC=gcc-4.0 (hit enter) then type export CC (hit enter)?

I can't do this until I fix gcc-4.0.

---

