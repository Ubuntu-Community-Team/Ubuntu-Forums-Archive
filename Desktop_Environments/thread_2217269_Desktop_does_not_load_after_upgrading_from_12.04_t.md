---
title: "Desktop does not load after upgrading from 12.04 to 14.04 beta"
date: 2014-04-16
forum: Desktop Environments
---

### Post by Manoj_Kumar_Sakarw on 2014-04-16
I was using 12.04 LTS, Today I upgraded to 14.04 beta version. After the upgrade desktop does not load after entering username and password. Please help me...

---

### Post by Frogs Hair on 2014-04-16
Hello and Welcome 

Try selecting the old kernel at boot . This won't solve the problem, but may allow you to try some things from the desktop if the old kernel loads.  Post any messages if any you have seen as well.

---

### Post by deadflowr on 2014-04-17
> **Manoj_Kumar_Sakarw said:**
> I was using 12.04 LTS, Today I upgraded to 14.04 beta version. After the upgrade desktop does not load after entering username and password. Please help me...

Is it hanging at the login screen after you type and enter the password?
Like you type the password and then it leaves you a blank password field, but nothing else happens.

Or does the screen just go black.

If it's the former, then perhaps it's the issue of the package ubuntu-session not getting installed correctly.
Older versions of Ubuntu had unity's session in the package gnome-session.
But for 14.04, they made a new one called ubuntu-session.
You might try this
press ctrl+alt+F1(or F2-F6)
enter your name and password.
Then try installing the ubuntu-session package
```
sudo apt-get update && sudo apt-get install ubuntu-session
```
then 
```
sudo restart lightdm
```
if it doesn't load, maybe a full reboot and see...
It's all guess work though.

If though it's the latter, and the screen is just blank then we'll have to get into some deeper stuff, maybe.

---

### Post by Manoj_Kumar_Sakarw on 2014-04-17
This is what I see after login

[ATTACH=CONFIG]252133[/ATTACH]

I can see two kernel versions on boot screen and selected the older one to boot with but that did not work.

After that I tried 
```
sudo apt-get update && sudo apt-get install ubuntu-session
```

```
sudo restart lightdm
```

Above commands also could not solve the issue.

---

### Post by deadflowr on 2014-04-17
It seems you're hanging at the login screen, like it's trying to load the desktop.
Perhaps a reinstall of the desktop might help
```
sudo apt-get install --reinstall ubuntu-desktop
```
or
```
sudo apt-get install --reinstall unity
```

I also think it might be a compiz issue, maybe.
Or something is preventing compiz from loading.

---

### Post by Manoj_Kumar_Sakarw on 2014-04-17
I tried both the commands but its the same story. 
Should I wait for the Final Ubuntu 14.04 release?

---

### Post by deadflowr on 2014-04-17
The way that it's hanging for you, to me, seems like compiz isn't loading correctly.
Maybe a reset is in order.
Look over this
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

See if that helps.

---

### Post by fatemeh2 on 2014-06-30
I have the same problem.
After upgrading to ubuntu 14.04 desktop did not load but it loaded using the old kernel. I formatted my hard drive and reinstalled ubuntu but the desktop still does not load.

---

### Post by MibunoOokami on 2014-08-19
Has anyone found a solution to this problem? My second machine which I decided to upgrade has this exact same problem.
I followed the instructions in this thread and in this one [here]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html") but when I got to this part 
```
dconf reset -f /org/compiz/
```

I get an error message. ```
error: Cannot autolaunch D-Bus without X11 $DISPLAY
``` I have no idea what to do from here.

EDIT:The only kernel present only says Ubuntu or Advanced options for Ubuntu.
I've since followed the instructions in a post in this [thread]("http://askubuntu.com/questions/476930/ubuntu-desktop-does-not-load") but it was the same story when trying to log into gnome.

>  I have had the exact same problem since yesterday as well. To fix it I  had to install gnome-panel then run unity reset through unity tweak  tools.
  Ctrl + Alt + F1,
  sudo apt-get install gnome-panel
  sudo mv ~/.Xauthority ~/.Xauthority.backup
  Reboot and select gnome on login.
  once logged in open a terminal Ctrl + T
  sudo apt-get install unity-tweak-tool
  unity-tweak-tool --reset-unity
  log out and log in again using unity this time and that fixed it for me.
     


I installed unity-tweak-tool via the ctrl+alt+F1 screen and tried launching it but ended up with an infinite looping of ```
error: Cannot autolaunch D-Bus without X11 $DISPLAY
```

---

### Post by MibunoOokami on 2014-08-21
Bump. ):p

---

### Post by satnelav on 2014-09-07
Same problem.

---

### Post by mail-wz6bkyhu4 on 2014-09-08
I also have the same issue. After login, desktop will not load.

---

### Post by tschill on 2014-10-25
I had the same problem today after my upgrade, just a blank wallpaper and the mouse pointer was visible. I could not even open a terminal.

 I noticed that the login screen was in low resolution, so I assumed it was a problem with the graphic card driver. Mine is a Radeon HD 3470. I removed the installed fglrx driver with

```
sudo apt-get remove fglrx*
```

A restart brought up a high resolution login screen and revived the desktop, no other problems so far. Installation of the open source driver with

```
sudo apt-get install xserver-xorg-video-ati
``` 

was not necessary for me, it was already installed. 

Nvidia card owners might want to have a look [here]("http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login").

---

