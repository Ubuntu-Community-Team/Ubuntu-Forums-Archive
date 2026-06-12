---
title: "xfce4 keyboard issues"
date: 2018-05-10
forum: Desktop Environments
---

### Post by lvm on 2018-05-10
1. Where are the advanced keyboard settings available in KDE or gnome? e.g. I am used to shifted numpad arrows acting like shifted normal arrows: selection, not numbers.

2. Where is the keyboard layout indicator? I have two keyboard layouts, but there is no layout indicator on the panel. I am using scrolllock to switch layouts, but scrollock LED doesn't work either. And layout switching is global, not per-application - how can I change that?

3. I cannot add notification area item to a panel - add button is grayed out, does it mean that it is already added? But there is no [visible] notification area on this panel... Maybe this is why I cannot see the keyboard layout indicator?

18.04. Trying xfce for the first time, sorry for dumb questions.

---

### Post by tinylagarto on 2018-05-10
In Xfce it is possible to achieve the same thing like in other desktops. 

First open the Xfce settings and go to keyboard and add your layouts. Then add a panel indicator from the right click menu to the Xfce panel and it should show your layouts.

How did you add Xfce? To be able to use the keyboard layout you need *xfce4-xkb-plugin *installed on your system.

---

### Post by lvm on 2018-05-10
Ok, so there are some plugins which were not installed with xfce4 package - thanks. I installed keyboard layout indicator (indicator font size doesn't change though - even when I set it to 2pt it is enormous), and notification area started working after a reboot, but I still don't know how to set advanced keyboard settings. And I didn't find anything to change colours to my liking, just predefined themes - am I missing something?

---

### Post by xubu2 on 2018-05-10
Since 18.04 **numlockx **comes preinstalled on Xubuntu.
Uninstall it if it's on your system.
I've had the same problem.

---

### Post by tinylagarto on 2018-05-10
> **lvm said:**
> Ok, so there are some plugins which were not installed with xfce4 package - thanks. I installed keyboard layout indicator (indicator font size doesn't change though - even when I set it to 2pt it is enormous)...

Are you already on 18.04? Because the new keyboard layout plugin was revamped and looks better now.

---

