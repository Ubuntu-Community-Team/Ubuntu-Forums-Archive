---
title: "Reboot into different OS?"
date: 2007-06-22
forum: Desktop Environments
---

### Post by Keshyden on 2007-06-22
I would like to, if possible, set up something similar to the 'reboot into another OS' feature of SUSE 10.2. I am using GNOME currently. If this is possible, I'd really like to set this up.

Thanks.

---

### Post by fumduck on 2007-06-22
like dual booting??

[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

---

### Post by Keshyden on 2007-06-22
Yes, it would be dualbooting. In Suse, there is an option to restart into another operating system that is installed on your system when you log out.

---

### Post by vertigo1980 on 2007-06-22
do you mean like an option to "reboot to windows XP", so that you don't have to manually select the OS in grub?  i'd be interested in that too.

---

### Post by Scheater5 on 2007-06-22
Are you sure you're not just talking about using GRUB?  
What OS's do you have installed on your system right now?  That is, are you asking how to dual boot, or that dual boot isn't working?
If you are wondering how to do it, it's rather easy.  Install Windows first (or shrink your NTFS partition - BACK UP YOUR DATA FIRST) and then create a partition for Ubuntu in the new space (probably ex3) and a swap partition about the size of your RAM.  Then boot up an ubuntu live cd and install.  Select "manually partition when given the option.  Place "/" (your root partion) in the ex3 partition and "swap" in the "linux swap" partion.  
Grub will then automatically recognize that a Windows operating system is installed and place it in GRUB for you to chose from at boot up.

detailed instructions [herel]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html").

---

### Post by PurplePenguin on 2007-06-22
They're asking about a feature that lets you, from within linux (not in grub at bootup) see selections such as:

- Shutdown
- Reboot
- Reboot into Windows

or something quite similar to that.  I have noticed this, I guess when I was using SuSE.  It was pretty cool to be able to select the OS I wanted to boot into, without having to wait for the grub screen to come up.

I don't know if you can somehow add this functionality to Ubuntu... I imagine you can, and it probably just requires editing a config file somewhere... I'd be interested in hearing about this, too.

---

### Post by fiery on 2007-06-23
> **PurplePenguin said:**
>  I have noticed this, I guess when I was using SuSE.  It was pretty cool to be able to select the OS I wanted to boot into, without having to wait for the grub screen to come up.

I don't know if you can somehow add this functionality to Ubuntu... I imagine you can, and it probably just requires editing a config file somewhere... I'd be interested in hearing about this, too.

Not a 100% sure, but I think it's a KDE thing? Not sure as I only used KDE for a short time, a long time ago. So if it's a KDE thing, I guess it must be KDM, the KDE login manager. KDE / Kubuntu users??

---

### Post by compwiz18 on 2007-06-23
Theoretically it would be possible to modify the GRUB config file when you choose a shutdown option... but that seems like a lot of work.

---

### Post by Keshyden on 2007-06-23
I am not talking about setting up GRUB, I mean on an existing system with Windows and Ubuntu already setup.

In SUSE (KDE), there is an option to restart into Windows located in the KDE menu.

This is great when Linux is your default GRUB option. When you are in Linux you can restart into Windows and when you are in Windows, you can restart into Linux - either one without having to pick an option from the GRUB menu (i.e. get up and get a drink, come back to the right OS)

---

### Post by pingpongboss on 2007-06-24
oo i remember this from SUSE too. anyone figure it out?

---

### Post by Nekiruhs on 2007-06-24
If openSUSE did it, there must be a way to do it in Kubuntu. I installed Kickoff, the openSUSE menu, and it showed the option, but said it was unimplemented in the menu. I'd love to see this feature in Kubuntu.

---

### Post by tgm4883 on 2007-07-01
Found this script while googling.  The guy uses KDE, but from the looks of it, it should work with gnome.  I don't have a dual boot system anymore otherwise I would test it.

Credit to [http://robotics.caltech.edu/~klk/linux.html](http://robotics.caltech.edu/~klk/linux.html)

---

