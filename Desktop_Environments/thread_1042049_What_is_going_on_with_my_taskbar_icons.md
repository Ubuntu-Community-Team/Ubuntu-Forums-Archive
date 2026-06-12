---
title: "What is going on with my taskbar icons?"
date: 2009-01-17
forum: Desktop Environments
---

### Post by Exile09 on 2009-01-17
Hey guys I wondered if you knew what has happened to my ubuntu 8.10 install?

[[IMG]http://img297.imageshack.us/img297/2558/helpmesr3.png[/IMG]](http://img297.imageshack.us/my.php?image=helpmesr3.png)
(click to enlarge)

Basically my program icons (that are normally in the taskbar on the top right of the screen) have somehow managed to move out of the taskbar and into there own program program window.

This is driving me mad so any help would be much appreciated!

---

### Post by vanadium on 2009-01-17
Try deleting these icons and then re-add them to the taskbar.

---

### Post by damis648 on 2009-01-17
You must have accidentally removed the notification area. Right click the top panel and then choose "Add to panel..." and scroll down and add 'Notification Area'. The icons should dock back into your panel, you might just have to move the notification applet back to its original position.

---

### Post by vanadium on 2009-01-17
Try the suggestion of damis648 first.

---

### Post by Exile09 on 2009-01-17
I've tried adding the notifcation area to the panel & it doesn't work. Nor does deleting the icons and then adding them back to the taskbar.

[IMG]http://img209.imageshack.us/img209/9690/helpme2fx8.png[/IMG]

---

### Post by vanadium on 2009-01-17
Did you restart the system or at least log out and back in?

---

### Post by Exile09 on 2009-01-17
logging out & doing a system restart or doing ctrl + alt + backspace to restart x-window makes no difference :confused:

I've been living with this problem for about a week now, but now its really starting to annoy me!

---

### Post by damis648 on 2009-01-17
The notification area is being blocked by the next applet. Drag that little grip-looking thing over to uncover the icons.

---

### Post by Exile09 on 2009-01-18
[IMG]http://img513.imageshack.us/img513/9863/helpme3rr3.png[/IMG]

Does anyone have any suggestions on how to resolve this? I think I'm gonna just do a reformat and reinstall ubuntu beacuse this is really winding me up....

---

### Post by oaqster on 2009-01-18
> **Exile09 said:**
> 
Does anyone have any suggestions on how to resolve this? I think I'm gonna just do a reformat and reinstall ubuntu beacuse this is really winding me up....

dont htink a reinstall is required, its just a visual thing - the three i see (i think) are the network manager, blue tooth applet and pidgin.  looking at your previous screen shot you seem to have added a notification area cuz i see a divider (you might have even added two)

> **Exile09 said:**
> 

[IMG]http://img209.imageshack.us/img209/9690/helpme2fx8.png[/IMG]

if you right click on divider and click on about you should see a popup with "Notification Area" and version number.  if not right click on the dividers and remove from panel and add the notification area by right click and Add to panel

now right click just to the right of the divider and select add to panel and add the network manager and the blue tooth applet.  for pidgin start pidgin and goto Tools -> Preferences -> Interface, the first option on that tab will be "Show system tray icon" select Always from the drop down.  once you have everything you need back on your notification area move it to where you want and right click on the divider and select lock to panel (you might have to unlock other stuff if your moving it across them)

give this a shot and let me know....
- oaqster

---

### Post by Exile09 on 2009-01-19
Nope still no joy.

When I try to add Notification Area to the toolbar I just get those little boxes (or dividers as you may call them). I don't seem to have any Notification Area. I have the same problem on the bottom toolbar as well...

---

### Post by sleepitoff on 2009-01-19
That is odd. Have you tried deleting the panel, adding a new panel, then manually adding back everything you had there?

---

### Post by Exile09 on 2009-01-19
yes I'm afraid that didn't work & I still have the same problem!

---

### Post by Exile09 on 2009-01-20
Right this has been going on for too long now! & I ant take it much longer!

I'm going to give it another day but unless anyone has any ideas that don't involve removing and re-adding things, I'm going to change the OS because I cant have my OS doing strange things like this........

---

### Post by damis648 on 2009-01-20
Open a terminal and do the following:
```
rm -r ~/.gconf/apps/panel
```and then log out and back in. This resets your panel config.

---

### Post by Exile09 on 2009-01-20
> **damis648 said:**
> Open a terminal and do the following:
```
rm -r ~/.gconf/apps/panel
```and then log out and back in. This resets your panel config.

This fixed it!

Thank you so much!

and also thanks for everyone else's efforts its much appreciated!

:D:D

---

### Post by Exile09 on 2009-02-08
right I think there may be a bug in ubuntu or gnome because despite doing what damis648 suggested I keep getting this problem a little time after I have reconfigured by desktop.

As I felt it may have something to do with some of my desktop effects I decided to do a reinstall (without the effects) and once again I have this problem!

Since I have done the reinstall all I have done to customize my desktop is remove the evolution & help icon & add a terminal icon. Also I have added eyes, forcequit, & system monitor to the bottom gnome panel/taskbar.

This is a fresh installation so I dont understand why I still have this issue?? The only thing I can think of is that there is a bug involving the panel/taskbar icons & gnome or ubuntu.

Once I get some time I might give kubuntu a go, as these problems are really annoying me!

---

