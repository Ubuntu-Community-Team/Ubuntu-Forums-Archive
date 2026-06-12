---
title: "Simple request - Bound to be Complicated ;-)"
date: 2009-02-12
forum: General Help
---

### Post by 1ronlung on 2009-02-12
I currently have Kubuntu 8.10 installed on a USB drive attached to my PC. When I want to boot Linux, I F12 one time boot menu.. Nice and simple..

Problem is, I'm falling in love with Linux and am seriously considering installing it on my laptop.  I'll do a fresh install of Windows first, so GRUB should take care of itself...

Thing is .. I want to transfer my existing Kubuntu settings and conf/add-ons to my laptop hard disk.  I've been through a strict learning curve with Kubuntu.. Not least getting my fecking broadcom wireless to work .. And , quite frankly, do *not* want to go through it all again ..

I think what I'm requesting shouldn't be difficult, but will remain sceptical until someone versed in these things let me know..

Final question .. 30 gig hard disk.. 10 gigs used by kubuntu .. Realistically, what size swap file will I need?  Currently have 10 gig on my external, but on the internal size is of the essence...

Many Thanks in advance,
ironlung

---

### Post by x33a on 2009-02-12
just copy the /home partition stuff into the fresh installation and all your configurations and addons etc will be available to you.

as for the swap, it isn't related to the hard drive, it depends on the amount of ram you have. 

swap should be twice the capacity of the ram, for best performance. and, if you have large amount of ram, swap will barely be used, but it's required for hibernation.

---

### Post by 1ronlung on 2009-02-12
Thanks for the answer dude.
Am a bit sceptical as it seems too easy.

By just copying the home directory, all additional software I've installed, settings in Opera and ..well... everything will be transferred ?

Thanks,
ironlung

---

### Post by dcstar on 2009-02-12
> **x33a said:**
> 
.......
swap should be twice the capacity of the ram, for best performance. and, if you have large amount of ram, swap will barely be used, but it's required for hibernation.

Statements that "swap should be twice the capacity of the ram" were valid in 1990, now they are only still-repeated myths.

For 99% of users with sufficient RAM, the only size requirement for any Swap now is hibernation and then swap has to be at least as big as physical RAM.

---

### Post by phirestalker on 2009-02-12
copying the home directory over will not get the settings for daemon and root level programs copied, those are in /etc and the extra files are in /var.

If you want to make your laptop work exactly like the system you already have running what you could do is boot up kubuntu on the laptop if it is already installed and copy everything on the external drive right over the laptop files. When you reboot you may end up going through 2 or 3 reboots to get X set up on the new graphics card and things like that as the hardware is different. I have not tried this so cannot say for sure. The only thing I have done was switch from P4 to P4 dual core and both had nvidia, but it booted right the first time.

Main thing is, since hardware is different it might not be that simple, maybe let some people who have braved such things reply, I am just offering some extra knowledge as I know it.

---

### Post by 1ronlung on 2009-02-12
Cheers Dude.

Good news is that USB drive with original OS was set up on the laptop whose internal drive I want to copy to.  Hence, no hardware problems :)

I appreciate x33a's reply, but my gut says there's more to it than copying the home dir.

Can I literally just copy the files files from my USB onto the laptop internal ?  Any problems with hidden files or permissions ?

---

### Post by phirestalker on 2009-02-12
well unlike windows there are no protected files (ie you could delete EVERY file from your system while it is running). so there is no problem there, as for permissions.... I believe that copying the files over all at once since it is retaining the directory structure should also be able to keep permissions. I put faith in this method also because a backup program that I have does nothing but simply back up files and then the restore function lets you restore them to their original location. Since it is the same hardware you would essentially be doing the same thing. However as with any undertaking that requires overwriting.. BACK UP YOUR FILES. that is to say anything that is currently on the laptop that can't simply be reinstalled (docs, pics, vids, etc.) put it on a drive not involved in the process or burn to cd, just in case

on a side note: I had an upgrade process interrupted before on ubuntu and it seems that during ANY part of an upgrade you can do something to get your system back on track. Whereas I was trying to install the newest windows 7 in a vm and it froze on the last part and when I "rebooted" it just kept erroring telling me to start the WHOLE process over again.. UGH. Me and windows we are through. Every day I am amazed with the simplicity of recovering from "disaster" with ubuntu, especially when compared to the windows world.

---

