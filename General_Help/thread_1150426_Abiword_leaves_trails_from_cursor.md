---
title: "Abiword leaves trails from cursor"
date: 2009-05-06
forum: General Help
---

### Post by SnappyU on 2009-05-06
Hi all,

Wonder if you guys get this problem?
My Abiword install in Ubuntu Jaunty is leaving trails all over.

Anyone facing the same problem or have a fix?

Many thanks! :)

---

### Post by Jozef Štaffen on 2009-05-09
I have the same problem, but only when I have compiz enabled.

---

### Post by pme 72 on 2009-05-26
Me too. I was using AbiWord for a log file in Hardy and Ibex but have switched to Text Editor in Jaunty. It does open more quickly. It was helpful to be able to change the font characteristics with AbiWord though. 

You can erase the trails by scrolling the page up or down. Turning off Compiz works too. I tried reinstalling AbiWord but that did not solve the problem.

---

### Post by electromatic on 2009-06-19
Hi,

Just an FYI, I tried the live CD of Fedora 11 (on my little EeePC) turned on compiz, and ran abiword.

No cursor drawing issues.

Yum was such a pain to use that I couldn't install ccsm to find out what compiz settings were going on to compare with what I have on ubuntu 9.04 with compiz running.

Will investigate more.

---

### Post by pme 72 on 2009-06-19
This week I upgraded my video card from ATI Radeon x1550 to Radeon HD4550. I did not think to check abiword with open source drivers with the new card but I enabled the fglrx driver and noticed that the cursor trails have disappeared.

---

### Post by becxjo on 2009-08-27
I have the same problem with my ubuntu 9.04 (x86_64). The abiword leave marks of cursor on the screen.

---

### Post by freddiespagheti on 2009-09-09
This wasn't a problem for me until I changed my appearance preferences. I fixed it by going to:

System>Preferences>Appearance

Click on the "Visual Effects" tab and then set it to either "Normal" or "None"

---

### Post by becxjo on 2009-09-25
Just for your information the issue of Abiword is not only related to compiz. It seems that Abiword behaves as such in the presence of any [other] composite manager. I installed a minimalist ubuntu without Gnome and Metacity (OpenBox is windows manager) and for creating visual effects I added xcompmgr (which is a very light composite manager). The result with Abiword was the same.

Note that here I don't have any of gdm, metacity, compiz and/or gnome.

---

