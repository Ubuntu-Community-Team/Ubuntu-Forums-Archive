---
title: "Fedora 11 can't find my wireless network"
date: 2009-06-22
forum: General Help
---

### Post by shizumasa14 on 2009-06-22
I have an Acer Aspire 4730z running Fedora 11 with KDE. (I switched temporarily from ubuntu because jaunty doesn't like my Intel graphics card), and it wont find my network when I click on the network icon. It found it easily in Ubuntu. Can someone help please? Thanks!

---

### Post by epyonite on 2009-06-22
If you cannot see any wireless networks, you may have to install drivers for your wireless card, ubuntu and fedora support differnt ones on a fresh install, you can use ndiswrapper or what works for me is BCM43xx-fwcutter [http://fedoramobile.org/fc-wireless/bcm43xx-yum-extras](http://fedoramobile.org/fc-wireless/bcm43xx-yum-extras)

If you can see other wireless netowrks you may need to turn on wpa-supplicant support
system->admin->services then scroll down to wpa-supplicant

you might also try the fedora forums, I myself prefer fedora but i would imagine most people here use mainly ubuntu.

---

