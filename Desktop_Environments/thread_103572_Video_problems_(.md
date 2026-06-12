---
title: "Video problems :("
date: 2005-12-14
forum: Desktop Environments
---

### Post by afcode on 2005-12-14
Hi im new on this forum, im trying to install kubunteu 5.10 on my laptop. :
1.- Installing:
im boot from cd, and appears the isntallation menu(default,etc..) im choose default, this begins to install and the picture starts to load, but then this stays in black... and dont installl anything.. im reboot and this time im choose :
linux vga=771
and, this time this installs ALL,
2.- trying to begin thi X desktop:
after installtion  reboot the system and appears the grub boot selector(i have kubuntu and winxp pro). im select ubuntu and starts to load, with a picture that says kubuntu with shados and fonts on blue(or some color like that :P).
then starts on TEXT mode...(i dont know why) im loged with my name and pass, and enters, im try to enter X or startx to starts the MODE GRAPHICAL, but sends me error on DRI:
(EE) RADEON(0) DRIselectInit failed or something like that..
Im try to get information with:
xorg.conf, sudo, etc.. but dont send me nothing....

my video card its:
Ati radeon xpress 200m with ram selectable(i have 32 selected, if i change to more like 64 or 128 never begins the system)
Thanks for any help you can give me. :D

---

### Post by afcode on 2005-12-14
:D im solved the problem:

I never know that the  ATI drivers arent on KUBUNTU 5.10 version,
for those that have problems with boot in X after install, just install the new drivers:
1.-sudo apt-get install xorg-driver-fglrx
2.-reboot
3.-echo fglrx | sudo tee -a /etc/modules
4.-reboot
5.-sudo depmod -a;sudo modprobe fglrx
6.-reboot
7.-sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11xorg.conf
8.-reboot

AND ITS ALL!!!
Now im answering my own question on my new kubuntu SYSTEM!!!!

:cool:

---

### Post by IconK7 on 2006-05-27
This one worked for me, too, but with one small change. The last line:

7.-sudo sed -i -e 's/"ati"/"fglrx"/' /etc**/X11xorg.conf**

worked only when I changed /X11xorg.conf to /X11/xorg.conf, so the line read:

7.-sudo sed -i -e 's/"ati"/"fglrx"/' /etc**/X11/xorg****.conf**

I have been trying to install Ubuntu/Kubuntu 5.10 for months, this is the only thing that worked. LOL just in time for Kubuntu 6.06 release in a couple of days.  I have tried a couple of beta releases (including the RC version just yesterday) and the install quits for the very same reason: my ATI X800XL videocard. Hope the Final release includes a fix. I have tried **Mandriva**, **SUSE** and **Mepis**, all have **NO** **PROBLEM** installing on this machine. What's **Ububtu's**  problem?

---

