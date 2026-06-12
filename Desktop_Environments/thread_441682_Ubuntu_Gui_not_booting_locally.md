---
title: "Ubuntu Gui not booting locally????"
date: 2007-05-12
forum: Desktop Environments
---

### Post by Linux_cat on 2007-05-12
Hi I got some help installing an nvidia driver for my ubuntu server installtion, following that i have installed ubuntu-desktop and kde, thing is when the machin boots now i get a blank black screen after it goes through the boot process...however

I can ssh into the machine and ssh -X in as well and run graphical applications including kde, why is it not booting straight to the gui??

can anyone help?

---

### Post by happyhamster on 2007-05-12
If you installed ubuntu-desktop (instead of kubuntu-desktop) then gnome should also be installed. So perhaps gdm and kdm are competing for glory during bootup, and the resulting bloody carnage is censored with a black screen. Or something like that :)

So my guess is to try kde/kubuntu-desktop or gnome/ubuntu-desktop.

---

### Post by Linux_cat on 2007-05-13
hi thanks for the reply, when u say try kde/kubuntu desktop of gde/ubuntu desktop, how would i try these??, what command would i issue, and remember I cant even get a command line locallly i have to ssh in.

Is there a key combination that will exit me into command line on my local machine so i can issue starkde or something?

---

### Post by Linux_cat on 2007-05-13
ok, so this is what i have done....

I went into the xorg.conf and entered my BusID to PCI:1:0:0 and then ran

sudo dpkg-reconfigure kdm

I made gdm my default manager and restarted my server.

when i booted it up it gave me the message that xserver could not be displayed properly and got a command line.

I reissued the dpkg-reconfigure kdm command and switched it back to kdm and then 

startx

instead of getting a blank screen i get a ubuntu organge logo with an empty progress bar???, i still can log in using ssh and forward graphics via ssh -X, 

I really want to get a proper desktop on this thing can anyone help?

---

### Post by Linux_cat on 2007-05-16
Anyone help me??

---

