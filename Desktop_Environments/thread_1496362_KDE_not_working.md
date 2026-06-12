---
title: "KDE not working"
date: 2010-05-29
forum: Desktop Environments
---

### Post by Hagar55 on 2010-05-29
I'm running lucid gnome on my laptop (Dell studio 1737).

Thanks to my ATI GPU I had to install the alternate version of xserver to let compiz work.
[http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/](http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/)

Now I tried installing the KDE destop enviremont, the install went just fine but when I try to log into KDE I see the startup screen for a second then everything goes dark.
It stays that way in the background i think the desktop is there because the mouse cursor is there, I can move it around but that's all.

Does KDE work differently and so can the different xserver be the cause of KDE not working ?

---

### Post by Hagar55 on 2010-05-30
I seem to have the same problem on my desktop (aging AMD Athlon System with an NVidea graphics card to the xserver isn't a factor here.

Anyone have an idea to why this isn't working ?
I know I could log into Karmic before I changed to Lucid on the desktop.

---

### Post by Hagar55 on 2010-05-30
For the dektop I went into synaptic and reinstalled the KDE desktop and it works now.

On the laptop however I looked both in synaptic and in the software centre and It seems I installed the necessary packeges.

I choose KDE in the login screen and I see the blue startup and the first icon appear, then all goes black and I only get the pointer of the mouse.

When I push the power button I get the Kubuntu log off screen and the computer shuts down just fine so I just don't get the GUI when I log into KDE.

When I go back into gnome all is fine.

Are there packages I need to check or are there commands in terminal that insure all is installed correctly.
I can find instructions on how to do it in Intrepid and in Karmic but nothing for lucid.

All help is appreciated.

---

### Post by phara0h1 on 2010-07-04
Hi I have the same problem. I changed the desktop environment from Gnome to KDE just to see what it was like - the programs I have set to automatically run at startup (emesene and transmission) appear but with no minimise, maximise, close buttons/bar at top and I can move my cursor, but everything else is a black screen.

I tried to restart and change it back to Gnome, but that option is now missing from the log in screen... :S

What do I do to get Gnome back?

*I'm on the windows partition atm, my laptop's not 'completely' useless but I still want to get back onto ubuntu.

---

### Post by lais on 2010-07-04
> **Hagar55 said:**
> I'm running lucid gnome on my laptop (Dell studio 1737).

Thanks to my ATI GPU I had to install the alternate version of xserver to let compiz work.
[http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/](http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/)

Now I tried installing the KDE destop enviremont, the install went just fine but when I try to log into KDE I see the startup screen for a second then everything goes dark.
It stays that way in the background i think the desktop is there because the mouse cursor is there, I can move it around but that's all.

Does KDE work differently and so can the different xserver be the cause of KDE not working ?

I think the changes you did to xserver is resulting in the KDE Plasma desktop crashing.

---

### Post by cavalier911 on 2010-07-04
> What do I do to get Gnome back?
Verify presence and path to gdm (gnome display manager)
```
whereis gdm
```
```
sudo nano /etc/X11/default-display-manager
```
change
```
/usr/bin/kdm
```
to this
```
/usr/sbin/gdm
```

I've heard if you have multiple display managers with 
kdm set as default in this example and run 
```
sudo dpkg-reconfigure kdm
```
A menu is presented to let you change the default back to gdm.

---

