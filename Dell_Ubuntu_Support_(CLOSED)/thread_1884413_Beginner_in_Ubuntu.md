---
title: "Beginner in Ubuntu"
date: 2011-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by meetdilip on 2011-11-21
Got a Dell laptop with Ubuntu. Need help in 

1. How to know the current version of Ubuntu ?

2. How can I see what all hardware I have ?

3. How to have *my computer* icon on desktop ?

4. I got only one drive, but unable to create any folders in it. 

5. Is there something like* control panel* in Ubuntu ?

Thanks in advance

---

### Post by crazy bird on 2011-11-21
>  
1. How to know the current version of Ubuntu ?

**System > About Ubuntu**. There you can find whoch version you're running. 
 
>  
2. How can I see what all hardware I have ?

open a terminal (applications > accessoiries > terminalk) and type this command: **sudo lshw > hardware.txt**. In your home folder a file hardware.txt is created showing all hardware of your system.
 
>  
3. How to have *my computer* icon on desktop ?

Do you have Gconf-editor enabled? Go to ***System > Preferences > Main menu***. Click in the left screen on the entry **System tool** and check the entry **Gconf-editor** and close everything. Go to applicatiuons > system tools > gconf-editor and go to this [COLOR=black]entry: [/COLOR][COLOR=#ff0000][COLOR=black]**/apps/nautilus/desktop/**. Check the box if *computer_icon_visible*. [/COLOR][/COLOR]
 
>  
4. I got only one drive, but unable to create any folders in it. 

 
use this command:
**sudo chmod -r 777 /media/*****
 
*** is the name of your drive, like sda1. You have to find out which drive can't be accessed as you describe. Or do you mean your only drive where you also installed Ubuntu onto??
 
>  
5. Is there something like* control panel* in Ubuntu ?

On the toolbar go to ***system > preferences*** or ***system > administration***. There you find almost everything you need to make changes to the Ubuntu system.
 
> 
Thanks in advance

no problem!

---

### Post by meetdilip on 2011-11-21
Thanks a lot. 

Mine is Ubuntu 10.10  - the Maverick Meerkat released in 2010

When I take System > Administration > Update Manager, I can see an option to upgrade to 11.04. Shall I try it ? How much time will it take ? 

Also is there any aero like display in 11.04 ?

---

### Post by mastablasta on 2011-11-21
> **meetdilip said:**
> Thanks a lot. 
 
Mine is Ubuntu 10.10 - the Maverick Meerkat released in 2010
 
When I take System > Administration > Update Manager, I can see an option to upgrade to 11.04. Shall I try it ? How much time will it take ? 
 
Also is there any aero like display in 11.04 ?
 
Current version is actually 11.10 already. 11.04 is from April this year (i.e. 2011=11 April =04). Version 10.10 is supported until April/May next year when an LTS (Long term support) version will be out which is supported for 5 Years.
 
Upgrade can take a lot of time depending on your internet connection and your computer. It can also go wrong. In which case you need to prepare a liveCD as backup so you can install it all from scratch. if you wish to "upgrade" and if you didn't put any data yet on computer it might be a better idea to do a backup image of system to external drive (you can use redobackup for that-->another LiveCD) and then simply install the latest version.
 
11.04 differs a lot from 10.10 as it is the first with Unity interface, which is still buggy in 11.04. version 11.10 fixed most issues and is also a major change as it uses Gnome 3 (as opposed to your current Gnome 2.3). Gnome 3 is a lot different and more heavy on resources, though there are way to cut it all down. you can have a look how version Ubuntu 11.10 look like here: [http://www.ubuntu.com/tour/](http://www.ubuntu.com/tour/)
 
If you go for fresh install remember that there are also other versions of Ubuntu (Gnome+Unity) out there. Such as windows look a like Kubuntu (uses KDE as opposed to Gnome), a bit lighter on resources Xubuntu (looks a lot like your current version), and the super light Lubuntu (still work in progress but uses only about 80MB Ram to run and kind of looks like win98 ). You can try them all without touching your current configuration before installing using LiveCD or LiveUSB (you need a 1GB USB key to do this).
 
LiveCD (or LiveUSB) can also be used to upgrade the OS if your connection is poor.

---

### Post by meetdilip on 2011-11-21
I will try a CD upgrade then. Thanks.

---

### Post by I_can_see_the_light on 2011-11-21
> **crazy bird said:**
> 
use this command:
**sudo chmod -r 777 /media/*****
 
*** is the name of your drive, like sda1. You have to find out which drive can't be accessed as you describe. Or do you mean your only drive where you also installed Ubuntu onto??

Why 777? Allowing execution of every file on the drive seems a little bit dangerous.

---

