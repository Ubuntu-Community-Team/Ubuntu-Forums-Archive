---
title: "WEP Key Lost!"
date: 2008-12-08
forum: General Help
---

### Post by DizzyEwok on 2008-12-08
I lost the WEP key and the password to get it back so I was wondering if I could try to crack my own network?
I have been looking around and I have seen "Aircrack" so I installed it but I cannot find it anywhere and if I try to install it again it says it is already installed...
Anyone know what to do?

Thanks

---

### Post by SPr on 2008-12-08
See my post below. Google screwed up the links in this version.

---

### Post by Dr Small on 2008-12-08
Don't you have access to the router where you can change the WEP key?

---

### Post by gettinoriginal on 2008-12-08
Do a file search for aircrack, or you can try to type it in terminal to see if that starts it.  For more help I found this.

[http://www.linuxquestions.org/questions/linux-newbie-8/retrieve-a-wep-key-wifi-in-ubuntu-gutsy-617722/](http://www.linuxquestions.org/questions/linux-newbie-8/retrieve-a-wep-key-wifi-in-ubuntu-gutsy-617722/)

Good luck:p

---

### Post by SPr on 2008-12-08
I've never used aircrack but I do know that it has to be run as root from the terminal (sudo aircrack-ng, sudo airodump-ng etc).

Aircrack-ng isn't the only program installed with this package and they will be listed in the manual (man aircrack-ng).

It's a complex set of programs so take a look at the manuals and follow this tutorial [http://www.aircrack-ng.org/doku.php?id=tutorial](http://www.aircrack-ng.org/doku.php?id=tutorial) the newbie guide [http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide) and here's the main site [http://aircrack-ng.org/doku.php](http://aircrack-ng.org/doku.php)

I'm all for doing things the hard way (you learn far more like that) but why not log into the router and change the key or, easier still, reset the router?

---

### Post by DizzyEwok on 2008-12-08
As I have said, you need a password to log into the router which I have lost but at the moment I am trying to work it out and it seems to be working.....But it says...
 -a <amode> : force attack mode (1/WEP, 2/WPA-PSK)
How do I type that into the terminal?
sudo aircrack-ng -a 1 (doesn't work)?

---

### Post by edm1 on 2008-12-08
I can tell you how to use aircrack but it'd be alot easier for you to press the reset button on your router.

---

### Post by itsbradman on 2008-12-08
As SPr said, why not reset the router?  All residential wireless routers have resets that will restore them to default logins and ususally no wep.

---

### Post by lakris61 on 2008-12-08
> **DizzyEwok said:**
> As I have said, you need a password to log into the router which I have lost but at the moment I am trying to work it out and it seems to be working...


Hi,
something similar has happened to me before. One way is to reset Your router to the factory defaults and use the default username/password. Have You tried that?

/Lakris

---

### Post by theozzlives on 2008-12-08
> **DizzyEwok said:**
> I lost the WEP key and the password to get it back so I was wondering if I could try to crack my own network?
I have been looking around and I have seen "Aircrack" so I installed it but I cannot find it anywhere and if I try to install it again it says it is already installed...
Anyone know what to do?

Thanks

My router has a reset button you push with a pen to reset everything, including passwords, to default factory settings.

---

