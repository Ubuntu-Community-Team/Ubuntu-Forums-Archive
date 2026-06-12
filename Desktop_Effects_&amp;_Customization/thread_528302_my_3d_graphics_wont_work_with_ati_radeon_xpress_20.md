---
title: "my 3d graphics wont work with ati radeon xpress 200m"
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by the cooke on 2007-08-17
first of all im completely new to all of this ubuntu terminal stuff and i really need some help. for some reason my whole sudo apt-get wont work, my synaptic package manager wont work, and my add/remove program thing wont work. but the main reason i came here was to ask if someone could help me with my graphics card i have a ati radeon xpress 200m graphics card and i have beyrl installed but also need help installing the drivers and i need to get all of that other stuff working as well the main thing i want to do is get my 3d working. so if anybody can help the new guy it would really be appreciated.  oh yeah and since im the new guy i would sorta appreciate if you all didnt use the big words !!!

---

### Post by amadeus266 on 2007-08-18
I can't help with the 3d stuff since I have had no luck with that graphics card myself (I only tried twice on a friends PC) but you need to open a terminal and enter "sudo dpkg --configure -a" to reset the apt-get thing, then go into synaptic package manager and look under custom filter and then broken and see if you have any broken packages and fix them. You probably won't get very far with the graphics thing until you fix the other issues.

---

