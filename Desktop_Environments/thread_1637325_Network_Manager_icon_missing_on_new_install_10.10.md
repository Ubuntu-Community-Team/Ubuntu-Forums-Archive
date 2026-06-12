---
title: "Network Manager icon missing on new install 10.10"
date: 2010-12-04
forum: Desktop Environments
---

### Post by iain gordon on 2010-12-04
Hi my first post
Just installed (clean install) of Ubuntu 10.10 on an old desktop pc. The network manager icon is missing,:sad:

Buy the way i had to run install from safemode. As I was having problems with login in, I kept trying to login in to the normal desktop but Ubuntu  kept thinking about it  for approximetly ten seconds and then asking me to login in again repeatedly.

however when i switch to guest user on the guest desktop the network manager icon appears. I have used this icon to enter a mobile broadband account and to connect up to and down load all updates surf etc.:D

Read a number posts and find this problem with the network manager icon are quite common.

On the main (problem) desktop i have
Tried installed a new panel but unable to add the notification area can add other icons
Tried adding the notification area to the old panel get brief white flash on panel
Removed the other icons and reinstalled these icons and tried adding the notification area.
looked at "!nm-applet-sm-disable" appears ok

Thanks time

Iain

---

### Post by CaronMargarete on 2010-12-04
> **iain gordon said:**
> Hi my first post

Read a number posts and find this problem with the network manager icon are quite common.

On the main (problem) desktop i have
Tried installed a new panel but unable to add the notification area can add other icons
Tried adding the notification area to the old panel get brief white flash on panel
Removed the other icons and reinstalled these icons and tried adding the notification area.
looked at "!nm-applet-sm-disable" appears ok

Thanks time

Iain

Iain, I've got the same issue- driving me mental trying to figure it out. 

At first I thought I was missing something in the Synaptic Package so I tried to reinstalled the network-manager-gnome, the net connected again but the icon still isn't visible, irrespective of doing the same things as you did above. Although, what did you do to look at "!nm-applet-sm-disable" and what did you expect to see because I haven't tried this yet?

Thanks.

---

### Post by iain gordon on 2010-12-04
Hi Caron

found the alt+f2 then type in "nm-applet" from the thread below
iain

[http://ubuntuforums.org/showthread.php?t=1633127&highlight=network+manager+icon+missing](http://ubuntuforums.org/showthread.php?t=1633127&highlight=network+manager+icon+missing)

---

### Post by CaronMargarete on 2010-12-04
> **iain gordon said:**
> Hi Caron

found the alt+f2 then type in "nm-applet" from the thread below
iain

[http://ubuntuforums.org/showthread.php?t=1633127&highlight=network+manager+icon+missing](http://ubuntuforums.org/showthread.php?t=1633127&highlight=network+manager+icon+missing)

Hmmm tried "nm-applet" and as per the link "nm-applet &" and neither have worked. Am I meant to restart my laptop?

---

### Post by iain gordon on 2010-12-08
Hi Caron

I still have the network manager icon problem and if you find a resolution do please inform me.

I am not sure if you need to restart your laptop for the  "nm-applet &" to take affect. I am a complete new user of Ubuntu and you have probably tried it by now.

If you look under the system tab then preferences then startup applications you can scroll too and highlight network manager click on edit and once again you should see an entry for "nm-applet --sm-disable". In another thread it was mentioned to check that this was entered, but i do not no the detail on why.

How about using Synaptic package manager (under system tab administration) to unistall Network Manager and then reinstall to see if this fixes the problem? I have yet to give this a try.

I am just getting used to Ubuntu and find a number of things like some desktop settings are not stored after powering down, so at the moment not sure what going on exactly.

Iain

---

### Post by sml on 2011-01-15
no luck for me with alt+f2 and nm-applet and nm-applet & 

any other ideas?

what is progress from your end since early December?

---

### Post by iain gordon on 2011-01-15
Hi sml
 
On another PC i did not have this problem with Ubuntu (when run from just cd let alone install), so i decided not persue it any futher.  The problem PC is old and was cheap model i also had other problem with the display with Ubuntu the desktop did not all show on the monitor and would scroll left and right. So i never got bottom of network manager icon in my situation. But happy to say it appears to work on another PC which is 9 years old, but i am yet to install and use it regularly.
 
Iain

---

### Post by grahammechanical on 2011-01-15
CaronMargarete

You do need to reboot. Configuration files are often read at boot time. Change one and a reboot may be necessary.

Make sure that Network Manager is in the list of Startup Applications. System>Preferences.

To get the network manager icon in the top panel, click on the panel and select Add to Panel and look for Notification Area. Select it and click Add.

Regards

---

### Post by ericrichards420 on 2011-01-15
right click on the panel and go to add to panel. add "Notification Area" that should work.

---

