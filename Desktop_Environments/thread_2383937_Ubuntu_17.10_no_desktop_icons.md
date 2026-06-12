---
title: "Ubuntu 17.10 no desktop icons"
date: 2018-01-31
forum: Desktop Environments
---

### Post by goodstuff9 on 2018-01-31
Ubuntu 17.10 (xorg), gnome 3.26.2.  
After installing 17.10, there are no icons on the desktop.  I am unable to add anything to the desktop.  
In the tweak tool all five switches for icons on the desktop are on.  
In dconf I see this:  
org.gnome.nautilus.desktop volumes-visible true
org.gnome.desktop.background show-desktop-icons true
org.gnome.desktop.draw-background true
Any ideas on how I can fix this problem?  I find nothing online that will help me.

---

### Post by Frogs Hair on 2018-01-31
Have logged out and back in since adding the icons ? You shouldn't have to do this, but I'd start with that.

---

### Post by goodstuff9 on 2018-01-31
Yes, I have tried that, rebooting as well, still the same problem.

I want to be clear, though.....  You asked if I have logged out and back in "since adding the icons".  Not sure what you meant by that, since my question/problem is that I cannot, and have never been able to add any icons to the desktop at all.

---

### Post by ajgreeny on 2018-01-31
What do you see from command ```
ls Desktop
```
Are there any icons (.desktop files) showing, or are the icons you want something else and not launchers?

---

### Post by mc4man on 2018-01-31
You could always try this, may shake something loose
```
mv .config/dconf/user .config/dconf/user.bak && reboot
```
To restore the .bak if desired - ```

rm /.config/dconf/user && mv .config/dconf/user.bak .config/dconf/user && reboot
```

---

### Post by goodstuff9 on 2018-01-31
> **mc4man said:**
> You could always try this, may shake something loose
```
mv .config/dconf/user .config/dconf/user.bak && reboot
```
To restore the .bak if desired - ```

rm /.config/dconf/user && mv .config/dconf/user.bak .config/dconf/user && reboot
```


I ran these commands, nothing changed.

---

### Post by goodstuff9 on 2018-01-31
> **ajgreeny said:**
> What do you see from command ```
ls Desktop
```
Are there any icons (.desktop files) showing, or are the icons you want something else and not launchers?


I have a bunch of desktop files in the Desktop directory, but nothing appears on the actual desktop.

---

### Post by mc4man on 2018-02-01
> **goodstuff9 said:**
> I have a bunch of desktop files in the Desktop directory, but nothing appears on the actual desktop.

Try creating or adding a text file or folder to your Desktop folder, see if it shows up

---

### Post by goodstuff9 on 2018-02-01
> **mc4man said:**
> Try creating or adding a text file or folder to your Desktop folder, see if it shows up

I can add them to the Desktop directory, no problem.  Nothing appears on the desktop.

---

### Post by pablosquared on 2018-02-02
Open the Tweaks app and, under the Desktop tab, check the "Show Icons" setting, If it's off, you won't see any icons on the desktop. You cna pick and choose which ones to display.

---

### Post by pablosquared on 2018-02-02
More here:
[https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/](https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/)

---

### Post by goodstuff9 on 2018-02-02
> **pablosquared said:**
> Open the Tweaks app and, under the Desktop tab, check the "Show Icons" setting, If it's off, you won't see any icons on the desktop. You cna pick and choose which ones to display.

I had already done that.  I have the switch on to show icons on the desktop.  I also have on all the switches for the different folders listed.  Still does not work.

---

### Post by mc4man on 2018-02-02
> After installing 17.10, there are no icons on the desktop.  I am unable to add anything to the desktop.  

Was this an upgrade of 17.04 to 17.10? If so just do a fresh install of 17.10 or even 18.04-dev which is in better shape than 17.10 will ever be..

---

### Post by goodstuff9 on 2018-02-02
> **mc4man said:**
> Was this an upgrade of 17.04 to 17.10? If so just do a fresh install of 17.10 or even 18.04-dev which is in better shape than 17.10 will ever be..

Upgrade from 17.04.  

I was hoping to avoid doing what you suggest, because unfortunately Ubuntu doesn't give me a way to know the applications I've installed, including those from PPAs, etc., nor does it give me an easy way to know what I've installed from SNAP versus debian, etc., nor does it enable me to know all the settings I've set for all the various applications, nor do I have a way to recall all the configuration files I've had to manually create for things like fstab, samba, etc.  

