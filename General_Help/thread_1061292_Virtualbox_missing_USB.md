---
title: "Virtualbox missing USB"
date: 2009-02-05
forum: General Help
---

### Post by xsilvergs on 2009-02-05
Hi,

I'm using Intrepid with latest updates (05-02-09) and have just installed Virtualbox OSE 2.0.4 from the repositories, I then installed Windows XP-Home as the guest.

There is no mention of USB in the lefthand side of Virtualbox Setting.
When I run Windows in virtualbox if I select Devices and then hover over USB Devices the menu to the right the only option is <no available devices>

I have read many post on the forum but they seem to relate to older Gutsy or Hardy versions.

Can anybody help me enable USB?

Thank you.

---

### Post by lykwydchykyn on 2009-02-05
The open source version does not do USB, IIRC.  You need to download the non-opensource version from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

EDIT: see this page for feature comparisons:
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by albinootje on 2009-02-05
> **xsilvergs said:**
>  I'm using Intrepid with latest updates (05-02-09) and have just installed Virtualbox OSE 2.0.4 from the repositories, I then installed Windows XP-Home as the guest.

There is no mention of USB in the lefthand side of Virtualbox Setting.


You need the PUEL version from the VirtualBox website, because the OSE version doesn't support usb..

Easiest is the install Virtualbox 2.1.2 (or later) which does not need any changes at all when it comes to "enabling usb support" inside the VirtualBox host system itself.

---

### Post by RedSingularity on 2009-02-05
Even when you check the USB boxes in the "real" version it still wont work.  Look at [THIS]("http://ubuntuforums.org/showthread.php?p=2082674")
Just follow the instructions there and you will be fine.

---

### Post by albinootje on 2009-02-05
> **Shadow121 said:**
> Even when you check the USB boxes in the "real" version it still wont work.  Look at [THIS]("http://ubuntuforums.org/showthread.php?p=2082674")
Just follow the instructions there and you will be fine.

With VirtualBox PUEL 2.1.2 (and newer) this is no longer needed. 
Usb support "for VirtualBox itself" should work out of the box.

---

### Post by xsilvergs on 2009-02-05
Thanks.

I've removed the OSE version using Synaptic and installed the .deb from Virtualbox site, installed it but it doesn't show up under Accessories.

Any ideas?

---

### Post by RedSingularity on 2009-02-05
> **albinootje said:**
> With VirtualBox PUEL 2.1.2 (and newer) this is no longer needed. 
Usb support "for VirtualBox itself" should work out of the box.

Thats what i thought.  Then once i had it set up it wouldnt work untill i followed these steps.  Mabey it was just my PC  x_X

---

### Post by albinootje on 2009-02-05
> **xsilvergs said:**
> installed it but it doesn't show up under Accessories.


-> Applications -> System Tools

---

### Post by xsilvergs on 2009-02-05
albinoottje

It doesn't come up there either, I've started it from Terminal and USB is there now.

Is there an easy way to add things to the menus?

---

### Post by albinootje on 2009-02-05
> **Shadow121 said:**
> Thats what i thought.  Then once i had it set up it wouldnt work untill i followed these steps.  Mabey it was just my PC  x_X

Hmm, I cannot find the thread related to the usb-in-VB howto by hotshotdj concerning version 2.1.2, but I've tested the default-usb-support from VB 2.1.2 in Ubuntu 8.04 and it worked.

That howto is here by the way :
[http://ubuntuforums.org/showthread.php?t=1015763](http://ubuntuforums.org/showthread.php?t=1015763)

---

### Post by albinootje on 2009-02-05
> **xsilvergs said:**
>  Is there an easy way to add things to the menus?

Hmm, weird :( Can you test it first with :
*) opening a terminal
*) then type : VirtualBox

And then add a custom launcher to your top panel by right-clicking on the top panel, and choose "add to panel", custom appl. launcher, with name -> VirtualBox, and command -> VirtualBox.

---

### Post by xsilvergs on 2009-02-06
albinootje

Thank you thats's it, and thanks to the others that posted to help me. I've even managed to connect my Garmin Zumo GPSr.

Tony

---

