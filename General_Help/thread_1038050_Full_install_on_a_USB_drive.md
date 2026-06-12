---
title: "Full install on a USB drive"
date: 2009-01-12
forum: General Help
---

### Post by Hagablog on 2009-01-12
I have a 16gb thumb drive and I bought it with the intention of putting Ubuntu on it so I don't have to fiddle with my (touch wood) perfectly working MacBook.  I have used the "Create a USB startup disk" creator and although I found it alright, what I really wanted was a full install of Ubuntu as if I installed it on my HD.  

When I go through the Install process I see my internal HD that I DO NOT WANT TO TOUCH but not my thumb drive which is plugged in, functional and mounted.  

I have a USB boot CD from [http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/) so I CAN boot it on my Mac.  Plus, what format will this be.  If possible I would like it as something Windoze can't read.  

Thanks in advance.

---

### Post by Hagablog on 2009-01-12
It would appear I've answered my own question.  What I did was unmounted my thumb drive and then in the installer I made sure that I partitioned the right thing (VIMPORTANT that you don't select the wrong drive. 

ATM it hasn't yet installed but I'll see how I go.  So far so good.

---

### Post by jimv on 2009-01-12
I installed Ubuntu to a 4 gig thumb drive just like a regular HD and it worked fine, albeit a bit slow.

---

### Post by Hagablog on 2009-01-12
Nope didn't work, just wiped my hard drive.  DO NOT TRY WHAT I SAID IN MY LAST REPLY.  It's a good job I have a backup. 

So Im still after any sugestions please.

---

### Post by ubun_two on 2009-01-12
You must have chosen your HDD by accident.

I have not done this, but if I were to try something it, I'd use a regular Intrepid live CD to boot up.  Then insert the empty thumb drive, ummount, and procede with install.  When I get to the partition screen, make sure not to do anything with HDD, and just partition the thumb drive.  The procede with the rest of install.

---

### Post by Hagablog on 2009-01-12
I did all that and I made sure that I selected my thumb drive.  After it, both my HDD and my USB were empty.  Is there any way I can make my HDD unwritable to Ubuntu, without physically disconecting it.  

It said it was installing GRUB, by what I understand it's a bootloader, so to replace the standard Apple bootloader on my Mac (should be on Apple Users I know but my real issue isn't to do with my Mac).  I don't really want this but since I can find no trace of it I think I'm okay.  

@jimv:  How did you do it?  Do you have to make any changes to your computer?

---

### Post by snowpine on 2009-01-12
Sounds like it installed Grub to your hard drive, replacing the Apple boot loader and making the computer unbootable (but all of your data should still be somewhere on the hard drive). Sorry but I am not a mac guy and can't tell you how to fix it.

What I can tell you is this. When you get to the final step (step 7) of the Ubuntu installer, you need to click Advanced Options and choose to install Grub on the USB drive (sdb, for example). Assuming you also chose the correct drive during the partitioning stage, that should keep the installer from touching your internal hard drive. (Unless something is different about  Macs that I'm not aware of.)

---

### Post by WitchCraft on 2009-01-12
I have installed ubuntu on a USB drive and on a pen drive, and both times it worked flawlessly and didn't whipe the internal hd.


Enable the boot from USB option in your BIOS.
change the boot sequence to:
CD first, USB second, HD third

You can boot with the normal ubuntu install cd. NO pendrive special cd or something.

on the guided install, select the appropriate drive.
on one of the next screens:
PUSH THE BUTTON ADVANCED (and tell the installer to install grub on /dev/sdxy) (you can tell the right drive two screens back by their filesize...)

put in any aditional info the installer wants
finish installation and restart

that's all there is to it...

---

### Post by dcstar on 2009-01-14
> **Hagablog said:**
> I have a 16gb thumb drive and I bought it with the intention of putting Ubuntu on it so I don't have to fiddle with my (touch wood) perfectly working MacBook.  I have used the "Create a USB startup disk" creator and although I found it alright, what I really wanted was a full install of Ubuntu as if I installed it on my HD.  

When I go through the Install process I see my internal HD that I DO NOT WANT TO TOUCH but not my thumb drive which is plugged in, functional and mounted.  

I have a USB boot CD from [http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/) so I CAN boot it on my Mac.  Plus, what format will this be.  If possible I would like it as something Windoze can't read.  

Thanks in advance.

You cannot use **the same USB drive** that you are booting from to install Ubuntu on **that USB drive**, you must boot off something else to install onto the USB drive (like a standard Ubuntu Live CD).

---

### Post by Hagablog on 2009-01-14
Thank you, I suspected something like that but had no idea how to fix it.  ATM I am restoring my Mac from a backup and I need it working well for the rest of the month, in febrary however I'll try what said.  

If I was to partition my pen drive (let's say: 4gb Windoze readable, 14gb Linux) is it possible to have them in that order, so Linux boots off the second partition.  I have found that Windoze doesn't read the second partition.  Or if the first is a format Windoze can't read will it skip to the second one.

---

### Post by steve8track on 2009-01-14
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

That claims to work like a live CD for any hardware, only with a persistent partition so it's more truely like a portable OS.

Unfortunately, it didn't work for me when I switched the flashdrive into another computer.  Perhaps I did something wrong.

---

