---
title: "How to create an O.S. Image?"
date: 2009-02-11
forum: General Help
---

### Post by JECHO on 2009-02-11
Hey guys I have just got ubuntu 8.10 running, and looking how i want it to and am trying to figure out how i can create an image of the O.S. (as i have it configured) so that i can just burn the .iso file to a disk and boot to it if i ever need to reinstall. anyone know how i can do this? Its a pain when i have to reinstall the O.S. because i then have to reinstall the programs and everything... if anyone can help me out at all, that would be awesome. Thanks

---

### Post by AllRadioisDead on 2009-02-11
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by JECHO on 2009-02-11
> **ihermit said:**
> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I know how to create .iso files.... what im asking is how to create an iso backup of my linux configuration and have it bootable.... im assuming it is much different than just creating a normal disk image.

---

### Post by avtolle on 2009-02-11
Take a look at remastersys. I think that will help you do what it is that you want.

---

### Post by JECHO on 2009-02-11
> **avtolle said:**
> Take a look at remastersys. I think that will help you do what it is that you want.


remastersys?

---

### Post by avtolle on 2009-02-11
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html) for some information.

---

### Post by LowSky on 2009-02-11
> **JECHO said:**
> remastersys?

Yes, and it works great.. one word of Caution, disable and uninstall any proprietary drivers (like graphics and wifi) beofre making the disk nas other systems will not have the same hardware.

---

### Post by mykrob on 2009-02-11
or you could just buy a copy of Acronis True Image, runs about $50 USD. If you have access to a Windows machine, you can create a bootable Acronis disk and make an image of your Ubuntu machine as it is right now. To restore that image, boot from the same Acronis disk and restore the image from either another disk or a network location.

I use this app a lot for work, although we have the server version. It does fine for Linux or Windows.

I have also used clonezilla for Linux.

---

