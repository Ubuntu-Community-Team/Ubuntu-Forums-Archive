---
title: "Um, how can I get the latest updates to fix wifi if I have no internet on wifi OR LAN"
date: 2011-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wintersun72 on 2011-01-14
Hello, I was under the impression that with a bootable USB I would have all the fancy installable proprietary drivers I kept hearing about all over the internet where people smugly told each other how all they did was go to the system admin panel and enable the broadcom drivers etc. 

I've been working on this B130 for 2 days both in terminal and in the software installer with no success. My LAN connection is non functional. When I plug in, I see animation where the wifi signal should be for a second before I am told that I've been disconnected. Every time I try to build a directory or install a set of drivers, headers, or even wl- I mean ANYTHING- I am told that Ubuntu cannot create the directory. 

I'm about to hang it up. I get that I need to install new drivers and I'm TOTALLY willing and capable of unpacking and placing files where they need to go. I retrieved Broadcom's set, I did the blacklist thing, I did all kinds of things yesterday. At the end I can't install the wrapper program or the cutter because of the header issue. I can't install the headers because I can't update on the internet. 

Ergh! Why do so many people say that Ubuntu ships with the 43xx drivers?

As a side note, I love Ubuntu on my acer Aspire notebook and as soon as I find a way to create a floppy disk with SATA drivers I'll be able to install the hard drive on my other tower and get it running over there as well.

---

### Post by fjgaude on 2011-01-15
Maybe you have a permissions issue. You have to be "root" to do most things in Linux, like create directories in etc and other OS areas.

---

### Post by techunit on 2011-01-15
I have had this problem before. First sometimes you need to turn off the computer remove the battery and put it back in before Ethernet starts working. Don't ask me why but on some computers this is the case.

If that doesn't work:
Plop in the Ubuntu Install Disk and go into synaptic package manager:

Click Settings>Repositories

A new dialogue box will open

Now tick Cdrom with Ubuntu 10.xx at the bottom of the window. Close the window and click reload.

No open the Additional Drivers page and try to install the restricted wifi driver. It should work now.

The problem lays with Ubuntu's licencing. They can't prepackage any proprietary drivers in the install, but now they have permission to put them on the disk should someone need them. but they can't have it installed with the operating system. Please don't quote me on this as this may be incorrect.

Good Luck!

---

### Post by wintersun72 on 2011-01-16
it's updating! I took out the battery and plugged it back into the router. Here's hoping something interesting happens with the wifi card. I'm really excited. Now on to the SATA driver issue on the other PC. Got Mythbuntu to run from CD and accept that I have storage, but not recognize a drive letter.

Edit: Thanks so much for the gentle welcome in to the forum!

---

### Post by Butsy on 2011-01-16
When I install Ubuntu, I make sure I'm wired to the internet so the drivers update during the install. Saves me a lot of work later... The only driver I need to update later is NVidia

---

### Post by stanz on 2011-01-16
I'm sooo glad to have the broadcom STA wireless Linux driver...
and also to have hardware drivers offer it!

---

