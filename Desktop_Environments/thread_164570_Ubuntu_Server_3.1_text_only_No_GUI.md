---
title: "Ubuntu Server 3.1 text only No GUI"
date: 2006-04-23
forum: Desktop Environments
---

### Post by new2linuxtoo on 2006-04-23
I am new to Ubuntu, and Linux for that matter. I have worked a load for my Dell 2400 and all is good. When I boot ubuntu it comes up and I log in.....but I am stuck in the old days of text not graphics. I have seen screen shots of graphics and instructions are graphic related. How do I boot into a gui session...Thanks in advance..

---

### Post by Mr Egg on 2006-04-23
It should do it automatically. What graphics card do you use?

---

### Post by dermotti on 2006-04-23
run  **sudo dpkg-reconfigure xserver-xorg**  and select **vesa** as your driver

then reboot

---

### Post by new2linuxtoo on 2006-04-23
Dell onboard ATI Technologies Inc 3D Rage IIC

---

### Post by dermotti on 2006-04-23
The above command should work no matter what. But you can also select ATI as your driver, but its not guranteed to work.

---

### Post by new2linuxtoo on 2006-04-23
I tried that and I am told xserver-xorg not installed and no fiole info is available

---

### Post by dermotti on 2006-04-23
umm... did you do a server install?

if you want graphics you need to install
[B]
sudo apt-get install ubuntu-desktop[/B] for gnome desktop

[B]
sudo apt-get install xubuntu-desktop[/B] for xfce desktop (best for servers)

or

[B]
sudo apt-get install kubuntu-desktop[/B] best for noobs

its gonna download bout 300 megs of stuff

---

### Post by enopepsoo on 2006-04-23
you must have done a server install.  Don't just jump right into gnome though!  Read up on Xubuntu and Kubuntu.  If you are 100% new to linux, use the gnome, but otherwise, why not experiment?

---

### Post by new2linuxtoo on 2006-04-23
I did the default install which I believe was a server install.

---

### Post by paritybit on 2006-04-23
From what I use none of my Debian servers use X. Maybe you should try ubuntu normal flavour if you are new to linux to cut your teeth on and then maybe move to server enviroment. I am sure you can install xorg on the server version but the normal flavour will install it all automatically and take a lot of the legwork (fingerwork?) out of it.

---

### Post by new2linuxtoo on 2006-04-23
Ubuntu desktop has downloaded and installed .... thanks.

I am sure I will be back again..

---

