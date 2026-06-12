---
title: "The following packages have been kept back"
date: 2006-06-02
forum: Desktop Environments
---

### Post by baosheng on 2006-06-02
when I use apt-get upgrade to update my system, I got the following information:
[SIZE="1"]
root@silver:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  kubuntu-desktop linux-image-386 linux-image-686 linux-restricted-modules-386 linux-restricted-modules-686 ubuntu-desktop
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.[/SIZE]

What does the "The following packages have been kept back" mean?

---

### Post by meng on 2006-06-02
For me, this meant that in order to install these, some dependent-type packages had to be replaced with newer depndencies. I solved it by going thru Synaptic and selected the "left alone" packages for installation. I guess that in your case, it is possible that "apt-get install kubuntu-desktop {etc}" may also work, if you don't have Synaptic.

---

### Post by johnc4510 on 2006-06-02
I don't run kubuntu, but on ubuntu, this would be what you needed to do:
sudo aptitude update
sudo aptitude dist-upgrade
I'm not saying this will work on kubuntu, understand?

---

### Post by NewWithoutClue on 2006-06-02
I'm not too sure on the whole idea about "kept back packages", but I do know that when you "sudo apt-get dist-upgrade" any and all packages that can be upgraded will be.

Regards,
Paul.

---

### Post by meng on 2006-06-02
[QUOTE=NewWithoutClue]I'm not too sure on the whole idea about "kept back packages", but I do know that when you "sudo apt-get dist-upgrade" any and all packages that can be upgraded will be.[/QUOTE]
Believe me, it can happen that packages get held back, the same thing happened to me after dist-upgrade. It seems some (semi)manual process is required to complete the remaining upgrades.

---

### Post by steveneddy on 2006-06-02
[QUOTE=meng]Believe me, it can happen that packages get held back, the same thing happened to me after dist-upgrade. It seems some (semi)manual process is required to complete the remaining upgrades.[/QUOTE]

Go to the equivilant of Synaptic Package Manager for KDE and upgrade these things individually. Some packages need to be removed before some other libraries get installed. It happenned to me on Ubuntu and I just went to Synaptic and upgraded each by themselves.

Happy computing!

-SE

---

### Post by baosheng on 2006-06-03
commands

[SIZE="1"]sudo aptitude update
sudo aptitude dist-upgrade[/SIZE]

are work.

---

