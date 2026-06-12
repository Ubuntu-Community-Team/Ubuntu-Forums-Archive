---
title: "Disable Tap-to-Click"
date: 2010-03-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bender2k14 on 2010-03-02
I have spent half a day trying to disable tap-to-click with no luck.  Although I found many solutions that worked for others, nothing has worked for me.

I have Ubuntu 9.10 and a Dell Mini 10.  How can I disable tap-to-click on my touchpad?

---

### Post by bobcollard on 2010-03-02
> **Bender2k14 said:**
> I have spent half a day trying to disable tap-to-click with no luck.  Although I found many solutions that worked for others, nothing has worked for me.

I have Ubuntu 9.10 and a Dell Mini 10.  How can I disable tap-to-click on my touchpad?
Either in Synaptic Package Manager or Terminal install "gsynaptics"  It is a touchpad control that is very versatile.  For Terminal type "sudo apt-get install gsynaptics" (without quotes)  Then put it in your Startup Applications.  You will have the choice every time you reboot to use it or not.  I use it sometimes when I use a USB mouse to shut it off or to change the settings for sensitivity.

---

### Post by jpl888 on 2010-03-02
Or alternatively you could just go into System -> Preferences -> Mouse -> Touchpad and untick "enable clicks with mousepad". 

See attached screen shot.

---

### Post by bobcollard on 2010-03-02
> **jpl888 said:**
> Or alternatively you could just go into System -> Preferences -> Mouse -> Touchpad and untick "enable clicks with mousepad". 

See attached screen shot.
Hmn, I thought that was for the mouse pad keys.

---

### Post by jpl888 on 2010-03-02
It works for me on a Dell Inspiron 1750 and Dell Mini 10V anyway.

---

### Post by bobcollard on 2010-03-02
> **jpl888 said:**
> It works for me on a Dell Inspiron 1750 and Dell Mini 10V anyway.
Okay, hope the OP (Original Poster) reads this.  I'm not using Gnome and it is not available in Xubuntu.  Thanks, I'll pass this along.

---

### Post by Bender2k14 on 2010-03-02
> **bobcollard said:**
> Either in Synaptic Package Manager or Terminal install "gsynaptics"  It is a touchpad control that is very versatile.  For Terminal type "sudo apt-get install gsynaptics" (without quotes)  Then put it in your Startup Applications.  You will have the choice every time you reboot to use it or not.  I use it sometimes when I use a USB mouse to shut it off or to change the settings for sensitivity.

gsynaptics does look like a solution, but I get the following error message:
> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

> **jpl888 said:**
> Or alternatively you could just go into System -> Preferences -> Mouse -> Touchpad and untick "enable clicks with mousepad". 

See attached screen shot.

My gnome-mouse-properties menu (System->Preferences->Mouse) does not have a touchpad tab.  See the attached screenshot.

---

### Post by jpl888 on 2010-03-02
What is the hardware?

i.e. can you post output of "lspci".

It seems strange I was certainly able to use the touch pad tab out of the box as it were.

---

### Post by bobcollard on 2010-03-02
> **Bender2k14 said:**
> gsynaptics does look like a solution, but I get the following error message:




My gnome-mouse-properties menu (System->Preferences->Mouse) does not have a touchpad tab.  See the attached screenshot.
Use Synaptic Package Manager and remove "gsynaptics" and install "gpointing-device-settings"

---

### Post by ExcessPhase on 2011-10-29
> **bobcollard said:**
> Use Synaptic Package Manager and remove "gsynaptics" and install "gpointing-device-settings"


I did this. I even installed synaptic package manager to "get to "gpointing-device-settings". 
It is installed.
What now? The mouse settings entry in system settings still does not allow to switch off the tap-to-click.

BTW -- touch-on-tap is as stupid as a "full-throttle-on-touch-on-steering-wheel"

---

### Post by bobcollard on 2011-10-29
> **ExcessPhase said:**
> I did this. I even installed synaptic package manager to "get to "gpointing-device-settings". 
It is installed.
What now? The mouse settings entry in system settings still does not allow to switch off the tap-to-click.

BTW -- touch-on-tap is as stupid as a "full-throttle-on-touch-on-steering-wheel"
Alt+F2 will open "Run"  Type in gpointing-device-settings and when it starts disable touchpad.  You can also put gpointing-device-settings in startup applications and have the option to make this setting as soon as you boot up.  The mouse settings are for the mouse.

---

### Post by cariboo on 2011-10-30
As things have changed quite a bit with the move to GTK-3 in Oneiric, solutions for older versions don't work. I'd suggest you start a new thread, specifying what version you are running, and what you've done so far. This thread is closed.

---

