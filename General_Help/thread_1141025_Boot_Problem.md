---
title: "Boot Problem"
date: 2009-04-28
forum: General Help
---

### Post by bturgan on 2009-04-28
Hi,

I have recently installed Ubuntu 8.04 on my Acer Aspire One, 8GB Model.

But than I have realized that this operating system is not built for netbooks. Cant see all of the screen on most of the apps. Its out of the screen.

So I have decided to install Netbook Remix on it. I have downloaded the necessary image file and Disk Imager software. I have tried to write the image file to my HP 4GB memory stick, but when I click write, it gave me an error "An error occured when attempting to write data from handle. Error 8:"

So than maybe Ubuntu 9.04 will fix my current problem. After downloading and copied the installed files to cd, I have tried to boot from CD.

But, I only see 2 boot options right now after installing Ubuntu 8.04. 

Boot Option Menu
1. IDE 0: SSDPAMM0008G1
2. Network Boot: LEGACY PCI DEVICE

Can anyone help me how to boot again from CD please?

Also I checked BIOS and,

1st Boot Priority is USB CD Rom

Thanks,

Berke

---

### Post by dandnsmith on 2009-04-28
I wouldn't have changed the boot order (if you did),
but used the F12 key on boot to change boot device, select the CD device on USB, and hit return

If that doesn't boot, then it isn't managing to recognise the actual CD as having a bootable content (try it with one that is known to work)

BTW - Mint5 has the equivalent to Ubuntu 8.04, and is much more configured to the AA1 netbook (in my experience)

---

### Post by bturgan on 2009-04-28
Thanks for your reply,

Actually I have changed the boot order. Do you think this is happening because of that?

I am inserting Acer's boot cd also too boot drive but it does not seem to work also.

The problem here, is  I cant see USB Cd drive in the boot options. 

Thanks again,

---

### Post by bturgan on 2009-04-28
I also can not find the cd rom option at Ubuntu. 

I check Places/Home Folder but can not browse the files of cd. Cant I update Ubuntu 9.04 from 8.10 from Ubuntu Operating system?

Thanks,

---

### Post by theozzlives on 2009-04-28
I don't know much about the AA1, but I've read in here that 9.04 works great on it.

---

### Post by dandnsmith on 2009-04-29
> **bturgan said:**
> 
Actually I have changed the boot order. Do you think this is happening because of that?
I am inserting Acer's boot cd also too boot drive but it does not seem to work also.
The problem here, is  I cant see USB Cd drive in the boot options. 

First thing is to try that drive with another PC - it's possible that either the Acer isn't working properly, or that CD device isn't.
Also try another CD device with the Acer.

Until you've worked out where the problem is, it isn't worth worrying about other details.

Have you tried the Acer with a USB stick plugged in to see if it offers the boot option with that? Mine will offer the option for booting, even on a stick which has not been configured for booting.

The OS upgrade in place - I've seen the comment in another thread that it is complicated because of the number of packages which have changed, and the dependencies (I wouldn't try it).

---

### Post by Silvr2008 on 2009-04-29
Have you booted off that USB drive before? I have an older notebook that is not capable of booting off the USB and so it does not show the drive in the boot option when you hit F12.

---

### Post by bturgan on 2009-04-29
Actually cd drive is working, I have tried with other computers, and also I have installed Ubuntu to my Acer with this cd drive.

It was offering boot option from USB Drive before, but after installing Ubuntu, it is not offering anymore.

Actually I gave it to Acer Service now, since its under warranty since I couldnt solve the problem.

Thanks a lot for all the help,

Berke

---

### Post by arab on 2009-04-29
i am having the same even after i received an update for the Ubuntu ImageWriter few minutes back hoping it would solve the issue....but the BOOT ERROR continues.

I hope there is a way to solve it.

MIni PC Model: HTC Shift 9500
OS onstalled: Ubuntu 8.10
Ubuntu Remix: Still waiting for solution soon.

---

