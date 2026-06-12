---
title: "How to switch between different versions of the Ubuntu desktops"
date: 2011-12-06
forum: Desktop Environments
---

### Post by unckybob on 2011-12-06
I am running ubuntu 11.04 on my old laptop. I just got a new laptop and installed 11.10. I've noticed that the desktops act differently. How can I determine what desktop I am using on my old computer, and how can I switch to that desktop on my new computer? 

I'm new to this, please help.

---

### Post by bluexrider on 2011-12-06
> **unckybob said:**
> I am running ubuntu 11.04 on my old laptop. I just got a new laptop and installed 11.10. I've noticed that the desktops act differently. How can I determine what desktop I am using on my old computer, and how can I switch to that desktop on my new computer? 

I'm new to this, please help.

11.10 incurred the Unity desktop 

I doubt you have Unity on 11.04

---

### Post by bluexrider on 2011-12-06
Forgot,

to switch back to that type of desktop you would need to do this:

sudo apt-get install gnome-session-fallbackfollow this tutorial

[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

---

### Post by unckybob on 2011-12-06
Thanks so much for that.

---

### Post by unckybob on 2011-12-06
I used your link and it works, except there is no "System" menu in the upper left hand corner of the desktop (right next to "Applications" and "Places".

---

### Post by cortman on 2011-12-06
Sorry, that's part of Gnome fallback. No more System. You can Alt + right click on the panel, select "add to panel" and add the classic Gnome menu if you want, which will give you your power options, etc.
The system config stuff is in the Applications menu.

---

### Post by matt3839 on 2011-12-06
> **unckybob said:**
> I used your link and it works, except there is no "System" menu in the upper left hand corner of the desktop (right next to "Applications" and "Places".

Same thing happened to me; sadly, it may be a new permanent change in GNOME 3. It's extremely different from the 2.x series.

There is a [GTK3-compatible fork of GNOME 2.x]("http://mate-desktop.org/") in development, but the current PPA is not going to be maintained for long.

---

### Post by Frogs Hair on 2011-12-06
You can enable the Linux Mint repository and install mate . [http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/)

---

### Post by Krytarik on 2011-12-07
> **Frogs Hair said:**
> You can enable the Linux Mint repository and install mate . [http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/)
Nice tip, Frogs Hair! Didn't know of that till now. Noted. :D

---

### Post by unckybob on 2011-12-08
Thanks Cortman. Can you tell me how to adjust fonts. Like in the window titles and panels?

---

### Post by unckybob on 2011-12-08
Can you tell me how to change the fonts in the window titles and panels?

---

### Post by bluexrider on 2011-12-08
> **Frogs Hair said:**
> You can enable the Linux Mint repository and install mate . [http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/)

i suppose if you wanted to give it a shot. I for one have been there and done that and made the return trip home.

---

### Post by unckybob on 2011-12-09
I found out you can make a lot of settings by installing the gnome-tweak-tool. At a terminal type:

# sudo apt-get install gnome-tweak-tool

Once it is installed you can find it at:

"Applications" -> "Other" -> "Advanced Settings"

Thanks for the help guys.

---

### Post by LandisTwo on 2011-12-29
> **bluexrider said:**
> Forgot,

to switch back to that type of desktop you would need to do this:

sudo apt-get install gnome-session-fallbackfollow this tutorial

[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

thank you.
Landis

---

### Post by LandisTwo on 2011-12-29
logout and click the 'gear' and choose another version .. ?

Landis.

---

