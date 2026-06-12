---
title: "Changing default studio appearance to ubuntu default"
date: 2010-09-28
forum: Desktop Environments
---

### Post by debasishg on 2010-09-28
Hi,

I know this might seems abit nob... but need some help from you guys ... 

I was using ubuntu 10.04 till yesterday.. and due to hdd crash i have changed my hdd.

while looking for my installation disc, my wall-mate gives me this Ubuntu Studio dvd and instead of downloading a new one, i have installed the studio. at the first sight ... i am being a fond of studio version .. its really cool.

now, i am quite habituated with default appearance of ubuntu, i found studio appearance is quite unusual (for me, menu layouts, panel everything). 

I would like to know how do i change this default appearance like ubuntu default 10.04 appearance. I am attaching a screen-shoot of my friends desktop, he upgraded his ubuntu thru apptitude update.

eagerly waiting for your help.

---

### Post by hhh on 2010-09-28
Hi,

Ubuntu Studio is an official remix of the standard Ubuntu desktop geared towards multimedia enthusiasts. It has some significant differences in the software that is included and the artwork compared to the standard edition...
[http://ubuntustudio.org/LucidLynx](http://ubuntustudio.org/LucidLynx)
[https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio](https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio)

If you just want to change the wallpaper and system theme, you should be able to do that by navigating to System -> Preferences -> Appearance and making changes to the Theme and Background tabs. I think that in Lucid the option to change the login screen is hidden, but doesn't change anything except the login screen appearance.

If you want to revert to the standard desktop, try the instructions at the bottom of this page...
[https://help.ubuntu.com/community/UbuntuStudio/FAQ](https://help.ubuntu.com/community/UbuntuStudio/FAQ)

If that doesn't work for some reason, just install the standard desktop edition over the studio edition.

Hope that helps.

---

### Post by Forcecommander4 on 2010-09-29
Hey. Did you install Ubuntu Studio itself? I downloaded Ubuntu 10.04 and then downloaded the desktop files for Ubuntu Studio through synaptic file manager.

I decided to try removing the theme from Studio. I simply removed the packages when I typed in "ubuntustudio" and now I have the old look of Ubuntu 10.04. This might not work if you downloaded Ubuntu Studio itself instead of downloading the desktop files in synaptic.

Hopes it helps, sorry if it doesn't.
-Forcecommander

---

### Post by debasishg on 2010-09-29
thanks to you both ... actually i have installed from DVD and before that i have no idea abt studio version (only hunted few pages).

thru googling ... i have removed all themes and re-downloaded studio desktop,themes and wallpaper with icons and works fine ...

now problem is that default studio login theme is gone and i am not able to set it again. SYSTEM/ADMINISTRATION/LOGIN SCREEN does not have any option to use login theme. 

@hhh ... is there any option to view hidden login screen option

---

### Post by hhh on 2010-09-29
I'm a bit confused... why did you uninstall Studio if you wanted to keep it? Anyway, open Synaptic Package Manager from System>Administration and put "studio" w/out quotes in the Quick search field, then install ubuntustudio-gdm-theme to change the login theme and plymouth-theme-ubuntustudio to change the boot splash image.

Or you good just reinstall Studio from your DVD over your current install, just have the installer reformat the Ubuntu partition when you do it.

---

### Post by debasishg on 2010-09-29
;)... 

just deleted few packages and updated thru aptitude and still runnin with studio.

anyway, boot splash has been already changed after dist-upgrade. but login theme didn't changed and i liked that theme.

shall let you know regarding gdm once i done with it.

---

### Post by debasishg on 2010-09-29
not successful ... still havin the old screen

---

### Post by hhh on 2010-09-29
I think this will do it...
[http://www.webupd8.org/2010/03/gdm2setup-is-now-available-for-ubuntu.html](http://www.webupd8.org/2010/03/gdm2setup-is-now-available-for-ubuntu.html)

---

### Post by debasishg on 2010-09-30
seems something going wrong ... installed GDM2SETUP as directed .. and Xsplash too... but havin the following while runnin the gdm2 (attached screen-shot)

---

### Post by debasishg on 2010-10-01
bump,,,,

---

### Post by debasishg on 2010-10-04
bump...

---

