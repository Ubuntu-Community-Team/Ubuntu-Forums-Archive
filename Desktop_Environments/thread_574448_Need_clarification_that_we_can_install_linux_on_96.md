---
title: "Need clarification that we can install linux on 965 mother board"
date: 2007-10-12
forum: Desktop Environments
---

### Post by mandokar on 2007-10-12
Hi,

I am about to purchase a computer with Inter core 2 duo and mother board Intel 965 RY.

However, I have viewed N number of site where people have problem to install linux osftware on their computer.

Can you please reply to this with the supported linux version which can be installed on this computer.

One more, then SATA will be the hard disk.

Mandokar

---

### Post by PmDematagoda on 2007-10-12
The normal Ubuntu 7.04 should work properly on your computer since compatibility depends more on what extra stuff such as VGA cards or wireless cards you have.

So if you could post any wireless, sound or VGA cards you are going to use, we could tell you for sure if your new computer can support Ubuntu/Linux.

---

### Post by mandokar on 2007-10-12
Thanks for Replying so fast.

However, I am new to this Ubuntu and I am not so techie regarding Linux.  I want to learn linux.  

If you can guide me then I can change the parts (motherboard, processore) which support for linux.

However, if there is a new version going to be released from Ubuntu then I will fix to this only.

However, the assembeled pc will be :
e4400 core 2 duo.
965 mother board.
sata 160 gb HDD
20x LG dvd r/w


Thanks

---

### Post by PmDematagoda on 2007-10-12
I don't think you will have to worry about compatibility on your computer, just install Ubuntu 7.04 by downloading the .iso file from:-

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

After the download, burn the .iso at 4X speed to a CD, remember, burn an .iso, not a data disc also do not burn above 4X since the CD might get corrupted.

After you burn the CD, boot the computer using it, you will come to the Live CD menu where you select Run or Install Ubuntu from Live CD and once the Live CD finishes starting up just click on the install icon on the desktop and just follow the instructions to install Ubuntu on your computer:).

---

### Post by kyphi on 2007-10-12
I have been running Ubuntu on an Intel DG965WH board with Intel Core Duo processor for nearly a year.  There were some obstacles for Dapper Drake (6.06) but these have all been overcome.  The main obstacle was the inbuilt PATA controller which refused to 'see' the optical drives.  There were no problems with the SATA drives.  Version 7.04 does not have this handicap.

The changes I have had to make were:

a.  Use a separate sound card (I use nVidia 7900) because there have been problems with the inbuilt sound chip.

b.  Install an ethernet card because the inbuilt ethernet controller chip has not worked for me.

Other than that - full steam ahead.

---