But, if there is no other way, I realize this may be what I'll have to do.

---

### Post by mc4man on 2018-02-02
> **goodstuff9 said:**
> Upgrade from 17.04.  

I was hoping to avoid doing what you suggest, because unfortunately Ubuntu doesn't give me a way to know the applications I've installed, including those from PPAs, etc., nor does it give me an easy way to know what I've installed from SNAP versus debian, etc., nor does it enable me to know all the settings I've set for all the various applications, nor do I have a way to recall all the configuration files I've had to manually create for things like fstab, samba, etc.  

But, if there is no other way, I realize this may be what I'll have to do.
Well...
Upgrading from an install that used ppa's can cause issues, in many cases use of ppa-purge before the upgrade is required.
As far as snap vs. deb, just open Disks > any squash filesystem point to a snap. Or look in /snap directory.
Settings & config files are sometimes the cause of issues in a release upgrade.

In the case of 17.04 > 17.10 there were major interface, ect. changes, this lessens chance of a good upgrade. Throw in that there was virtually no testing of the 17.04 > 17.10 upgrade process.. 
Also consider that if on 17.10 you'll need to go thru this again when 17.10 goes EOL in July or thereabouts. So the strong odds are you'll have to bite the fresh install bullet sooner or later anyway.
If it was me I'd figure on a fresh install of 18.04, when is up to you.

If inclined create a new user, log into that user & see if it inherits any of your current issues. If not than you can figure your troubles reside somewhere in your Home folder which can be systematically deleted to resolve.

---

### Post by goodstuff9 on 2018-02-02
> **mc4man said:**
> Well...
Upgrading from an install that used ppa's can cause issues, in many cases use of ppa-purge before the upgrade is required.
As far as snap vs. deb, just open Disks > any squash filesystem point to a snap. Or look in /snap directory.
Settings & config files are sometimes the cause of issues in a release upgrade.

In the case of 17.04 > 17.10 there were major interface, ect. changes, this lessens chance of a good upgrade. Throw in that there was virtually no testing of the 17.04 > 17.10 upgrade process.. 
Also consider that if on 17.10 you'll need to go thru this again when 17.10 goes EOL in July or thereabouts. So the strong odds are you'll have to bite the fresh install bullet sooner or later anyway.
If it was me I'd figure on a fresh install of 18.04, when is up to you.

If inclined create a new user, log into that user & see if it inherits any of your current issues. If not than you can figure your troubles reside somewhere in your Home folder which can be systematically deleted to resolve.

Dude!!!!!  You are the man!!!!!  I created a second user, and that user does NOT have this problem.  

Question:  How do I determine what it is in my home directory that is causing the problem?

---

### Post by mc4man on 2018-02-03
Assuming the the replacement of .dconf/user had no good affect try,
Open file manager  > showing hidden files, browse to /home/the new user (something like Other Locations > Computer, ect.
Open another file manager window at your home folder, also showing hidden

Rename your .bashrc to .bashrc.bak, then copy the .bashrc from the new user & paste into your home folder.
Rename your .config to .config.bak, then copy the .config folder from the new user & paste into your home folder

Immediately after the  ^ log out & back into your user, see if anything changed.

---

### Post by goodstuff9 on 2018-02-03
> **mc4man said:**
> Assuming the the replacement of .dconf/user had no good affect try,
Open file manager  > showing hidden files, browse to /home/the new user (something like Other Locations > Computer, ect.
Open another file manager window at your home folder, also showing hidden

Rename your .bashrc to .bashrc.bak, then copy the .bashrc from the new user & paste into your home folder.
Rename your .config to .config.bak, then copy the .config folder from the new user & paste into your home folder

Immediately after the  ^ log out & back into your user, see if anything changed.

I did what you said, that solved this (and another) problem.  THANK YOU!!

---

### Post by portnoy256 on 2018-04-07
Maybe usefull for other users with the same problem: after an update o reinstall (or a system language change) the system folders could change name [in my case from "Desktop" to "Scrivania" switching from English (1033) to Italian (1040)].
In this case just move your files from older dir to new (and rebuild thumb cache if you like)! :popcorn:

Lorenzo

---

