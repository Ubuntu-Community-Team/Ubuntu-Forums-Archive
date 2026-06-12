---
title: "Xfce4 and Fluxbox question"
date: 2007-01-29
forum: Desktop Environments
---

### Post by ghandi69_ on 2007-01-29
Hi All, 

This is my first non-specific, not troubleshooting, more general question to post on these forums, so for those who do not like such questions.. I am sorry.  Basically, I am going for a completely new setup.  I am running ubuntu with gnome currently, on an Athlon 64fx 3200+ , 1 gig ram, 200 gig sata2, 7600gs video card, and to me it just feels too sluggish.  Too speed things up, I am planning on doing a complete reinstall, however I will be installing the server version of 6.10, and will build on top of it.  My main priorities for my new setup are.

1.) To be fast.  When I click on things to start programs, open folders, etc.. I want it to happen right away!

2.) To be functional.  My main uses for my computer include.. listening to music with amarok, importing audio cd's and downloading a ton of music, c++ programming with anjuta, web development with bluefish, photo shopping with gimp,  I have an external hard drive I like to be able to plug in with usb and have it auto detect, along with an ipod.  Also, I have not done this, but I hope to be purchasing a TV/Tuner card soon and implenting that into my system as well.

3.) For the Desktop to look nice.  I know that seems to conflict with my first priority, but its not like my computer is 5 years old, plus, I am easy to please when it comes to this.  By looking nice, I don't want many 3d wiz bang special effects, I just want to have total control for color themes and window menus, from colors to text fonts to panel widths... maybe if I'm feeling crazy I'll have a conky script running.

So my question is, I think I'm going to go with fluxbox or xfce, but I"m not sure which one. Also, are there any functionality issues in terms of ease of use that one or the other really cuts back on?  Also, I've heard that gnome and kde are "desktop" environments where xfce and fluxbox are "window managers".. does that mean I have to add more things after the server install...

(note:: I've been practicing with the setups... I've done the server install and have added both setups.. and so far, from early experimenting, configuring fluxbox seems easier, but I've barely scratched the surface.)

Any kind of input would be much appreciated!!

THanks,  

Ghandi_69

---

### Post by kerry_s on 2007-01-29
Try Xubuntu first before you go for the server install and have to figure out what you need to get everything to work.-> [http://www.xubuntu.org/get#edgy](http://www.xubuntu.org/get#edgy)

---

### Post by ghandi69_ on 2007-01-29
> **kerry_s said:**
> Try Xubuntu first before you go for the server install and have to figure out what you need to get everything to work.-> [http://www.xubuntu.org/get#edgy](http://www.xubuntu.org/get#edgy)

Hey, I'll look into it.  However, I guess something I should have mentioned is that I enjoy the learning experience as well, so when looking at the two systems.. I'm willing to work around bugs to get to my ideal desktop, as opposed to starting with it.  I guess I was wondering about the possibilities and potential more than ease of use.

---

### Post by kerry_s on 2007-01-30
Sounds good, I guess i'll just kinda run through what i usually do with a server install.

server install
login
sudo su
nano /etc/apt/sources.list
# out the cdrom and un # all the repos
ctrl+x+y and enter to save
apt-get update
apt-get dist-upgrade
(your install line, see below)
reboot
login and continue building up, i usally just wait till i need something and then install it.

Fast no flash system:
apt-get install x-window-system-core gdm fluxbox emelfm leafpad eterm synaptic

With thunar:
apt-get install x-window-system-core gdm fluxbox thunar leafpad eterm 
synaptic

Xfce4:
apt-get install x-window-system-core gdm xfce4 leafpad synaptic


That's all to it, quick simple install just enough to get you into gui and continue from there at your leisure.

---

### Post by 3rdalbum on 2007-01-30
XFCE is a desktop environment. When you install it, you get a file manager, panels, an Applications menu, configuration utilities, window manager, and multiple desktops. Fluxbox is a window manager - you get the window manager, an applications menu, and a virtual desktop switcher.

---

### Post by ghandi69_ on 2007-01-30
Hey Kerry and 3rd.. THanks for the input..

Thanks guys.. I think I'm probably going to go with XFCE4, just because it sounds a little more functional.  Kerry, that information regarding extra things to install when adding XFCE will be very useful, such as leafpad and synaptic.  I'm pretty comforable about where things are regarding the repos and how to add and configure different sources... so I think I should be alright. 

thanks,
Ghandi

---

### Post by kerry_s on 2007-01-30
Good deal, you know where to reach us if you get stuck. :D

---

