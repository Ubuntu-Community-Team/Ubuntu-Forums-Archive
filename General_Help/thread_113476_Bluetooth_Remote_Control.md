---
title: "Bluetooth Remote Control"
date: 2006-01-06
forum: General Help
---

### Post by sunny_nwho on 2006-01-06
I will be very thankful if anyone can tell me how i can use my Sony Ericcson K750 as a remote control with my laptop for music as well as presentation. I want to use the remote either by IRDA ot Bluetooth....thanks in advance

---

### Post by Nomearod on 2006-01-06
[QUOTE=sunny_nwho]I will be very thankful if anyone can tell me how i can use my Sony Ericcson K750 as a remote control with my laptop for music as well as presentation. I want to use the remote either by IRDA ot Bluetooth....thanks in advance[/QUOTE]


I also would like to know about any program to do that, but I own a Nokia 6680.

---

### Post by sunny_nwho on 2006-01-13
I found a solution...the bluetooth remote control works excellent in Gnome....but in KDE u have to do some command line work.......first i will tell gnome then KDE

GNOME
$sudo nano  /etc/default/bluez-utils and chnage the HIDD_ENABLE = 1

restart computer and start remote control from your phone (SE 750i) and u will see that the remote works....So far i did not know how to configure media player but i can use the desktop and presentation..

KDE 3.5

chnage as above...after this i had a problem of pairing so i used the following command and it worked well

$ sudo hcitool cc --role=m <address of the phone>

and ur phone will be paired and u can normally start remote from the phone and it works....

---

### Post by QwUo173Hy on 2007-09-15
Will this work with any bluetooth phone or do I need to buy a specific model?

---

### Post by FuturePilot on 2007-09-15
This got me going with my Sony Ericsson
[http://ubuntuforums.org/showpost.php?p=1774584&postcount=10]("http://ubuntuforums.org/showpost.php?p=1774584&postcount=10")

---

