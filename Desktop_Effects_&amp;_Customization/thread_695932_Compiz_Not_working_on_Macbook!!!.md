---
title: "Compiz Not working on Macbook!!!???"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by k3y5rmy1if3 on 2008-02-13
Guys!!! I just got ubuntu. (I'm a newb!!!) Im running it off of my macbook, newest gen. It has a gma x3100 video card, and 1 gig of ram. I installed compiz fusion,and when i try to enable desktop effects it says that they cant be enabled! it doesnt go higher than "none". I would really really appreciate it if someone could help me fix this problem! i'll do anything! its so irritating cause compiz looks so awesome...i would really appreciate real answers, and not just a reply to look through the forum, if thats possible. PLEASE HELP!

---

### Post by ronmarley1 on 2008-02-13
> **k3y5rmy1if3 said:**
> Guys!!! I just got ubuntu. (I'm a newb!!!) Im running it off of my macbook, newest gen. It has a gma x3100 video card, and 1 gig of ram. I installed compiz fusion,and when i try to enable desktop effects it says that they cant be enabled! it doesnt go higher than "none". I would really really appreciate it if someone could help me fix this problem! i'll do anything! its so irritating cause compiz looks so awesome...i would really appreciate real answers, and not just a reply to look through the forum, if thats possible. PLEASE HELP!

The Intel 3100 cards have been blacklisted because of video playback issues.  This link: [http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112) is to a sticky above that explains how to get around it.  However, you may have video playback issues.
In a side not, I was able to have Compiz-Fusion running using the live CD on a friend's Macbook with the same specs.  It worked right out of the box using the experimental driver.  I did not try video while using the live CD.  It was on a friends PC and I just wanted to play a bit.

---

### Post by k3y5rmy1if3 on 2008-02-13
I entered the code into terminal...and i went into appearance, it will still not let me check "custom appearance", it just pops up with "cannot set desktop effects"...im getting quite depressed... ;-(

---

### Post by k3y5rmy1if3 on 2008-02-13
OHHHHHH! Do i need xgl to run compiz/desktop effects?!!! I tried to open compiz from terminal and it said that xgl was not present!!! where could i get xgl without paying?

---

### Post by ronmarley1 on 2008-02-14
XGL is free.  Typing ```
sudo apt-get install xserver-xgl
``` in a terminal should do it.
However, I don't think you want XGL.  AIGLX should work.
Did you try the intel experimental driver?  Go into System -->Administration -->Screens and Graphics.  On the Graphics Card tab, try changing the driver to "intel-Experimental modesetting driver for Intel integrated graphics chipsets."  After making the change, you'll need log off or restart X to have the changes take affect.  You can restart X by hitting the <Ctrl><Alt><Shift><Backspace> keys.

---

