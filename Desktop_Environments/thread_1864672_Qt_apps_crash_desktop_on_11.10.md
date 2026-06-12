---
title: "Qt apps crash desktop on 11.10"
date: 2011-10-19
forum: Desktop Environments
---

### Post by davemar on 2011-10-19
I've just installed 11.10 and have found a serious problem. Every time I start a Qt based application (ffado-mixer was the first one I tried) it crashes the desktop at some stage and send me back to the login page.

This is in both Unify2D and Gnome classic, so it does not appear to be desktop style dependent. There appears to be something in Qt that causes the crashing, but it is difficult to trace as it falls over right away taking out the whole desktop.

So far I've tried these (which I assume all use Qt):
ffado-mixer: crashes split second after starting.
qjackctl: crashes when a pull-down menu is selected.
some very simple old qt app I wrote: crashes when selecting a menu item.

What on earth is causing all this?

---

### Post by ppsalama on 2011-10-19
Hello.
I think that your problem is like the mine one [as I wrote yesterday]("http://ubuntuforums.org/showthread.php?t=1864238") in a post in this forum. Look my problem:[INDENT][I]Hello.
first... sorry for my english...
I have this problem:
Just after installing Skype and/or qbittorrent, when I run it, my Unity 3D session crash (with an ugly screen effect) and get back to gdm in order to login again.
I don't know why it happens in my clean installation of ubuntu 11.10. In natty both worked fine.
Probably you need more info about my PC. From natty to oneiric I only got problems changing nouveau drivers for propietary nvidia drivers (finally I got it works fine -I suppose it-).

I would like Skype and qbittorrent work again.
Thank you very much for your help.
Best regards
[/I]
[/INDENT]It happens like you: when I pull down a button in any menu.
I hope somebody can help us.
best regards

---

### Post by davemar on 2011-10-19
I tried recompiling Qt from source to see if that improved things, and it's still the same. 

There's got to something very fundamentally wrong for the desktop to crash so easily.

---

### Post by ppsalama on 2011-10-19
I have confirm in my PC, as you say, that it is a problem with QT: VLC also crash my desktop :(.
I'll read this thread for any solution.
Best regards

---

### Post by ppsalama on 2011-10-22
Installing all libqt4-* does'nt solve the problem :(

---

### Post by davemar on 2011-10-26
I've narrowed to down to a problem with the nvidia drivers. I changed my xorg.conf file so it doesn't use the nvidia drivers anymore, and the crashing disappears and the Qt apps run fine.

Has anyone else experienced problems with nvidia drivers under 11.10?

---

### Post by ppsalama on 2011-10-26
Hi,.. davemar.
As well I use nvidia drivers in 11.10. Please, can you tell me how you change your xorg.conf file? Now you use the nouveau drivers?
Thank you very much

---

### Post by ronniew on 2011-12-02
Same here. Any Qt based app either crashes the desktop when trying to open or crashes the desktop if trying to access one of the programs menus if it does open. 

Any help is appreciated.

---

### Post by lemanh on 2012-01-29
Exactly the same here. After launching Skype (or for example Google Earth) x-server-crash occurs, that's pretty bad. So, any help is still welcome.

Nvidia Drivers installed via these commands:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

sudo apt-get install nvidia-current

([http://www.hecticgeek.com/2011/10/how-to-install-latest-proprietary-nvidia-drivers-in-ubuntu-11-10-oneiric-ocelot/](http://www.hecticgeek.com/2011/10/how-to-install-latest-proprietary-nvidia-drivers-in-ubuntu-11-10-oneiric-ocelot/))

Is there any solution of this problem?

---

### Post by sakaal on 2012-02-05
I seem to be having this same issue with nVidia 2000M.

If you can confirm that this bug affects you in the Launchpad, it might help getting it fixed sooner:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/927288](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/927288)

---

### Post by hussam_nasir on 2012-04-29
Solution to this problem seems to be very simple which i found after struggling with the problem for a year.

This is on the assumption that all of you have used the nvidia-settings utility to generate your xorg.conf file.

Edit the /etc/X11/xorg.conf file and comment out or delete the below shown lines

Section "Files" 
FontPath "unix/:7100" 
EndSection

Save the file and restart GDM or lightDM which ever is your login manager using

/etc/init.d/gdm restart

or /etc/init.d/lightdm restart

Now all of the QT applications like virtualbox and skype should not crash X

---

### Post by NormInNorman on 2012-08-25
> **hussam_nasir said:**
> Solution to this problem seems to be very simple which i found after struggling with the problem for a year.

This is on the assumption that all of you have used the nvidia-settings utility to generate your xorg.conf file.

Edit the /etc/X11/xorg.conf file and comment out or delete the below shown lines

Section "Files" 
FontPath "unix/:7100" 
EndSection

Save the file and restart GDM or lightDM which ever is your login manager using

/etc/init.d/gdm restart

or /etc/init.d/lightdm restart

Now all of the QT applications like virtualbox and skype should not crash X
Holy crap! Thank you!

I just did a clean install last week and since then I've installed the latest nvidia drivers, cinnamon, vlc's blu-ray support, and makemkv on top of getting the blue faces out of my flash movies. I was starting to think that was too much to troubleshoot at once and I figured I was going to have to reformat everything again. This fixed it!

---

