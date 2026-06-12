---
title: "No access to desktop in Unity for 16.04"
date: 2016-07-06
forum: Desktop Environments
---

### Post by meetdilip on 2016-07-06
I just updated to 16.04 from 14.04. Everything was fine. Just that there  is nothing on desktop. No icons, nothing. I cannot change wallpaper  either. I have a few files in " Desktop " folder. None can be seen on  Ubuntu's default Unity desktop.The system hangs once in a while as well.  Could this be related ? Any solution ? Thanks.

---

### Post by grahammechanical on 2016-07-06
I am confused. With Unity we do not have folders & files on the desktop. Do you have a top panel with indicators at the right side of the panel? Do you have a launcher on the left screen side with applications such as file manager & Libreoffice?

If you right click the desktop wallpaper do you get a menu? There should be an option to change desktop background. That will open System Settings at the Appearance utility. 

Did you upgrade with Gnome 3 shell & Cinnamon still installed? You could try updating.

```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```

Regards.

---

### Post by meetdilip on 2016-07-06
Yes. Top panel is there and working fine. I had launcher on left, but changed it to go to bottom. I have Libre office and File Manager icons. I have resized the icons though.

But when I try to change the wallpaper and right click on desktop, I didn't get any menu. I was not able to change background as well. I even went to settings and tried changing wallpaper there. No effect on default wallpaper on desktop. I updated while I was within Gnome since I couldn't bring back Unity before update. I reinstalled Unity and want to use it now.

Thanks. I will try those commands.

PS : I use Radeon drivers. I had to choose alternative option in " Additional Drivers ". Could that be an issue ?

---

### Post by deadflowr on 2016-07-07
The issue is that unity has the file manager handle the desktop, but gnome does not.
So you need to reset it in unity.
This command will do that:
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
This will bring back the right click and all your items in the Desktop folder.

> 
The system hangs once in a while as well. Could this be related ? 
I'm not sure how.
Seems like a different issue.

> PS : I use Radeon drivers. I had to choose alternative option in " Additional Drivers ". Could that be an issue ?

What alternative options?
There aren't any additional drivers in 16.04 for Radeon/AMD cards, currently.

---

### Post by meetdilip on 2016-07-07
Thanks @deadflowr , it got ok by itself

> **deadflowr said:**
> 
What alternative options?
There aren't any additional drivers in 16.04 for Radeon/AMD cards, currently.


There is some option called " Using Processor microcode firmware for Intel CPUs from Intel-microcode (Proprietary) " . I unticked it anyway.

I still have issues with ctrl c/v/x keys. Can you help me here : [http://ubuntuforums.org/showthread.php?t=2329958&p=13514182](http://ubuntuforums.org/showthread.php?t=2329958&p=13514182)

---

