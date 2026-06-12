---
title: "desktop effects couldn't be enabled"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by moh_nema on 2007-10-23
hi I'm new In Ubuntu

I have problem

when I tray to enable desktop effects I have these message
desktop effect couldn't be enabled

how can solve these problem ?

---

### Post by Lord_Dicranius on 2007-10-23
What type of video card does your PC have?

---

### Post by moh_nema on 2007-10-23
my vedio card is
intel (R) 946Gz express chipset family

---

### Post by Kiyo86 on 2007-10-23
Could you go into the package manager and post which Compiz packages are installed?  It could be that there are some integration packages are not installed yet.

---

### Post by googlah on 2007-10-23
I had this. The problem is that you are using the GNOME session. You will need XGL to get it to work.. atleast for me.

So fire up a terminal and install it with
```
sudo apt-get install xserver-xgl
```

---

### Post by Lord_Dicranius on 2007-10-23
> **googlah said:**
> I had this. The problem is that you are using the GNOME session. You will need XGL to get it to work.. atleast for me.

So fire up a terminal and install it with
```
sudo apt-get install xserver-xgl
```
Beat me to it ;-P

---

### Post by rootie on 2007-10-24
Before you do that, try this:

Run Systems>Administration>Screens and Graphics>Graphics Card tab.

Did Ubuntu choose the right graphics card driver?

If not, choose the right one. Try enabling effects now.

No go? Reboot, check if the selected driver is still correct, then try enabling again.

Worked for me (Intel 85x) :D

Solution from here: [http://ubuntu-utah.ubuntuforums.org/showpost.php?p=3518530&postcount=12](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=3518530&postcount=12)

---

