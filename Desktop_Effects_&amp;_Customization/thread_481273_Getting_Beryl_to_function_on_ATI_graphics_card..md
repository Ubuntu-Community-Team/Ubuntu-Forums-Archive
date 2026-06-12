---
title: "Getting Beryl to function on ATI graphics card."
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by Antonio44 on 2007-06-22
I have heard that about this beryl thing and I really would like to use it. i have installed it and when I go to enable desktop effects my screen goes white for a little while and then nothing happens. I am running Ubuntu 7.04 and I have a gateway MX something or other. I want to think my graphics card is a ATI Radeon XPRESS 200M 5955. That is what the device manager says anyway. I ould like to get all those cool beryl effects. Please help. I am a newbie so make it as easy as possible please!


A.

---

### Post by akshayas1986 on 2007-06-22
Desktop effects on System > Preferences is for Compiz (Another desktop manager)... Go to shell and type

beryl-manager

You should get a Ruby on the taskbar and I think your desktop effects must be enabled (Considering you video drivers are fine)

Akshaya Srivatsa

---

### Post by Antonio44 on 2007-06-22
Ok I did that but nothing happens.
The ruby shows up but it all works the same.

A.

---

### Post by cawill on 2007-06-22
To change window manager, right click on ruby, select 'Select Window Manager' and choose Beryl.

---

### Post by Antonio44 on 2007-06-22
The screen went completely white and I had to reboot.

---

### Post by Ultra Magnus on 2007-06-22
What card do you have - if it is not supported by the open source driver you need to get the the closed source one - but this doesn't support 3d so you need to use Xorg. I found it quite difficult to set up and I had no idea what I was doing but i used some scripts from here [http://ubuntuforums.org/showthread.php?t=257684](http://ubuntuforums.org/showthread.php?t=257684) and its all working fine.

Try getting 

sudo apt-get install xserver-xorg

---

