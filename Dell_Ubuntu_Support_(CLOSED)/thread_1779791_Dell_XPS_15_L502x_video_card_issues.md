---
title: "Dell XPS 15 L502x video card issues"
date: 2011-06-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shadowsall on 2011-06-10
Hi, I have a Dell XPS 15 L502X with the integrated Intel HD graphics and a Nvidia GeForce 525M.  Currently I am using the Nvidia-current driver.  When I look at the "Additional Drivers" tility, it says the "Nvidia driver is activated, but not in use."  I would prefer to use the Nvidia driver to the Intel graphics.  Right now I am having trouble with 3D acceleration in Ubuntu 11.04.  I have used nvidia-xconfig, but every time I restart the xorg-server it is no longer able to run and I have to revert the the backup xorg.conf.  I am running xorg-server-core version 1.10.  I am wondering if anyone has any solutions for me to enable 3D acceleration in Ubuntu 11.04.

---

### Post by RI_VIPER on 2011-06-12
I have the same issues.....without using the graphics card...the display quality is too bad. the display breaks at certain places, and dragging a window leaves trails.

---

### Post by Finalfantasykid on 2011-06-13
Because Optimus isn't quite supported yet, the closest thing to getting full 3d capabilities is by using bumblebee [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee).  I would recommend using the intel graphics for regular desktop usage, that way you get 3d acceleration, and high battery life, but using bumblebee you will be able to run games or other gpu demanding programs with the nvidia card.

---

### Post by Blitzskee on 2011-07-29
> **Finalfantasykid said:**
> Because Optimus isn't quite supported yet, the closest thing to getting full 3d capabilities is by using bumblebee [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee).  I would recommend using the intel graphics for regular desktop usage, that way you get 3d acceleration, and high battery life, but using bumblebee you will be able to run games or other gpu demanding programs with the nvidia card.

I have the same issues as the above posts, zero 3D acceleration therefore no unity.

How would I go about using the intel graphics for regular desktop usage?

---

### Post by Vusys on 2011-07-29
> **Blitzskee said:**
> I have the same issues as the above posts, zero 3D acceleration therefore no unity.

How would I go about using the intel graphics for regular desktop usage?

Seconded. I'm pretty sure it's already using the intel graphics, but there are graphical glitches when using Compiz. Some effects will cause the desktop to flicker and reload. Stranger still, 
after installation with 11.04, it works fine. After all the updates and a reboot it's only then I get problems.

---

### Post by ehode on 2011-07-29
In order to wrestle control with that video card you'll need to get optimus up and going.

I have a XPS 15 (L502) also.

Wrote up a quick entry on my site about it.

[http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support](http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support)

---

### Post by partofthething on 2011-10-26
The bumblebee project that you link in your comment appears to be obsolete, according to this page:
[https://launchpad.net/~mj-casalogic/+archive/bumblebee]("https://launchpad.net/%7Emj-casalogic/+archive/bumblebee")

I'm finding links suggesting using Ironhide instead:
[https://launchpad.net/~mj-casalogic/+archive/ironhide/+packages]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/+packages")

The guy running both these projects updates status on his blog:
[http://www.martin-juhl.dk/](http://www.martin-juhl.dk/)

I haven't tried ironhide yet but will need to soon since I accidentally enabled the proprietary driver and now my fan runs all the time b/c the nvidia card is taking all my juice.

---

