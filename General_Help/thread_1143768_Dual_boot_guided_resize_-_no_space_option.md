---
title: "Dual boot guided resize - no space option"
date: 2009-04-30
forum: General Help
---

### Post by andrewduerden on 2009-04-30
I've just installed ubuntu 9 as a dual boot alongside vista.  During the install I chose the option that suggested the installer would allow me to specify how much space the ubuntu installation is allowed to have.  I followed all the on screen prompts but was never asked any questions as to how much space to allocate to ubuntu.  The install completed and everything was working fine.

Yesterday I went to chck for updates and was told that I didnt have enough disk space to apply them.

Within ubuntu I checked how much disk space was being reported on the "file system" and got told ....

contents 276,214 items totaling 17.5gb (some contents unreadable).  Location  Computer:///.  Volume unknown.  Free space o bytes.

As I'm new to ubuntu and so not really familiar with it yet. I booted into windows and looked at the partitions.  Alongside my existing windows partition there were two extra ones.  One of about 2gb and another of about 200mb.

The actual hard drive is 250gb and is only half full.  Why would ubuntu only reserve 2gb for itself when this is obviously far too little?

I'm considering removing grub and absorbing these two linux partitions back into my main windows partition then re-trying the same install process incase it was just a glitch ... unless there is an easy way to increase the linux partition size by and extra 10gb.

Does anyone know if this is possible?

Thanks

---

### Post by pkmauro on 2009-05-08
I'm having a very similar issue also. 80gb drive, allocated 60gb for Ubuntu, but my file system is 100% full, and I can't load any new apps.

---

### Post by andrewduerden on 2009-05-11
figured this out.  I was expecting to be presented with the option of typing in the amount of space I wanted to use for ubuntu.  Instead, when you get the screen that gives you a graphical representation of the current state of your partition, you can drag the right hand side of the scale and drag to the left to choose how much space to reserve for ubuntu.  If you dont do this, the absolute minimum space is used .... which is enough to install ubuntu but not enough to do anything with.

I just removed ubuntu from my system and restarted the install process.

---

