---
title: "Power management"
date: 2006-07-08
forum: Desktop Environments
---

### Post by dasyar613 on 2006-07-08
I am wondering if anybody else is having the same problem. On my desktop unit  in prefences, when I set the inactivity, to let say 2 minutes, and in general I set it to hibernate or suspend, neithe one seems to work. But, in the shutdown window, when I choose hibernate option, the computer goes into to hibernate mode. Has anybody overcome this problem?

Thanks
New to Ubuntu

---

### Post by atoponce on 2006-07-08
I could be wrong, but I think there is still very limited support with suspend and hibernate.  I know that I have yet to get it working correctly on my laptop.

---

### Post by dasyar613 on 2006-07-08
I have ubuntu 64bit installed on my ACER5002, it seems to work fine on that machine, but I do not have any intention of doing a WOL on that unit. When you bring it up from hibernation though, it takes an awfull long time, so it might be just as well if I do a shutdown on my laptop.

---

### Post by dasyar613 on 2006-07-08
As a follow up, this is a bug, and it has been posted in bugzilla. Now, I guess we just have to be patient.

---

### Post by orb9220 on 2006-07-08
Also check in gconfig settings.

menu>system tools>configuration editor

then in Gconfig goto apps/gnome-power manger and check those settings.

My gnome power applet was set to never for monitor shutdown, But it would shutdown anyway.

So in ac_sections I changed the values to 0 for disable.

And whamo-chango my monitors stayed on.

Beats me why the gnome-power mangement wasn't working.

But gconfig has all there for you to check and change.

:-({|=  "No More,No More being a Slave to the XP Dark Side"

---

### Post by dasyar613 on 2006-07-08
OK,now you got me, what OS are you describing, KUBUNTU or UBUNTU gnome. The menu selections that you described are not on my ubuntu 6.06 desktop. What I did experiment with is the power management located in preferences.

Thanks

---

### Post by orb9220 on 2006-07-08
The main menu "orange cirlce " which shows from bottom up:

System
Places
Add/Remove
System Tools >Configuration Editor

---

### Post by orb9220 on 2006-07-08
If it is not there then go into Main>Acessories>Alacarte Menu editor

And scroll down to system tools and check to have it show up in yer menu

---

### Post by dasyar613 on 2006-07-08
Interesting, none of my menues shows an configuration editor. I went to the ADD/REMOVE, and the configuration editor has a check in the box, so it got loaded, but where?  I guess I will uncheck it, and then recheck it, in the ADD/REMOVE. This should be interesting.

---

### Post by orb9220 on 2006-07-08
If configuration menu with a big red g is not in your menus or listed in Alacarte menu.

Then you need to run synaptic and do search on config

and see if it is itstalled.

---

### Post by orb9220 on 2006-07-08
It's called "gconf-editor" may be abele to run from terminal.

---

### Post by dasyar613 on 2006-07-08
Thanks, that was a good piece of information, but, it did not help. When I found the info for the power management,in gconf-editor, all the pertinant check boxes had a check in them. So, it still does not work on my desktop system. I had high hopes of getting the WOL to work, I hope I do not have to go back to my W2K system, or  heaven forbid the Vista beta 2 for customers CD.

---

