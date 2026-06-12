---
title: "Request for aid for the linux newbie"
date: 2009-04-19
forum: General Help
---

### Post by rsadambrown on 2009-04-19
Hello all,

I hope I've come to the right place. First off apologies if this questions is simple or already answered elsewhere. I did a thorough search using any keyword I could think of and didn't see it, so here's hoping I'm not sounding like a total idiot...

I currently have in possession a friend's laptop that has Ubuntu installed on it, however has a problem. It will not load the Operating system at all. Anytime I try and turn it on it starts off with the GRUB Loading 1.5 and goes to the ubuntu title screen, continues to load, then cuts back to the black&white dos looking screen with the following message:

kinit: No resume image, doing normal boot...
[   57.393475] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   57.393475] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 


And then it repeats that message over and over.

Now, I went to said website, and looked around, but I have no idea how to get the file there from the webiste onto the labtop, as it does not have wireless internet access, and cannot even get to a operating system to access the cd or floppy drive?

I'm trying to install windows xp onto the labtop from an install disc I have, and after moving the cd drive to the top of the boot list in bios settings, it still bypasses the d drive and goes straight into trying to load ubuntu.

Also, I've interuppted the load screen trying to load the backup versions, and all of them display the same message.

I am wondering is there a simple command I can use to boot from cd, or format the c drive? I'm linux-stupid - and my friend is even less literate. From reading the guides and faqs on this and other sites, I cannot find anyone who has this same problem where no operating version will load at all. I'm just trying to make the labtop functional again!

Any help will be most appreciated, thank you.

---

### Post by DGortze380 on 2009-04-19
> **rsadambrown said:**
> Hello all,

I hope I've come to the right place. First off apologies if this questions is simple or already answered elsewhere. I did a thorough search using any keyword I could think of and didn't see it, so here's hoping I'm not sounding like a total idiot...

I currently have in possession a friend's laptop that has Ubuntu installed on it, however has a problem. It will not load the Operating system at all. Anytime I try and turn it on it starts off with the GRUB Loading 1.5 and goes to the ubuntu title screen, continues to load, then cuts back to the black&white dos looking screen with the following message:

kinit: No resume image, doing normal boot...
[   57.393475] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   57.393475] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 


And then it repeats that message over and over.

Now, I went to said website, and looked around, but I have no idea how to get the file there from the webiste onto the labtop, as it does not have wireless internet access, and cannot even get to a operating system to access the cd or floppy drive?

I'm trying to install windows xp onto the labtop from an install disc I have, and after moving the cd drive to the top of the boot list in bios settings, it still bypasses the d drive and goes straight into trying to load ubuntu.

Also, I've interuppted the load screen trying to load the backup versions, and all of them display the same message.

I am wondering is there a simple command I can use to boot from cd, or format the c drive? I'm linux-stupid - and my friend is even less literate. From reading the guides and faqs on this and other sites, I cannot find anyone who has this same problem where no operating version will load at all. I'm just trying to make the labtop functional again!

Any help will be most appreciated, thank you.


Please verify your BIOS settings. There will be a function key you need to press at Boot time to enter the BIOS. Move your CD Drive to boot first.

Try one of two things.
Attempt to boot the recovery kernel from the GRUB menu
or
Download and boot the Ubuntu LiveCD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

We can move on from there after you get the system to boot to a usable OS

---

### Post by rsadambrown on 2009-04-19
> **DGortze380 said:**
> Please verify your BIOS settings. There will be a function key you need to press at Boot time to enter the BIOS. Move your CD Drive to boot first.

Try one of two things.
Attempt to boot the recovery kernel from the GRUB menu
or
Download and boot the Ubuntu LiveCD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

We can move on from there after you get the system to boot to a usable OS

I've tried both of those things. I entered BIOS and reordered my cd drive to the top, however it still ignores the cd in there.

Secondly, I've tried every single recovery kernel from the GRUB menu. All the different versions and their corresponding recovery versions. 

I'm downloading now and will update with the results as soon as I give it a whirl -- appreciate the feedback sofar!

---

### Post by DGortze380 on 2009-04-19
> **rsadambrown said:**
> I've tried both of those things. I entered BIOS and reordered my cd drive to the top, however it still ignores the cd in there.

Secondly, I've tried every single recovery kernel from the GRUB menu. All the different versions and their corresponding recovery versions. 

I'm downloading now and will update with the results as soon as I give it a whirl -- appreciate the feedback sofar!

If the BIOS settings are correct, and the CD is not corrupt, and the CD Drive is functioning properly, there is no reason for it to not boot a CD.

I know that is not much help, but it at least lets you know not to waste any time looking for some mysterious Linux reason for it not booting a CD... one doesn't exist.

---

### Post by codeseer on 2009-04-19
If you can disable all of the boot items, except the CD drive, try that.

---

### Post by Torgas Prim on 2009-04-19
Sounds like a Dell and the wireless daughter card freaked.
Go to the support site and it will tell you how to find the wireless card and unplug it.
I bet it boots fine after that.

---

### Post by rsadambrown on 2009-04-19
Well it has a external wireless card, so I just pulled that out of the slot. 

Now it wont even boot up at all haha.

I'm burning the ubuntu iso into a blank cd right now...

---

### Post by Torgas Prim on 2009-04-22
Ouch sorry.
Then it is your modem card.
Both can cause the same issue

---

