---
title: "[SOLVED] OS Dell &amp;amp; DRM"
date: 2007-08-16
forum: Dell  Ubuntu Support
---

### Post by erlenmeyer316 on 2007-08-16
I work for a small company and talked them into going out on a limb and purchasing a Dell Ubuntu PC XPS 410. They are a windows only shop and it was a tough sell, but they finally agree. Unfortunatly my luck ran out there. They were not happy (afraid) and asked me to install windows onto the PC. 

So I started the process and found out very quickly that there seems to be some sort of DRMish software mechanism that Dell has install to preven the installation of windows. Now I know the reason for this, but we have an MSDN liscense and have legitimate copies of windows. Everytime I start an install it craps out during the hardware scan and says that it can't find the harddrive. 

I called Dell support and asked some questions about this and they seemed to imply that they do have some sort of software that prevents a windows install. I'm in the process of trying to get around it, but I found this to very disheartening.

You think that buying a PC means that you can install any OS you want, but that's not the case at all. It's very Microsoft like and very disappointing.

---

### Post by aldenhg on 2007-08-16
I somehow doubt that Dell would do something like that. First of all, Ubuntu is open-source, so having a PC locked to it only is more than a little counter intuitive. Second of all, I would guess that there's a problem with the Windows installation process. If you gave us specific error messages we might be able to help you through it. Believe it or not, a lot of us still use Windows and I have to install it on a nearly daily basis. Unless you can quote the DRM thing, I'd recommend just telling us what goes wrong when and we can help you through it.

---

### Post by heimo on 2007-08-16
> **erlenmeyer316 said:**
> I work for a small company and talked them into going out on a limb and purchasing a Dell Ubuntu PC XPS 410. They are a windows only shop and it was a tough sell, but they finally agree. Unfortunatly my luck ran out there. They were not happy (afraid) and asked me to install windows onto the PC. 

So I started the process and found out very quickly that there seems to be some sort of DRMish software mechanism that Dell has install to preven the installation of windows. Now I know the reason for this, but we have an MSDN liscense and have legitimate copies of windows. Everytime I start an install it craps out during the hardware scan and says that it can't find the harddrive. 

I called Dell support and asked some questions about this and they seemed to imply that they do have some sort of software that prevents a windows install. I'm in the process of trying to get around it, but I found this to very disheartening.

You think that buying a PC means that you can install any OS you want, but that's not the case at all. It's very Microsoft like and very disappointing.

I seriously doubt your words and think you're wrong. Before spreading such a strong accussations, you should get much stronger facts. Sounds a lot like FUD now.

---

### Post by Arthur Archnix on 2007-08-16
Yeah, go into the bios and set the sata drive to compatibility mode. If it's XP professional that should let install detect the hard disk.

---

### Post by mike999999 on 2007-08-17
> **erlenmeyer316 said:**
> I work for a small company and talked them into going out on a limb and purchasing a Dell Ubuntu PC XPS 410. They are a windows only shop and it was a tough sell, but they finally agree. Unfortunatly my luck ran out there. They were not happy (afraid) and asked me to install windows onto the PC. 

So I started the process and found out very quickly that there seems to be some sort of DRMish software mechanism that Dell has install to preven the installation of windows. Now I know the reason for this, but we have an MSDN liscense and have legitimate copies of windows. Everytime I start an install it craps out during the hardware scan and says that it can't find the harddrive. 

I called Dell support and asked some questions about this and they seemed to imply that they do have some sort of software that prevents a windows install. I'm in the process of trying to get around it, but I found this to very disheartening.

You think that buying a PC means that you can install any OS you want, but that's not the case at all. It's very Microsoft like and very disappointing.

There is no drm installed with Ubuntu. 

You're installing windows wrong.  ;-)

The specs for the 410 say it has sata drives, you will need to either use a floppy to load sata drivers (f6 during setup) or slipstream your drivers onto your Winxp disk. 

Good luck.

---

### Post by jacob01 on 2007-08-17
most likely it is the file system because dell uses the same bios in all of their dells

a reason why it woun't recognize the hard drive it because ubuntu uses the linux ext3 file system so it windows wont recognize the hardrive

so to fix it try to format the drive with fat or somthing maybe make a linux cd of        pc linux os then run the installer or the partitioner on the pclinux live cd and format the drive with   fat   file system so that windows can see the drive (windows cant read the linux file system ext3) 

and if that didnt work there must it must be a something in the bios (i doubt dell did that because they use the same motherboard on their linux desktops as they do their windows desktop) but if there is a program preventing you from installing the os, your only other real option is to either get a new motherboard or try to flash that one

---

### Post by jacob01 on 2007-08-17
did you get windows installed?

let us know when you do

---

