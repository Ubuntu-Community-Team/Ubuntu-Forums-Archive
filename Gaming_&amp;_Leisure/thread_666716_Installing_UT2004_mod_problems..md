---
title: "Installing UT2004 mod problems."
date: 2008-01-13
forum: Gaming &amp; Leisure
---

### Post by Urfaust on 2008-01-13
I am having a problem getting any mods to run on UT2004. I downloaded the loki installers and did the "sh blahblah.run" to install them, but they are not recognized when I open the game and click on community. I then emptied the folders into the locations in the UT2004 folder...ie., textures into textures and ect. This allowed the game to show up in the ut2004, but when I click activate the window closes and another prompt shows up with a bunch of lines and then it says it cannot connect to ut2004.epicgames.com... or something like that.  In the read me file it says to run RedOrchestra, I tried that in the terminal and the alt-f2 window and no luck. I uninstalled, then reinstalled the game so I could begin fresh again.  

Also,  I installed the game in a folder in my home folder because I could not install it in the local/games, because i don't have permission unless I'm on the root account. If that makes a difference.  The mod is Red Orchestra.
Any suggestions? =D 

 Thank you.

---

### Post by cooldude on 2008-01-13
An easier way is to put the whole red orchestra folder into the ut2004 folder NOT into the subdirectories. Then bring up a console & type 

"ut2004 -Mod=RedOrchestra"  exactly as written it should run the game. You have to install the ut2004 linux patch 3369-2 for the game to work at all.

So if you want to delete the game later on just delete the one folder instead of all the individual files in different folders. A lot cleaner uninstall.

Let me know if it works....

As far as root problems:

Where did you install it ut2004? Home directory or /usr/local/games? if installed in /usr/local/games just type in sudo nautilus then you can move it from home directory to /usr/local/games/ut2004

---

### Post by Urfaust on 2008-01-13
I typed that into the terminal and got:

bash: ut2004: command not found


I downloaded the loki megapack. that should keep the game at the latest patch, I believe. 

And the game is in the home directory

---

### Post by cooldude on 2008-01-13
if you did not install as root, that only works globally. So you will have to point file browser or console to ut2004 folder then type or click on the "ut2004" script file as soon as you get inside ut2004 folder, in your home directory. Game should start same applys as I said before except ignore the last part about sudo nautilus thing as you don't need root permission to run in your home directory.

if you type it in console  you may have to do it this way ./ut2004 or sh ut2004

you will still be able to run the ut2004 game if no patch is installed, but if red orchestra does not run latest patch may not be installed. easy way to tell is run ut2004, go to multiplayer, as soon as you do that look in upper right hand corner of screen will give you latest version number which should be 3369. it wont show the -2 part though.

---

### Post by Urfaust on 2008-01-13
Yep, the version is 3369

Also, It is also worth noting that I put the symbolic links outside of the ut2004 folder in their own separate folders. (inside of the home folder) I am not sure as to what exactly symbolic links do.

---

### Post by cooldude on 2008-01-13
O.k. just put the red orchestra folder in inside ut2004 folder. Then in console type /home/your_user_name/ut2004/./ut2004 -Mod=RedOrchestra then enter, should see a splash screen for red orchestra.

---

### Post by cooldude on 2008-01-13
> **Urfaust said:**
> Yep, the version is 3369

Also, It is also worth noting that I put the symbolic links outside of the ut2004 folder in their own separate folders. (inside of the home folder) I am not sure as to what exactly symbolic links do.

they just point to the file you need to start it with, but don't really think you need them persay.

I play red orchestra quite a bit but now most people play the paid version ( Red Orchestra OST front ) so not as many people online. But on saterdays around 3:00 centeral USA time will see all kinds of people. they use [www.funlevel.net](www.funlevel.net) server so still have people play the 3.3 version still.

---

### Post by Urfaust on 2008-01-13
Awesome, thank you!

---

### Post by cooldude on 2008-01-13
red orchestras working? I guess so...lol

---

