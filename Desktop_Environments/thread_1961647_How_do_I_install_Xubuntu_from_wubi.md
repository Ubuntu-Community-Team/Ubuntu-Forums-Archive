---
title: "How do I install Xubuntu from wubi?"
date: 2012-04-19
forum: Desktop Environments
---

### Post by Virtuality314 on 2012-04-19
I found that Ubuntu ran really slowly, so I did some research and found xubuntu, which is supposed to be slightly faster.

So I downloaded an iso image and ran the existing wubi I had to try an install xubuntu.

However, there was no option for installing xubuntu.

So how do I install Xubuntu from wubi?

Specifications:
I am running Windows XP SP3

Virtuality314

---

### Post by bcbc on 2012-04-19
Place same release of wubi.exe with the xubuntu ISO into the same directory. Remove any Ubuntu CD/USB from the computer.

---

### Post by Virtuality314 on 2012-04-21
Thank you, that worked perfectly, all I had to do was delete the ubuntu iso

EDIT:

Wubi keeps on hanging on the Creating Virtual Disks part...I have seen some other forums but none of them help me...What should I do?

---

### Post by bcbc on 2012-04-21
> **Virtuality314 said:**
> Thank you, that worked perfectly, all I had to do was delete the ubuntu iso

EDIT:

Wubi keeps on hanging on the Creating Virtual Disks part...I have seen some other forums but none of them help me...What should I do?

Is that still within Windows? Does the log file give any indication of what's happening?

It's a good idea to run chkdsk and defrag (if required).

---

### Post by Virtuality314 on 2012-04-23
OK, so this is what happened in the end.

I mounted the ubuntu iso onto Virtual Clone Drive. Upon running, I got the option to install from live cd, install from within windows or to find out more about ubuntu. I chose to install from within windows. 

The wubi installer came up and I started the installation process. As usuall, it froze upon creating virtual disks.

Out of curiosity, I restarted my computer and chose the ubuntu option from the os choices menu. It started to complete the installation process (weird, as the installation hadn't actually been done properly) but I quit the installation. Upon doing this, the "Install Ubuntu" option appeared on the screen, as if I had started up a live cd. I clicked on it and the installation completed.

A while later, I did the same thing with Linux Mint (unfortunately had to uninstall ubuntu) and found the installation to be much more helpful. It even allowed me to resize and create partitions.

As a result, I am now on Linux Mint, which I think is slightly better than ubuntu as it has all the functionality of ubuntu plus a more elegant look.

I am sorry Ubuntu, I must leave you...Linux Mint has won me over...We  are going to settle down in Mint land, where the only plants are mints and the animals are known as Polo and Mentos... =D

Virtuality314

EDIT: I forgot to add that wubi actually installs much quicker on a partition with no files on it...It only took me 5 minutes to install Linux Mint instead of the usual 1 hour.

---

### Post by bcbc on 2012-04-23
Wubi is not intended to install on a separate partition (or make new partitions). It uses virtual disks. I'm really not sure what happened to you, but it's not normal. And when you installed linux mint you did a normal install (not comparable to the wubi install).

But it sounds like you've found your happiness in mint land, so...  enjoy

---

### Post by mafsi on 2012-10-27
> **bcbc said:**
> Place same release of wubi.exe with the xubuntu ISO into the same directory. Remove any Ubuntu CD/USB from the computer.

Not working on Win7!

---

### Post by bcbc on 2012-10-28
> **mafsi said:**
> Not working on Win7!

Since 12.10, Xubuntu was removed from Wubi by the request of the Xubuntu project lead. It's no longer possible to install Xubuntu, except with an elaborate workaround.

You can still use Xubuntu with 12.04.1 wubi.exe but that also requires a workaround to install due to a bug: only possible with wubi.exe 12.04.1 and xubuntu desktop iso 12.04.1 in the same folder.

---

