---
title: "How to start X windows"
date: 2007-05-30
forum: Desktop Environments
---

### Post by yunqi on 2007-05-30
I just finished instal lthe  newest Ubuntu without other operation system, but can't enter Xwindows. How can I start Xwindows?

---

### Post by blazercist on 2007-05-30
you installed the server version?  

sudo apt-get install ubuntu-desktop  #this is for gnome
sudo apt-get install kubuntu-desktop  #this is for kde
sudo apt-get install xubuntu-desktop  #this is for xfce

once its installed either reboot or type
startx
in console to start x windows - at least thats how you do it with gnome.

---

### Post by FuturePilot on 2007-05-30
For installing the desktop environments you should use aptitude instead of apt. Aptitude handles dependencies better and since these are big meta packages you'll need to be sure to catch all the dependencies.
So if you want Gnome
```
sudo aptitude install ubuntu-desktop
``` 
KDE
```
sudo aptitude install kubuntu-desktop
```
XFCE
```
sudo aptitude install xubuntu-desktop
```

---

### Post by yunqi on 2007-05-30
yes, I installed 6.06 sever, I will try these commands, thank you!

---

### Post by yunqi on 2007-05-30
when I download and finished, startx, it report no ~/.xsession file, then Xwindows shutdown, how can I do then please?

---

### Post by matey3 on 2008-01-29
> **blazercist said:**
> you installed the server version?  

sudo apt-get install ubuntu-desktop  #this is for gnome
sudo apt-get install kubuntu-desktop  #this is for kde
sudo apt-get install xubuntu-desktop  #this is for xfce

once its installed either reboot or type
startx
in console to start x windows - at least thats how you do it with gnome.

Thanks for the info.

I tried to do all 3 commands but got errors so I mounted cdrom then tried it (with ubuntu server CD 7.04 in it) it again returned errors saying the packages are not available! then says xinit is not installed. so i did apt-get for xinit it again gave me error E: Package xinit has no installation candidate

so I am stuck with no X!? :(

linux used to come already with one X license (free) all u had to do was type X or Xconfigurate or startx etc ,.(been away from unix since 97 sorry) can anyone shed more light on this subject.
thanks in advance

---

### Post by kd2323 on 2008-01-29
Usually when I have a problem starting Xserver I use dpkg -reconfigure xserver-xorg and re-detect the vid card and whatnot. That might not be the case with you. Have you downloaded all of the standard updates before installing X? There might be an xserver update you need. I am just going through the simple solutions before I could offer a real one.

---

### Post by mali2297 on 2008-01-29
> **matey3 said:**
> Thanks for the info.

I tried to do all 3 commands but got errors so I mounted cdrom then tried it (with ubuntu server CD 7.04 in it) it again returned errors saying the packages are not available! then says xinit is not installed. so i did apt-get for xinit it again gave me error E: Package xinit has no installation candidate

so I am stuck with no X!? :(

linux used to come already with one X license (free) all u had to do was type X or Xconfigurate or startx etc ,.(been away from unix since 97 sorry) can anyone shed more light on this subject.
thanks in advance

If you cannot get internet connection in ubuntu, I suggest that you use the alternate CD (download from another computer?). This [link]("http://www.psychocats.net/ubuntu/nox") might help.

> 
Do you have a graphical environment installed?
The first step requires you to have a software repository. In most cases, if you're connected to the internet, the commands given will use your internet connection. If you don't have an internet connection but do have the Ubuntu Alternate Installer CD, insert it in your drive and type

sudo apt-cdrom add

This will add the CD as a software package source since you can't get packages from the internet.

To make sure you have a graphical environment installed:

sudo aptitude update
sudo aptitude install ubuntu-desktop

If you didn't already have it installed, you'll notice Ubuntu downloading and installing a whole bunch of packages, either from the internet or from your CD.

If you did have it installed, you'll simply be told ubuntu-desktop is already the newest version.


By the way, why did you choose to install the server edition?

---

### Post by matey3 on 2008-02-04
well thanks a lot for all the info/how-to's etc. and sorry for late reply i miss my internet cuz i moved and have to use the line at work... any way

I was told to install the server on my new job to do backups etc. so i wanted to avoid typing so much and use the gui as shortcut in moving/copying files etc...
otherwise i dont really need the xwindows (still would be nice to have..).

and thanks to KD2323 for the reply. I did have a problem wih nvidia dislay driver once before but i'll try it again (I think you have to delete this hidden file in the tmp folder in order to re-config.. X0 or something? ) It will tell me which file..

thanks a lot!

---

