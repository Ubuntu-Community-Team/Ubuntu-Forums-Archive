---
title: "How to install ATI driver for ubuntu 9.04"
date: 2009-06-21
forum: General Help
---

### Post by kraddark on 2009-06-21
Hi All!

I have followed the instructions  to install the ATI driver here [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers")


but it failed.. so i need to uninstall it..

Thanks in advance for the help!:)

---

### Post by Lord Noxarethor on 2009-06-21
You should go to System -> Administration -> Hardware drivers and install it from there.

---

### Post by kraddark on 2009-06-21
> **Lord Noxarethor said:**
> You should go to System -> Administration -> Hardware drivers and install it from there.

it says no proprietary drivers are installed on my system

---

### Post by Yellow Pasque on 2009-06-21
Please do not make multiple threads on the same subject. As I said in your other thread, the proprietary driver only supports RadeonHD 2x000 and later cards on Ubuntu 9.04

---

### Post by credobyte on 2009-06-21
Not to hijack this thread, but, what about ATI Radeon 9200 ? Haven't had a chance to install it correctly ( impossible wallpaper changing, screen recording at 2fps, etc. ). Hardware drivers are empty and I've followed a few Online tutorials with no luck so far.

---

### Post by Legace on 2009-06-21
> **credobyte said:**
> Not to hijack this thread, but, what about ATI Radeon 9200 ? Haven't had a chance to install it correctly ( impossible wallpaper changing, screen recording at 2fps, etc. ). Hardware drivers are empty and I've followed a few Online tutorials with no luck so far.

As he said, the ATi FGLRX driver does NOT support anything before HD2000. This includes 9200.

However, you should be perfectly fine with the open-source radeon driver (**xserver-xorg-video-ati**) as it offers full 3D acceleration for 9200.

---

### Post by credobyte on 2009-06-21
> **Legace said:**
> As he said, the ATi FGLRX driver does NOT support anything before HD2000. This includes 9200.

However, you should be perfectly fine with the open-source radeon driver (**xserver-xorg-video-ati**) as it offers full 3D acceleration for 9200.

Thnx, will try this later on today ;)

---

### Post by Yellow Pasque on 2009-06-21
> **credobyte said:**
> Thnx, will try this later on today ;)
You're probably already using it...

---

