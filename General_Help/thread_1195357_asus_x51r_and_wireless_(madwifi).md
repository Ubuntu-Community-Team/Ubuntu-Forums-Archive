---
title: "asus x51r and wireless (madwifi)"
date: 2009-06-23
forum: General Help
---

### Post by TheLions on 2009-06-23
[B]Hello!

I have problem with setting madwifi on my second computer - Asus laptop.
The funny thing I managed to get my wireless on Ubuntu 8.10 half year ago, but today after installing newer version of Ubuntu 9.04 i can't make it work.[/B]
[B]
Can someone point me in right direction?[/B]

And yeah i'll reinstall Ubuntu 9.04 bo eliminate all my config mess before trying anything.

lspci output:
02:00.0 Ethernet controler: Atheros Comunications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig output:
[[IMG]http://slike.hr/slika/p5y5wep0.png[/IMG]](http://slike.hr)

NetworkManager dosen't show any wirelles on range even AP is 1 meter away.

[COLOR="Orange"]**solved:**[/COLOR] [http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

---

### Post by 4r45h1 on 2009-06-23
I'm having the same problem with ubuntu netbook remix at my acer aspire one (a150)
my wi-fi it's an atheros a242x and can't make it work ;\
I've searched all foruns, all google stuff but no solution.

---

### Post by TheLions on 2009-06-24
did you looked here:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) ?

or here:
[https://help.ubuntu.com/community/AspireOneDiscussion](https://help.ubuntu.com/community/AspireOneDiscussion) ?

or here:
[http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164&p=1233#p1233](http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164&p=1233#p1233) ?

also **MAKE SURE THAT WIRELESS SWITCH IS ON**, i spent several hours trying to install drivers but switch was **OFF** so i had to do clean install to remove all my mess before installing drivers from upper link.
Also indicator led doesn't show current state of wireless so you can know is it off or on. Also on my laptop switch is switching only while loading Ubuntu (1s after grub screen )

---

### Post by smogf on 2009-07-27
This wifi card works with ath5k kernel driver so don't need to install madwifi driver anymore.

Greets.

---

