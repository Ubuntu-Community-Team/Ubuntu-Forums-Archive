---
title: "Remaster and install text / menu"
date: 2011-12-03
forum: Desktop Environments
---

### Post by garagestmarien on 2011-12-03
I am remastering my own version of Ubuntu for the family.
What I would like to know:
                                      Is it possible to add changes to the install details you get while installing, as I have added and removed some programs and I would like to reflect this when my remaster is installing.

---

### Post by oldtimer7777 on 2011-12-03
> **garagestmarien said:**
> I am remastering my own version of Ubuntu for the family.
What I would like to know:
                                      Is it possible to add changes to the install details you get while installing, as I have added and removed some programs and I would like to reflect this when my remaster is installing.

Yes, you can install and use Remastesys or Relinux. A really handy program to deploy a customized version of Ubuntu.

It will create a custom live ISO of whatever Ubuntu system you have installed presently (everything you have added up until now), and you can then install from either a newly burned disc with that custom.iso file or you can use Startup Disc Creator to move that ISO to a Live Bootable Flash Thumb Drive of your Customized Ubuntu to install from.  Piece of cake.

You may want to use a walkthrough first to make you have all the packages you are going to need on there as well since you will be installing to multiple systems:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

And make sure to clean out your system before you use Remastersys to create your ISO.

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

A good customized ISO of Ubuntu that has just about everything and the kitchen sink is around 2.2 Gb in size.

I use them everyday, and I don't know what I would do without this Remastersys either. It has been a life saver.

---

### Post by kd4dii on 2011-12-03
Hi
     I have not used remaster but I have used UCK.  That is Ubuntu customization kit.  I have used it for custom versions of 10.1 and 11.04 and found it is easy to use and add software you want installed at set up.  I will give remaster a shot and see if I like it.

Bob

---

### Post by garagestmarien on 2011-12-03
Okay,
I don't think my question was very clear

I know about uck and remastersys.
What I want to add to is the display you get while the system is installing.
You get choose language, time zone, partitions etc, then you get a display about the system while it is installing. I.E. Telling you about the programs for graphics, internet etc.
This is the bit I would like to edit, so my system while installing will let friends and family know what programs are available. Such as I have changed over from Open office to Libre office and also added Opera browser and a customised version of Clementine.
I guess all I need to do is find where these screens are stored so I can edit them.

---

### Post by oldtimer7777 on 2011-12-03
Well Remastersys isn't going to give you that kind of option, and neither will Relinux.  I don't think you even get any
splash screen when you use gtk-ubiquity installer either, so you might be spinning your wheels there. You don't get to use
the original installer that Ubuntu has on the live iso download.  You use a generic one that installs with Remastersys and Relinux. 

There won't be a splash screen or any options like you are imagining, except for the bare minimum, but try it out to see what I am saying first. 

I think you are talking about the Ubiquity splash screen that promote certain aspects about Ubuntu???  Is that what you mean? Because I don't get an option with the live installer on my Remastersys to install different software packages during my installation...   From the alternative disc install version of Ubuntu with the Text Based installer it is possible however, but it is very ugly that way. I have no idea how to configure the text installer to customize it.  Way too overkill for my uses.

It would be easier to install everything on one custom.iso with Remastersys from a checklist so you have everything anyone would ever need, and they can simply uninstall whatever they don't want after it is done installing on their computers. I think you will find that is best way eventually, otherwise you are looking for way more work than it is probably worth in the long run...  unless you were trying to build your own custom distro of Linux to share with hundreds of thousands of users, I would probably just do a Remastersys Dist and be done with it.

> **garagestmarien said:**
> Okay,
I don't think my question was very clear

I know about uck and remastersys.
What I want to add to is the display you get while the system is installing.
You get choose language, time zone, partitions etc, then you get a display about the system while it is installing. I.E. Telling you about the programs for graphics, internet etc.
This is the bit I would like to edit, so my system while installing will let friends and family know what programs are available. Such as I have changed over from Open office to Libre office and also added Opera browser and a customised version of Clementine.
I guess all I need to do is find where these screens are stored so I can edit them.

---

### Post by garagestmarien on 2011-12-04
Thank you oldtimer7777,
Yes, it is the Ubiquity splash screen that promotes certain aspects about Ubuntu.
However, if remastersys doesn't let you have that, then in a way my problem is solved.
I just didn't want a splash screen explaining (as example) the virtues of Openoffice, when I have Libreoffice installed, or about Banshee when I have a customised version of Clementine.
No, I'm not making a distro for thousands (It would be nice to think I was capable:D), I'm just making a spin for family (so if they have a problem, or need help, it becomes easy for me as they have the same system as me) and the splash screen is not really important and does not effect anything I have done, it's more just me liking everything to be right.

---

