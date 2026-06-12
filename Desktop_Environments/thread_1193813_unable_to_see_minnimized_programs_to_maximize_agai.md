---
title: "unable to see minnimized programs to maximize again......"
date: 2009-06-21
forum: Desktop Environments
---

### Post by duhfactor on 2009-06-21
Greetings,

I am running ubuntu 8.04 with gnome, and am having trouble as a switcher from windows. I have installed compiz which I'm happy with generally, and decided to install an application that looks like a lower toolbar that minimized programs sit on until you try and maximize them again. It was a 3D spotlight deal that worked fine for a while. Recently, that toolbar dissapeared, and as I minnimize programs, they disappear too, and I can only access them by clicking on the icon sitting on the top toolbar launcher, effectively opening up the program again, and again, and again each time I forget and minnimize the software. I wouldn't even mind going back to the standard lower toolbar that comes with gnome, but have no idea how to do that. I'm not sure why it stopped working, and wonder if it is still somewhere, but just doesn't launch during boot up or something....any ideas on how I can solve this problem??? Much appreciated.

D

---

### Post by ugm6hr on 2009-06-22
Alt-Tab will rotate between open applications.

I think you can put the original Gnome panel back by right-clicking on the desktop and adding a new panel (sorry, at work on Windows at the moment).  Then right-click on the new panel, and add to panel the correct applet.

If you can remember what the bar you installed was called, we might be able to help you find it.

---

### Post by linuxrockz on 2009-06-22
It seems that you were using awn (avant window navigator). As far as I remember it had a spotlight effect. Try launching awn by opening the terminal Applications > Accessories > Terminal then type "awn" and hit enter. It may launch.
 
To get the standard lower toolbar (its called as panel) right click on the upper panel and click "new panel". Now a blank panel would come at the bottom of the screen. 

Right click on it and click "add to panel"

and add the following applets 

1.Show Desktop 

2.Window List (this is the one you need to switch between minimized windows)

3.Workspace switcher
and 
4.Trash

Thats all you need to do.

P.S. To make your tab look more appealing you may right click on the panels and click properties go to the background tab select a solid color and decrease the opacity to make it more transparent :)

---

### Post by duhfactor on 2009-06-27
O.K. folks, I can now switch between minimized programs by using alt-tab, thank you. I found your right, it is the "awn" program that I downloaded which has this 3D effect that I used. I found the awn manager under "system-preferences-awn manager" and have opened it up thinking that there might be a setting wrong or something, but don't understand fully what should be in the possible dialog boxes. When I try to run "awn" from the terminal like this: "damon@damon-desktop:~$ awn" this came up:
"bash: awn: command not found". Would I need to try it as root? I would like to try and get awn to launch if I can, rather than go back to the standard gnome toolbar. By the way, in the awn manager, there is a tab labeled "launchers" and there is nothing listed in the possible dialog boxes, although there is an awn launcher listed under the "applets" tab in the manager. Any ideas??

Thank you!!

D

---

### Post by ckonestroh on 2009-06-27
Thats not the problem you need to 


right click panel > add to panel > select Window list....

Its back.....


To Remove this effect 


minimized window there will be a tab to Right

right  click it > select Remove from panel 


Cool feature comes with this a bit over kill

Right click minimized window > Move to other workspace select desktop you move program to 



later good luck...

---

### Post by perlluver on 2009-06-27
To start AWN, you will need to type avant-window-navigator.  If you would like it to automatically start when you login, then go to System>Preferences>Startup Applications or sessions, and click add, then add avant-window-navigator as the command.

---

### Post by duhfactor on 2009-06-28
> **perlluver said:**
> To start AWN, you will need to type avant-window-navigator.  If you would like it to automatically start when you login, then go to System>Preferences>Startup Applications or sessions, and click add, then add avant-window-navigator as the command.

Thanks folks, this worked well. This little toolbar shows up each time I boot up ubuntu now. Great!!! Thank you!! One more question without starting a new thread....can I use the same method to get compiz window manager to load up each time I boot ubuntu? I'm just not sure what command to use, and how I would find out in the future if I were to download another or different application...Ideas?

Thanks,

D

---

### Post by linuxrockz on 2009-06-29
Just add the command
```
compiz --replace
```
to the startup applications.
I hope that helps.
;)

---

### Post by duhfactor on 2009-06-30
> **linuxrockz said:**
> Just add the command
```
compiz --replace
```
to the startup applications.
I hope that helps.
;)

Wow,

It worked great, now compiz loads up at boot up. I'm glad you folks could help me out. When I get some time, I'll get over to ask some more compiz questions on how to get the cube to work....That will be for another day though.....thanks for everything folks.

D

---

