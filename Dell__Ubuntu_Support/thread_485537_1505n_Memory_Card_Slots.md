---
title: "1505n Memory Card Slots"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by mojorising on 2007-06-27
I have a Dell 1505n, which came with Ubuntu pre-installed and deleted the OS to put Kubuntu on it.

For some reason, I can not read any memory cards in the built in card reader. I have tried SD and Memory Stick Pro Duo (with an adapter). 

It appears the reader drivers seem to be installed and functioning OK.

Some output of lspci:
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

Has anyone with this laptop had similar problems? Any ideas on what I can I try to get this working?

Thanks in advance,

Mike

---

### Post by rivasdiaz on 2007-06-27
In ubuntu (gnome) the card reader works as expected for SD cards (Memory Sticks are not supoprted yet). This support is part of the kernel so Kubuntu shuld work ok too. Check if your SD card is fine.

---

### Post by jppaynesr on 2007-07-22
My experience is that a Sandisk SD card from a Nikon Coolpix works properly, however the Fujifilm XD Picture card from my Fuji camera does NOT work.

Any ideas about the XD card?

---

### Post by thecure on 2007-07-22
> **mojorising said:**
> I have a Dell 1505n, which came with Ubuntu pre-installed and deleted the OS to put Kubuntu on it.

Mike

FYI: Not sure on your hardware issue but next time just install the Kubuntu desktop with aptitude; then you can choose either desktop to run and you retain all your installed programs, drivers and files. (You can install the Ubuntu, Xubuntu and/or Enlightenment(E17)) on your Kubuntu instaltion and run which ever you feel like at the time.

---

### Post by mojorising on 2007-07-23
Thanks for the tip, thecure. While that works for some people, I actually prefer to reinstall this way so I don't have a bunch of programs loaded on my machine that I don't want (I use very few Gnome apps -- Firefox & Gimp, that's all) and I don't put unnecessary load on the apt servers by downloading and updating them. 

Hopefully support for the other popular memory formats goes into the kernel some time soon so there are even fewer excuses for people to run that other OS.  ;)

Mike

---

### Post by thecure on 2007-08-07
> **mojorising said:**
> Thanks for the tip, thecure. While that works for some people, I actually prefer to reinstall this way so I don't have a bunch of programs loaded on my machine that I don't want (I use very few Gnome apps -- Firefox & Gimp, that's all) and I don't put unnecessary load on the apt servers by downloading and updating them. 
Mike
Ubuntu/Kubuntu already has all the base files for running KDE/Gnome apps and so the actual gnome desktop isn't very large. Which ever is not your default desktop doesn't run until you start KDM or GDM respectively. Good to see you care about the load on the apt servers but you could always choose not to update those files that you are concerned about. Of course if you have a very old HD then I guess a couple of megs might make a difference. With a couple of my Feisty installs on 2 Gig USB pen drives that each have KDE, Gnome and Enlightenment on them and so it would seem you really cant be saving much space. (I wish I could get persistent mode to work I have to install them from my own drive.)If you love tweaking your desktop and RAM and slow processor is a big concern than I suggest E17 as your desktop. Very fast and has both KDE and Gnome elements also to run those programs.What turned me on to Ubuntu in the first place was that on my Dell Inspiron 6000 recognized everything; card slots, wireless, Bluetooth, media buttons and MAC keyboard;then Inspiron E1705; XPS 410N- added larger HD with 64bit Ubuntu;Gateway 450ROG;Compaq 5690;SonyRZ32G(except video)-all these computers media cards work out of box; with windows had major headaches with drivers for pretty much every device - yes I liked blowing my HD's and reinstalling when I got too much clutter; linux much faster and stable. If you really want a fast and lean distro to play with, buy a cheap USB stick and put Puppy Linux on it.

---

### Post by mythicalbyrd on 2007-08-29
The only time I tried an SD card in my 1505n was when my friend wanted to use my laptop to upload pictures from her camera onto facebook.  At first I thought something was wrong because it wasn't reading the card, but then I realized you need to push it in until it clicked (crazy modern technology).

You probably already knew that, but it might help someone.:guitar:

---

### Post by AKoine on 2007-12-14
> **mythicalbyrd said:**
> At first I thought something was wrong because it wasn't reading the card, but then I realized you need to push it in until it clicked (crazy modern technology).

You probably already knew that, but it might help someone.:guitar:

It did !! Thanks a lot mythicalbyrd ! :-)

---

