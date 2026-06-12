---
title: "Children Games with Shockwave"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by Lex Luthor on 2007-06-23
Hello,

   First of all, sorry if this is not the correct place. Please, send it to the correct location if it is wrong.

   My son has some of those child CD activities, that are made on Macromedia Shockwave. We install, and play it, but only on windows.

   I'd like to know if there is something I can to to run it on Linux, Wine, etc... I managed to install it, but when I run Wine gives me some errors, an I cannot run...

   Any clue ?

Thanks....

---

### Post by Matt Yun on 2007-06-24
Unfortunately, Adobe has no Shockwave Linux port.  There are a couple of possible solutions:

1)  Install IE4Linux, a pre-packaged WINE installation for Internet Explorer 6.  See this guide: [Installing IEs4Linux on Ubuntu]("http://www.psychocats.net/ubuntu/ies4linux"); or google for "ie4linux ubuntu".  This is probably the easiest solution, but I am uncertain about Flash/Shockwave compatibility.

2)  Install Windows XP in a virtual machine, through VMWare or VirtualBox.  I use VirtualBox myself, because it is easier to install, and easier to set-up audio, usb-support, host networking, and shared folders.  Here are basic guides for VirtualBox:  [Create and Manage Virtual Machines Using VirtualBox]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html") (with screenshots)

Although the guide is written for Edgy, it's the same method for Feisty.  One important change:  you don't need to download the VirtualBox package to install it; you can use apt-get!

In your /etc/apt/sources.list file, add the following:

**deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free**

Then open a terminal, and enter:

**wget [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) -O- | sudo apt-key add -**

and:

**sudo apt-get update && sudo apt-get install virtualbox**

VirtualBox will be added as new entry in your Applications -> System Tools menu.  Follow the above guide to install Windows XP.  Shockwave should work in the virtual environment, and you can load the CD from the host CDROM drive.

See this guide as well, from the Ubuntu Document Storage Project:  [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by Lex Luthor on 2007-07-25
Thanks, but these type of game does not work under IE, it is stand-alone, we install it and it works without having to open IE, or something similar...

I installed it with WineHQ, but it does not start, it gives me the error attached (in the Shrinker.err file).
With Cedega I cannot even install.

I have VirtualBox installed, but for children with 4 years old it is not a good choice... I'd like something tranparent...

---

### Post by Lex Luthor on 2007-08-04
Well, well, well,

In the hope to not activate the Ruindows Partition, I installer the activity on VirtualBox, but it didn't work either. 

It installed ok, but when I run it, it loads on memory, but after a while it's gone. No sound, no image, Nothing apears.

I don't know what to do....

---

### Post by hikaricore on 2007-08-04
I'm sorry friend, unless someone else come up with an amazing solution that the rest of us don't know of, you may honestly be stuck with this issue.

:/

I do however want to point out if you are just looking for childrens games, there are open source/free games of this variety availible.

Memonix: [http://www.viewizard.com/memonix/index_linux.php](http://www.viewizard.com/memonix/index_linux.php)
Childsplay: [http://childsplay.sourceforge.net/](http://childsplay.sourceforge.net/)
& Gcompris: [http://gcompris.net/-en-](http://gcompris.net/-en-) (i think gcompris is in the ubuntu software repos)

Best of luck,

--Aaron

---

