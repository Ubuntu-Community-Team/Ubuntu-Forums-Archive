---
title: "trouble with compiz"
date: 2011-12-17
forum: Desktop Environments
---

### Post by newcolt on 2011-12-17
I am completely new to linux and have been using it only for the past few weeks. I am using ubuntu 11.10. I wanted to apply different wallpapers for different workspaces. I downloaded CompizConfig Settings Manager, about an hour ago. I did something and now the menu on the left of my screen that appears when i place my cursor on the left end of my screen is gone! without which I don't know how to open the terminal. Along with it, the minimize, close buttons on the top of my windows has also disappeared. All that i can access now is my desktop. 

To open any folder, I open the folder on my desktop and direct myself to the desired folder. To access internet, I open a text file using Firefox and then access it. 

Kindly help me out!

---

### Post by azkraja on 2011-12-17
Log off first, and while log in screen appears just click  (*) like icon where you will find two option Ubuntu and Ubuntu 2D, just check the Ubuntu 2D and log in, you will find application panel on left side, just open Compiz Config Setting Manager again and make correction, be careful while using CCSM, it is making problem with this version 11.10. I totally UN-installed CCSM after waisting my time to fight with. other wise go to terminal and place the command " unity --reset " and let it work until finished, it will take sometime. My advise is not to play with CCSM unless you do not learn about it. Have a nice time, just let you know that i am also a new to Ubuntu and still learning.

---

### Post by newcolt on 2011-12-17
I don't even have the task bar on top! How do I log off? is there some other way to do it, other than selecting it from the menu on top?

---

### Post by tonglen on 2011-12-17
you can log off  by going under the curtain and bringing up the command line.
press Ctrl  Alt keys and F1 all at same time this will take you into 
 command line

type in your user id
and then you will be prompted to enter your password

once you have logged on type 
 sudo poweroff
you will be asked for your password
once entered your system will close down...

Oh and Ctr Alt and F7 together will take you back from the command line back into the GUI...

---

### Post by scorchgeek on 2011-12-17
CCSM is a pain in the rear in recent versions of Ubuntu. When I set it up most recently I just Googled one missing element at a time and figured out how to get it back, and after about five or ten I had everything working.

---

### Post by CaptinGoogle on 2011-12-18
Usually what happens to me is the Unity applet becomes unchecked for some reason. You could boot into Ubuntu 2D and open up Compiz and recheck the box. Then log back into Ubuntu 3D

---

### Post by newcolt on 2011-12-18
Thanks guys. But none of the shortcut keys worked either. So I restarted my system and went into recovery mode. There I made the changes again. But I'm annoyed with this software, so I have removed it completely. Is there any other way I can use different wallpapers for different workspaces?

---

### Post by newcolt on 2011-12-18
I uninstalled Compiz and rebooted the system. The problem has resumed now!

---

### Post by stinkeye on 2011-12-18
CCSM=compizconfig-settings-manager and is a program for changing **compiz** settings.

Unity is a plugin for **compiz** which is the window manager for the  "ubuntu" session.
Uninstall the program **compiz** and you uninstall unity.

The "ubuntu 2d" session should still work as it uses metacity as the window manager
with the unity2d packages.

---

### Post by thesarp on 2011-12-18
even im suffering from the same problem now, pls help..
im new to ubuntu and im using ubuntu 11.10..:confused:

---

### Post by stinkeye on 2011-12-18
> **thesarp said:**
> even im suffering from the same problem now, pls help..
im new to ubuntu and im using ubuntu 11.10..:confused:
Same problem as what?

---

### Post by thesarp on 2011-12-18
I was trying to apply a new wobbly effect and was playing around in the preferences area and i dont remember what i did,,, now there is no toolbars and i see only my desktop with the trash icon..

> **newcolt said:**
> I am completely new to linux and have been using it only for the past few weeks. I am using ubuntu 11.10. I wanted to apply different wallpapers for different workspaces. I downloaded CompizConfig Settings Manager, about an hour ago. I did something and now the menu on the left of my screen that appears when i place my cursor on the left end of my screen is gone! without which I don't know how to open the terminal. Along with it, the minimize, close buttons on the top of my windows has also disappeared. All that i can access now is my desktop. 

To open any folder, I open the folder on my desktop and direct myself to the desired folder. To access internet, I open a text file using Firefox and then access it. 

Kindly help me out!

---

### Post by stinkeye on 2011-12-18
Firstly try to open a terminal with ctrl+alt+t and run 
```
compiz --replace & disown
```
Leave it to run for a while.

If the launcher and panel dont appear use this to set compiz to defaults```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```
Give it 30 secs or so to run and if it still doesn't load properly run... 
```
compiz --replace & disown
```


Finally if that doesn't work...
Log out ctrl+alt+delete or use ctrl+alt+SysReq(print)+k
Change to the "ubuntu 2d" session by clicking on the cog icon and login.
Open a terminal and run this, which is the same as the other command but doesn't load compiz
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```

Then logout and choose the "ubuntu" session and login.

---

### Post by thesarp on 2011-12-18
Thanks a lot,,, it really helped me...:KS:KS:KS:KS

---

### Post by stinkeye on 2011-12-18
> **thesarp said:**
> Thanks a lot,,, it really helped me...:KS:KS:KS:KS
No problem.
Quite often when changing settings in ccsm it may fail to reload properly so the
first thing to try is the **compiz --replace** command.
It's always recoverable though, by setting compiz back to defaults.

What I do is install easystroke (mouse gestures),set it to autostart and bind a couple of commands to gestures so I can recover easily.(see pic)

When you have compiz set up how you like, use 
**ccsm > preferences** to export your profile.
Then if compiz becomes messed up use **ccsm > preferences** to import your saved profile.

---

### Post by thesarp on 2011-12-19
oh thanks for all the tips...:KS
im new to ubuntu so still trying to get the hang of it...


will do as you say for exporting n saving the profile for future use..:D

---

### Post by stinkeye on 2011-12-19
Previous releases of Ubuntu with compiz have been fairly stable but 
with the release of gnome3 and the new unity desktop it has become quite buggy.
I expect the 12.04 release to be a lot better.
Which part of the solution actually solved it for you?

---

### Post by thesarp on 2011-12-19
actually my ubuntu tool bars and all, crashed twice in past 2 days, first i tried wit the code

```
compiz --replace & disown
```

i got everything bac to normal,,,,
today, again i was trying to learn compiz, n it crashed again.. so tried the above code but it was of no use so i tried all n finally this worked for me ...

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```:D

---

