---
title: "Help with Using GNOME on HDTV"
date: 2008-09-10
forum: Desktop Environments
---

### Post by tehredbull on 2008-09-10
Hello, I just recently installed Ubuntu 8.04 LTS and I love it, accept for the fact that I cannot change the screen resolution to 1280 X 1024. It allows me only one option that is so bad that it is very difficult to use Ubuntu. I am new to Linux all together, so any help is appreciated.

Thanks in advance,



tehredbull

---

### Post by BLTicklemonster on 2008-09-10
What video card do you have?

Have you tried installing the restricted drivers for it, if it's a new enough video card?

What are you using to connect to the hdtv? Don't try s video it stinks. Try to find a vga cable at least.

---

### Post by tehredbull on 2008-09-10
I have an Nvida 9800 GT, I haven't been able to find a working link for the drivers, and I'm using DVI, so there shouldn't be any worries there.

---

### Post by BLTicklemonster on 2008-09-10
In synaptic, find envyng-gtk, and try it to get the best drivers. Hopefully what will get you the resolution you want. My Ubuntu looks awesome on our 50 inch plasma!

---

### Post by tehredbull on 2008-09-10
Edit I'm currently installing envyng-gtk. I'll let you know how it goes.

---

### Post by BLTicklemonster on 2008-09-10
You found synaptic, good. I'm sorry I just tossed an answer out like that.

---

### Post by tehredbull on 2008-09-10
I tried installing some drivers, but it didn't work.When I run the nvidia X server configuration tool this comes up: You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by BLTicklemonster on 2008-09-10
Main Menu, Applications, Terminal

type

sudo nvidia-xconfig

press enter

enter password (don't freak when you don't see letters when you type your password)

Reboot the computer.

---

