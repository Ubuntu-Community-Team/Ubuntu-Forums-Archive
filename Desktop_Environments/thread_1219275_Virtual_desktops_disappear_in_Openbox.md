---
title: "Virtual desktops disappear in Openbox"
date: 2009-07-21
forum: Desktop Environments
---

### Post by MobileDev on 2009-07-21
I use Gnome as my main desktop with Compiz, Metacity, and I recently installed Openbox. I like the clean appearance of Openbox and use it when running resource intensive stuff, like Virtual Box and some games, or when I have LOTS of apps open (usually during troubleshooting). Here's the problem:

When switching from Compiz to Openbox, I LOSE MY VIRTUAL DESKTOPS. Instead of 4, I only have 1. Now for the kicker: If I switch from Metacity to Openbox, I KEEP ALL 4 DESKTOPS. 

I am using the --replace option to switch between the three and it happens when I use fusion-icon too.

I am running Ubuntu 9.04 64-bit, but the same thing happens with Xubuntu (using Xfce, not Gnome) and Crunch Bang (with modified LXDE session)

What is the problem here and how do I fix it?

---

### Post by exjinn on 2009-10-05
I have this same issue though I have not tried switching from metacity to openbox. only from compiz or when logging in via GDM.

I am running 9.10 beta on Crunchbang.

---

### Post by jeffus_il on 2009-10-19
The problem is caused by the new gdm in 9.10
I installed xdm and during the install chose it as the default display manager
It's ugly but it works!

---

### Post by bkann on 2009-11-05
I have a similar problem, but I don't switch between environments.  I just run the Gnome/Openbox combo.

I lost my desktops at upgrade to 9.10 and tried moving to XDM (which I've done quite successfully in the past), but I cannot get it to invoke the Gnome/Openbox combo that I had before the upgrade.

For what it's worth, I found that if I go into obconf and adjust the number of desktops and then adjust them back, they all reappear.  For example, if I run 5 desktops, I'll go into obconf and specify 6 and then adjust it back to 5, then they all reappear.  They stick around until I reboot.

---

### Post by cnbiz850 on 2011-08-20
This is still unsolved under 11.04 64bits.  I run Openbox with Xfce and the number of desktops becomes 1 when I login.  I can not change it from the workspace switcher plugin's workspace setting on the xfce4-panel.  As bkann mentioned, I can only change it in obconf, but it does not get saved and I have to do it every time after I login.  

Why still no solution?

---

### Post by dodgefan on 2011-11-27
this is not specific to openbox. i am running debian testing with xfce4 and after i run fusion-icon, i loose two of my four virtual desktops and cannot change it back. i can set the number of desktops in the settings to 4 but it changes nothing

anyone?


***EDIT, found the solution here
[http://ubuntuforums.org/showpost.php?p=7856552&postcount=4](http://ubuntuforums.org/showpost.php?p=7856552&postcount=4)

---

