---
title: "Refresh (or change) custom app launcher icon via CLI"
date: 2009-10-01
forum: Desktop Environments
---

### Post by onyxwolf on 2009-10-01
(PLEASE HELP! Read third post down Pg 2 Nov 10, 09 Zenity notification is not working!!!)
Original post (still trying to find an answer to this other than Zenity Notification)--
I have a simple script to kill the screen saver with a custom application launcher. As you can see my goal is to also use the launcher itself as a notification icon as well. I'm doing that by simply replacing the icon set to be the icon in the properties with a different one (using same path and filename); HOWEVER, I have to refresh it for it to change the icon.

#!/bin/bash


saver=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`
if [ "$saver" = "true" ]
then
    (gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false)
(cp /usr/share/icons/hicolor/scalable/apps/apport.svg /home/onyxwolf/ThemeStuff/Icons/SaverStatus.svg) 
fi
if [ "$saver" = "false" ]
then
    (gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true)
(cp /usr/share/icons/hicolor/scalable/apps/checkbox.svg /home/onyxwolf/ThemeStuff/Icons/SaverStatus.svg)
fi

killall gnome-panel
---
But the only way I can find (with a couple hours of research) to refresh it is by resetting the whole panel; thus the killall command at the end. Its really ugly and inconvenient having to wait for my panels to reappear. Not to mention I have to cross my fingers and hope that everything is going to end up in the same place :-| !

Is there a way to refresh only the custom application launcher? Or is there a way to change its icon that will automatically refresh and switch the icon?

I'm going crazy trying to figure this one out!
Also is there a simple bash/sh way to make notification display that will go away on its own (i.e not having to click ok, like when you get a new mail with evolution)?

P.S. There really needs to be a message icon with a smiley pulling its hair out in frustration! ](*,)

---

### Post by onyxwolf on 2009-10-02
*Bump* Since figuring out this simple switch on off script I've made a couple more switches, leaving out my current way to change the Icon because none are as necessary to have on as my screen saver (I have sensitive info on pc and don't always remember to lock it myself). Anyone? Even Ideas are helpful to pursue.

---

### Post by onyxwolf on 2009-10-05
Seriously! No one has any ideas. I know that when you change the picture for the icon (with same name, like I'm doing now) file, you have to reset the launcher in order to take effect. Even if you go into the launcher's properties (right click on launcher>properties) and reselect the icon and hit ok. The pic on the launcher itself will not change; however, if you select a completely different Icon and hit ok it WILL change (obviously having to load the icon from a different file). So I'm trying to find a sh/bash way to change the properties of the Launcher in order to change the actual icon displayed on the launcher, so I don't have to killall the panel

---

### Post by onyxwolf on 2009-10-06
Last Bump, guess this is not possible!?! (I'm certain it is but I must need a lesson in presentation on these forums!) So guess I'll submit the idea for a custom switch application or something like that. (Don't see exactly how they could make a launcher or applet like that but hey I'm not the developing genius those guys are)

---

### Post by zhocchao on 2009-10-06
hi
Time to sleep for me now but could zenity be an option?

---

### Post by onyxwolf on 2009-10-09
I actually started another thread specifically for the notification display. Zenity is good but, as far as I've been able to figure, it requires you to press the ok button, and I just want one that pops up and goes away all by itself. Unless you know of a way to make Zenity do this.

---

### Post by zhocchao on 2009-10-10
```
#!/bin/bash
while(true)
do
   zenity --notification --window-icon=/usr/share/icons/hicolor/scalable/apps/apport.svg
 gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true &
   zenity --notification --window-icon=cp /usr/share/icons/hicolor/scalable/apps/checkbox.svg
  gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
done
```

You will have to modify this. But this way zenity will work the way you want

---

### Post by onyxwolf on 2009-10-10
I have to apologize I see what your saying. I got that mixed up with another tidbit I mentioned in my original post, because I only knew zenity as a popup notifier that opens another window. I was also looking on how to cause one of those without having to click ok (which someone did hook me up with-- apt libnotify-bin w/ notify-send cmd). I didn't realize zenity could send put icons in the notification area! Its not exactly what I was talking about, but I actually think its better. I tend to pay more attention to the notification area, to check on the battery, my connection status etc... Thank you!

---

### Post by onyxwolf on 2009-10-11
OK, not marking this as solved because it is not, yet. There should still exist a scripting way to change the panel custom app launcher icon upon a program launch; HOWEVER, there is a way to have an icon act as launcher and notification without having to restart the whole panel. The only bad thing about this way is it puts a constant background loop for the Zenity notification program. It is only fractionally (unmeasurable) taxing on the system, though. It is only zenity, after all. Anyways here is my final:

#!/bin/bash

saver=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`
if [ "$saver" = "true" ]
then
while(true)
do
   zenity --notification --window-icon=/usr/share/icons/exotic/scalable/actions/sleep.png --text="Screensaver is UP"
   gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
   notify-send --urgency=critical --icon=/usr/share/icons/hicolor/scalable/apps/apport.svg "Security Risk:
