---
title: "Grub removal- help!"
date: 2008-11-24
forum: Desktop Environments
---

### Post by marcmeier on 2008-11-24
Hi, All

I had Unbuntu 8.10 installed on a laptop to experiment with.

I decided to go back to Win XP, using my laptop's OEM recovery disks, ie I have no XP CD.

Everthing went fine, but, of course, the dreaded GRUB message came up... "GRUB loading stage 1.5"... "Error 17"... freeze up.

From what I can see, I need to fix the MBR.  I've had no luck with this.

As far as I can see, my OEM disks have created one partition, in FAT32.

Any help will be appreciated.

Cheers

---

### Post by Catalyst2Death on 2008-11-24
So, there are instructions here: [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/) for both windows and linux. If you had ubuntu installed, then you have the live-cd (I'm assuming) so you could pop that in and follow the linux instructions.  Otherwise you'll have to get to a windows machine with a floppy/cd burner, and your current machine will also need a floppy (if you go that route)

---

### Post by marcmeier on 2008-11-24
Thanks, Catalyst2Death

I tried that before, but it didn't work... I'll try again...

Cheers

---

### Post by caljohnsmith on 2008-11-24
Please be extremely careful of that tutorial Catalyst2Death linked to; whatever you do, I don't think you want to run the command:
```
dd if=/dev/null of=/dev/sdX bs=512 count=1
```
That erases Grub in the MBR, but it also erases the HDD's partition table, so the HDD will appear unformatted after you run that command. I don't think that is what you want.

If you want to install a Windows MBR from the Live CD, just open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
That assumes your Windows drive is sda, which it will be if Windows is on your internal drive. Give that a shot and let me know how it goes. :)

---

### Post by marcmeier on 2008-11-24
Thanks, caljohnsmith

Right- there's no Win left on the disk.  All I can do is reload Ubuntu 8.10 over the entire disk and carry on from there.

I was already a bit confused by the command syntax in Catalyst2Death's link, as they're "pure" Linux, as opposed to Ubuntu (I'm an old DOS, but not Linux, user).

I'm not sure that I got the commands correct, as the problem still exists.

Right- I'll re-install Ubuntu and move on from there.  First thing will be to remove GRUB (command syntax will be appreciated), then change the disk partition to a DOS format, then try another Win XP install.

Any further help/suggestions will be appreciated.

Regards

---

### Post by marcmeier on 2008-11-24
Oops

---

### Post by caljohnsmith on 2008-11-24
You've got me confused, because in your first post you said that you reinstalled Windows from your OEM CDs, but now you say there is no Win XP any more? You should definitely install Windows first and once Windows boots fine, you can shrink its partition and install Ubuntu. But with OEM CDs, I don't think there is any way you can install Ubuntu first and Windows after that without the OEM CDs wiping away your Ubuntu. My recommendation would be to go ahead and install Windows via your OEM CDs again, and if you still get a Grub error on start up, simply use the commands I gave to install a Windows MBR to your HDD. Let me know how it goes.

---

### Post by marcmeier on 2008-11-24
Sorry about the confusion- perhaps I should have said I ***tried*** to re-install XP.

I cannot install Win first, I get the GRUB problem: all I can do at present is to put Ubuntu back on and (try) to get rid of GRUB before trying to put Win back on.

I hope this clarifies things.

Thanks again

---

### Post by caljohnsmith on 2008-11-24
> **marcmeier said:**
> 
I cannot install Win first, I get the GRUB problem: all I can do at present is to put Ubuntu back on and (try) to get rid of GRUB before trying to put Win back on.

Will the OEM CDs let you install Windows, but once the installation is done and you reboot, you get the Grub error? Or for some reason do the OEM CDs not let you install Windows? I would not recommend putting Ubuntu back on the HDD just to remove Grub; if you boot your Live CD and run the commands I gave in my first post, that will replace Grub in the MBR with a Windows MBR. That should be all you need to do to get rid of Grub.

---

### Post by marcmeier on 2008-11-24
Cal

I can get through all the pre-install Win cr*p with the OEM disks, but, when it reboots to load Win, the GRUB story comes up.

Are you saying run Ubuntu in Demo mode to install the Win MBR?

Yours in undying gratitude (and some newbie confusion)

CD\..

Yee-ha!

Completed what you suggested, rebooted into Win successfully.

Thank you!!!!

---

### Post by caljohnsmith on 2008-11-24
> **marcmeier said:**
> Cal
Are you saying run Ubuntu in Demo mode to install the Win MBR?

Yes, exactly. :) In other words, if the OEM disks successfully install Windows, but the only step they leave out is installing a Windows MBR, then just do the commands I previously gave and that will install a Windows MBR for you. How about giving it a shot and let me know how it goes.

---

### Post by marcmeier on 2008-11-24
Cal

Many, many thanks- refer edited post above.

Regards

---

### Post by caljohnsmith on 2008-11-24
That's great news it worked. But before you dive into installing Ubuntu, you might want to check out this tutorial first:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

It does a good job of leading you step-by-step through the process with lots of great screen shots. Anyway, let me know how your Ubuntu installation goes or if you run into difficulties. :)

---

