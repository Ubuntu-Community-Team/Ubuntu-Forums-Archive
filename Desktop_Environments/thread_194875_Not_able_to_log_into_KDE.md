---
title: "Not able to log into KDE"
date: 2006-06-12
forum: Desktop Environments
---

### Post by jaideepg on 2006-06-12
I'm new to Ubuntu and spent most of the weekend installing ubuntu on my homemade pIII system. Since I had worked on KDE earlier I decided to install KDE as the windows manager. So far, so good.

I used the Synaptics application to download KDE, installed it and restarted my system, then nothing....

Well, actually, something did happen, the Ubuntu startup screen was replaced with the Kubuntu startup screen, after the processes load, I get to the login UI. Here is where the problem starts. I enter my username and password, the screen goes blank, and its back to the login screen. I'm not sure whats happening here. The console login works with the same username but doesnt work in the windows manager. If I enter the wrong password I get a prompt saying invalid login but if I enter the right one, it goes blank and brings me back to the login screen.

I need help! :-(  This is my main system as I junked my Windows installation for Ubuntu (after the nth virus attack).

---

### Post by Yigal on 2006-06-14
Did you solve it?

I have similar question - I'm new to ubuntu, downloading KDE packages now, want to try it without deleting gnome.

How (and what? session manager? start up?) should I organize for having choice on logon what to run - gnome or kde?

---

### Post by claydoh on 2006-06-14
What packages did you install?
The only thing you need to install is "kubuntu-desktop" which is a meta-package that tells synaptic to download and install everything you need for a complete Kubuntu desktop. It sounds like there aare parts missing and kde cannot load. If you get the login screen, you should be able to select Gome from the menu and get to your Ubuntu desktop. from there, you should use synaptic to install "kubuntu-desktop" to grab any missing KDE bits.

the command line actions is:
```
sudo apt-get install kubuntu-desktop
``` Afterward, if you find you prefer the Gnome login manager, type the following in a terminal window:
```
sudo dpkg-reconfigure kdm (or gdm, either one will bring up a login manager selection dialog)
``` You will be able to select whichever desktop you wish with either style of login manager


[SIZE=1]* edited to fix stupid typing error*[/SIZE]

---

### Post by jaideepg on 2006-06-15
Thanks Claydoh! Will try this.

---

### Post by jaideepg on 2006-06-15
[QUOTE=claydoh]
the command line actions is:
```
sudo apt-get install kubuntu-desktop
```
Afterward, if you find you prefer the Gnome login manager, type the following in a terminal window:
```
sudo dpkg -reconfigure kdm (or gdm, either one will bring up a login manager selection dialog)
```
You will be able to select whichever desktop you wish with either style of login manager[/QUOTE]

I did the first part and it downloaded the Kubuntu-desktop and installed it properly. when I try to use the second command you suggested, i get the following output - 

"dpkg: conflicting actions --control and --remove"

I'm still not able to log into the system using KDE or Gnome.:confused:

---

### Post by xenblend on 2006-06-15
I HAVE THE EXACT SAME PROBLEM AS YOU!!!!

Did you fix it? I have an Emachines (POS :P) T2625 w/ integrated audio/video/LAN... um, Athlon XP chip... do you have any of these things? Did you FIX it??

---

### Post by claydoh on 2006-06-15
[quote=claydoh]What packages did you install?
The only thing you need to install is "kubuntu-desktop" which is a meta-package that tells synaptic to download and install everything you need for a complete Kubuntu desktop. It sounds like there aare parts missing and kde cannot load. If you get the login screen, you should be able to select Gome from the menu and get to your Ubuntu desktop. from there, you should use synaptic to install "kubuntu-desktop" to grab any missing KDE bits.

the command line actions is:
```
sudo apt-get install kubuntu-desktop
``` Afterward, if you find you prefer the Gnome login manager, type the following in a terminal window:
```
sudo dpkg -reconfigure kdm (or gdm, either one will bring up a login manager selection dialog)
``` You will be able to select whichever desktop you wish with either style of login manager[/quote]

Ooookaayy, I apologize for the error, but the correct command would be :
> sudo dpkg-reconfigure gdm
I added a space between 'dpkg' and '-reconfigure' :sad:

---

### Post by xenblend on 2006-06-16
I wish I had checked back sooner... I'm re-installing kub606 with the alternate cd now... :( 

I'll post teh results though. :)

---

