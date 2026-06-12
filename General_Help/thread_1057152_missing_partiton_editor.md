---
title: "missing partiton editor"
date: 2009-02-01
forum: General Help
---

### Post by lulumara on 2009-02-01
Hi just want to know how I can load partition editor to preferences or administration ? Can see any editor I needto partiton or resize the Ubuntu and other partitions in it.

---

### Post by taurus on 2009-02-01
You have to install it first and then it will be in System -> Administration.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```
However, if you want to resize Ubuntu, then you have to use gparted from the LiveCD  or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), since you cannot resize a partition while you are using it.

---

### Post by lulumara on 2009-02-01
> **taurus said:**
> You have to install it first and then it will be in System -> Administration.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```
However, if you want to resize Ubuntu, then you have to use gparted from the LiveCD  or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), since you cannot resize a partition while you are using it.

I did download Gparted but it doesn't shows it.

---

### Post by lulumara on 2009-02-01
HI did reinstalled it and look at it on system/adm/partiton editor.
Thanks for the helped cheers !!!

---

### Post by lulumara on 2009-02-01
Can I put partition on my Ubuntu while I'm using the Ubuntu rt now means I want to make another partition to make room for my other OS that I want to install in the near future?

---

### Post by taurus on 2009-02-01
You cannot shrink, expand, or resize your Ubuntu's partition while you are using it.  It has to be done by gparted from either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by lulumara on 2009-02-01
I can't even boot to cd because my boot configuration doesn't give me to boot to cd how can I enable it I using Window XP I had a Gparted cd live that I burned it also I got Partition Magic Live cd but can't even use it because of boot problem . Oh when I click second time the Partition Edittor it doesn't even shows up at first it shows up and click the edit but it hangs up or freeze then tried to closed it.

---

