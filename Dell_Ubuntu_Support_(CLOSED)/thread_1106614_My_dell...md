---
title: "My dell.."
date: 2009-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fellixombc on 2009-03-25
Well, I haven't installed Ubuntu yet, but my dell machine needs a driver to run the internet. I can easily just get it off of a usb but, its an EXE file. 

So i was thinking, I just need wine. But HOW DO I GET WINE...If i have no internet?

---

### Post by Arndtwe on 2009-03-25
Have you tired running Ubuntu live CD? It might surprise you and already have the necessary driver to work. :-) Try live CD and report back!

---

### Post by fellixombc on 2009-03-25
> **Arndtwe said:**
> Have you tired running Ubuntu live CD? It might surprise you and already have the necessary driver to work. :-) Try live CD and report back!

Live cd? ill try finding that, but, in the mean time, I shall get ready for my swtich, upload all my important files to a site...etc,.

but, is there a way to download wine to a xp computer?

---

### Post by Arndtwe on 2009-03-25
Live CD is just running Ubuntu from a CD without actually installing it. This way, you can test it out and see if you like it, and also see if everything works... In your case your internet. 

Side note: How do you connect to the internet?

---

### Post by balloooza on 2009-03-25
Dell sells ubuntu laptops, so they SHOULD (don't quote me) have good wireless driver support

I CANT WAIT FOR JAUNTY BETA!!!(WOTP)

---

### Post by fellixombc on 2009-03-25
> **Arndtwe said:**
> Live CD is just running Ubuntu from a CD without actually installing it. This way, you can test it out and see if you like it, and also see if everything works... In your case your internet. 

Side note: How do you connect to the internet?

Ethernet port, MagJak. I need the driver, [http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=WRK_PNT_P4_360&os=WW1&osl=en&catid=&impid=]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=WRK_PNT_P4_360&os=WW1&osl=en&catid=&impid=")
the last one, but, how do i view it with the live cd? Do i just boot from cd?

---

### Post by balloooza on 2009-03-25
Wait, is this a laptop or a desktop.

2) is this a wireless card, a STANDARD ethernet nic, or some convulted dell contraption (usb ethernet, internet from a bluetooth, etc.)

---

### Post by Arndtwe on 2009-03-25
Yes, You need Ubuntu installed on a CD then you just boot the computer from the CD.

---

### Post by fellixombc on 2009-03-25
> **balloooza said:**
> Wait, is this a laptop or a desktop.

2) is this a wireless card, a STANDARD ethernet nic, or some convulted dell contraption (usb ethernet, internet from a bluetooth, etc.)

Desktop, ethernet cord...it sticks into the back of your computer, a ethernet jack...

---

### Post by anjilslaire on 2009-03-25
> **fellixombc said:**
> Ethernet port, MagJak. I need the driver, [http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=WRK_PNT_P4_360&os=WW1&osl=en&catid=&impid=]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=WRK_PNT_P4_360&os=WW1&osl=en&catid=&impid=")
the last one, but, how do i view it with the live cd? Do i just boot from cd?

Gigabit ethernet in a desktop? I can almost guarantee you won't need any special drivers. It'll work out of the box.

---

### Post by fellixombc on 2009-03-25
> **anjilslaire said:**
> Gigabit ethernet in a desktop? I can almost guarantee you won't need any special drivers. It'll work out of the box.

yes, a gigabit ethernet... when i re-install windows xp, e.g, format my computer, I need too.

---

### Post by anjilslaire on 2009-03-25
Thats the difference. MOre than likely, the network card will work automatically with the linux kernel. I've never personally seen a wired NIC not work automatically on a modern linux installation

---

### Post by mihai.ile on 2009-03-26
Just insert an Ubuntu Live CD, make sure it's picked up by the boot process and just pick Try Live without installing. Ubuntu will start from CD and detect and configure all hardware. Internet should work right away without any driver to download/install.

Just try, you have nothing to loose (by running it from the Live CD without actually installing).

EDIT: don't forget to post back here the results :)

---

### Post by fellixombc on 2009-03-26
> **mihai007 said:**
> Just insert an Ubuntu Live CD, make sure it's picked up by the boot process and just pick Try Live without installing. Ubuntu will start from CD and detect and configure all hardware. Internet should work right away without any driver to download/install.

Just try, you have nothing to loose (by running it from the Live CD without actually installing).

EDIT: don't forget to post back here the results :)

I got a burning error :(

---

### Post by issih on 2009-03-26
That happens sometimes...just means that you were unlucky with that platter, try again with another disc and perhaps reduce the burn rate.

---

### Post by fellixombc on 2009-03-26
> **issih said:**
> That happens sometimes...just means that you were unlucky with that platter, try again with another disc and perhaps reduce the burn rate.

I got it to work :) AND I LOVE LINUX :)

[[IMG]http://i214.photobucket.com/albums/cc112/fellixombc/th_screenshot.png[/IMG]](http://s214.photobucket.com/albums/cc112/fellixombc/?action=view&current=screenshot.png)

---

### Post by armandh on 2009-03-27
welcome to the greatest thing to happen to PCs since the 486

as you can see this forum is the instruction book for the latest on ubuntu.

now get all your files you wish to save on cd and then click install.

ubuntu comes with open office you only need to install flash
[first time you visit Utube you will get directed to the right place]
and you need to install the necessary codex for dvd/cd listning / viewing
[www.medibuntu.org](www.medibuntu.org) has it all

---

### Post by gbrainin on 2009-03-27
Personally, I prefer installing the "ubuntu-restricted-extras" package to installing anything from a website.  The package includes flash, java, and other similar items that are popular, but not free (in the licensing sense).

The advantage of installing through a package is that it is better integrated into the operating system, and you get automatic updates of the package along with the rest of your system.

To install: go to Sytem->Administration->Synaptic Package Manager, search for ubuntu-restricted-extras, and mark it for installation.  If it's not there, you probably don't have the universe and multiverse sources marked; you can fix that in System->Administration->Software Sources.

---