Screensaver is Disabled"

   zenity --notification --window-icon=/usr/share/icons/hicolor/scalable/apps/apport.svg --text="Screensaver is Down"
   gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
   notify-send --icon=/usr/share/icons/exotic/scalable/actions/sleep.png "Screensaver Active"
done
fi
if [ "$saver" = "false" ]
then
while(true)
do
    zenity --notification --window-icon=/usr/share/icons/hicolor/scalable/apps/apport.svg
   gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
   notify-send --icon=/usr/share/icons/exotic/scalable/actions/sleep.png "Screensaver Active"

zenity --notification --window-icon=/usr/share/icons/exotic/scalable/actions/sleep.png
   gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
   notify-send --urgency=critical --icon=/usr/share/icons/hicolor/scalable/apps/apport.svg "Security Risk:
Screensaver is Disabled"  
done	
fi


Odd, huh? First I kept the if-then approach because the sh file is called by .xsession. If it was just the one while loop instance that was set to show the Screensaver is UP icon to start, then if your session starts with the screensaver disabled, then it would all be backwards! The if-then causes the script to first check to make sure that it starts with the correct status, then switches correctly. Secondly, the way the zenity statements are structured is because the zenity command with the UP status and icon will display that icon, but I found that the commands directly below the zenity command is what happens when you click on it. Anyways there is your button to disable the screensaver w/icon notification. Enjoy...

Can't forget to thank zhocchao for the zenity notification and while loop structure info. Also please note that the icons I used to represent the "Screensaver is UP" status is from the Exotic theme which you may not have so you may have to edit what icons you're using.

Cheers!

---

### Post by hamidaddin on 2009-10-31
I have the same problem. I have more than one script to toggle things on and off (touchpad, 3g modem...etc). These scripts have shortcut icons on the gnome-panel and I would like to toggle the icons from the script based on the status without reloading the whole panel.

Anyone knows of an easy way to do this?

---

### Post by onyxwolf on 2009-11-04
Hey, the above script (one posted just above your reply) works great. I don't think it actually creates a constant loop it just stays on all the time, only looping after you click on it twice (just putting looping back to the starting position), and other than it be randomly placed with your other notifications, its aesthetically pleasing enough. Now I can imagine that the touchpad and modem are not just turned on and off by gconf. Can you post your scripts so we can take a look at them to see if there is away to do it through zenity notification?

---

### Post by onyxwolf on 2009-11-05
Sorry was repeating myself didn't realize a post I started actually made it to 2 pages! LOL

---

### Post by onyxwolf on 2009-11-10
OK There's a couple serious problems with Zenity Notification. First is that it causes all of my notifications in the Notification area to bounce (back and forward) A LOT! Its very annoying. And while running AWN (I just installed and think I'll enjoy it) the icons (my "buttons") don't reappear half the time. Again very annoying!

---

### Post by Jhongy on 2009-11-12
I've been trying to do the same as you -- toggling a proxy (starts/kills an SSH background service, modifies proxy settings), to use with Chromium (in Firefox there were extensions that added buttons to the toolbar).

It's easy to change the .Desktop file for the launcher to point to the new icon, but I can't refresh the panel icon without doing killall gnome-panel.

There doesn't seem to be any external way to force a redraw -- gnome-panel seems to be a self-contained application (for example, if I open the "Add applet" dialog, then use xkill to kill the dialog, it kills the whole gnome-panel application.

I also tried using Zenity, but it's far from ideal.

I also use AWN, and in the end I decided to stick with a static AWN launcher icon, and notify-send alerts. If you really want to have a toggling icon in AWN, you could probably create an AWN applet quite easily -- they have an example python applet on their site that you can copy.

J

---

### Post by onyxwolf on 2009-11-17
Thanks I just started playing around with docks. I tried AWN but found Cairo to be more to my liking because it is far more customizable. I didn't think to check if I can do it thru that though. I'll have to give it a try!

---

### Post by onyxwolf on 2010-06-01
I have abandoned this for a long time, as I got to wrapped in other projects but I found the perfect solution in Cairo-Dock using it's DBus plug-in. A quick line in the script and it changes the icon to whatever you want it to!!! Just wanted to make sure I noted this here.

---

