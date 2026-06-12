---
title: "Synaptics touchpad on Vostro V13 with 9.10"
date: 2010-02-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by brieweb on 2010-02-05
What do I need to do to get this synaptics touchpad gesturing working for my Vostro V13? I installed Karmic. I see that there is no static xorg.conf file. I thought the days of configuring X were in the past, but once again they seem to have come back to haunt me.

---

### Post by louisiana84 on 2010-03-13
It would be a shame if we don't find a fix for this issue. This machine really rocks Ubuntu 9.10.

---

### Post by bobcollard on 2010-03-15
Try installing gpointing-device-settings in Synaptic Package Manager.  It has controls and settings for synaptic Touchpads.  Put it in startup applications so you have control at bootup.

---

### Post by jrssystemsnet on 2010-03-18
> **brieweb said:**
> What do I need to do to get this synaptics touchpad gesturing working for my Vostro V13? I installed Karmic.

```
user@box:~$ sudo apt-get install gsynaptics
```

Then you'll have a "Touchpad" applet in the System menu.

---

### Post by bobcollard on 2010-03-18
> **jrssystemsnet said:**
> ```
user@box:~$ sudo apt-get install gsynaptics
```Then you'll have a "Touchpad" applet in the System menu.
Gnome in Ubuntu 9.10 has a problem with gsynaptics, besides which, the site which has gsynaptics recommends gpointing-device-settings as the current version.  See this link:
[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

---

### Post by jrssystemsnet on 2010-03-18
> **bobcollard said:**
> Gnome in Ubuntu 9.10 has a problem with gsynaptics, besides which, the site which has gsynaptics recommends gpointing-device-settings as the current version.  See this link:
[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/) Well I'll be dipped in it - I hadn't personally noticed any issues with Karmic and gsynaptics, but thanks for the notice about gsynaptics being deprecated in favor of gpointing-device-settings; I had no idea.

:: trundles off to update some FAQs ::

---

### Post by bobcollard on 2010-03-18
> **jrssystemsnet said:**
> Well I'll be dipped in it - I hadn't personally noticed any issues with Karmic and gsynaptics, but thanks for the notice about gsynaptics being deprecated in favor of gpointing-device-settings; I had no idea.

:: trundles off to update some FAQs ::
I was using gsynaptics for awhile before I found out.  You're welcome.

---

### Post by jrssystemsnet on 2010-03-18
OK, so a note to the OP:

you should **sudo apt-get install gpointing-device-settings**, but there are some rough edges... notably, it doesn't leave you with a menu item to get to it.

System -> Preferences -> Main Menu; navigate to System -> Preferences, click New Item, set the Command to /usr/bin/gpointing-device-settings, the Name to Pointing Devices, and take your pick of the three icons in /usr/share/gpointing-device-settings/icons.  That will give you a Menu item (and a Launcher icon to go with it, if you're using Netbook Remix).

---

### Post by bobcollard on 2010-03-18
> **jrssystemsnet said:**
> OK, so a note to the OP:

you should **sudo apt-get install gpointing-device-settings**, but there are some rough edges... notably, it doesn't leave you with a menu item to get to it.

System -> Preferences -> Main Menu; navigate to System -> Preferences, click New Item, set the Command to /usr/bin/gpointing-device-settings, the Name to Pointing Devices, and take your pick of the three icons in /usr/share/gpointing-device-settings/icons.  That will give you a Menu item (and a Launcher icon to go with it, if you're using Netbook Remix).
Use the command line or create a Launcher on your desktop.
```
sudo apt-get gpointing-device-settings
```Also put it in your startup applications using the name of the program for the command and Touchpad Control for the Description

---

### Post by rpared01 on 2010-03-18
Hey thanks for the info. i just got my V13 two days ago and im using gpointing now, this rocks.

---

### Post by viniosity on 2010-03-28
I installed gpointing and I can get vertical scrolling working, but only if I hold down the mouse button.  Is there any way to enable it *without* requiring a mouse-button press?

---

### Post by bobcollard on 2010-03-28
> **viniosity said:**
> I installed gpointing and I can get vertical scrolling working, but only if I hold down the mouse button.  Is there any way to enable it *without* requiring a mouse-button press?
I just tested mine, it works fine on the right side and I never hold down the button. Don't know if this is a Vostro problem or maybe someone else can help?  My Dell is nearly 8 months old.

---

