---
title: "How To Install True Combat: Elite"
date: 2010-11-01
forum: Gaming &amp; Leisure
---

### Post by The_Accursed_One on 2010-11-01
Okay, I'm sure this is a never-ending question but how do I install True Combat : Elite? I have the .zip file but thats about the extent of where I am. How do I install it?

I have Ubuntu 10.04 if that helps at all :P

---

### Post by WienerWuerstel on 2010-11-01
> **The_Accursed_One said:**
> Okay, I'm sure this is a never-ending question but how do I install True Combat : Elite? I have the .zip file but thats about the extent of where I am. How do I install it?

I have Ubuntu 10.04 if that helps at all :P

Extract the .zip file and put the Folder "tcetest" in /home/yourusername/.etwolf

---

### Post by The_Accursed_One on 2010-11-02
Is there a guide on how to install this on Ubuntu from start to finish? From their website it says I need Wolfenstein: Enemy Territory and all sorts of stuff. Need a guide in a bad kind of way.

---

### Post by WienerWuerstel on 2010-11-02
> **The_Accursed_One said:**
> Is there a guide on how to install this on Ubuntu from start to finish? From their website it says I need Wolfenstein: Enemy Territory and all sorts of stuff. Need a guide in a bad kind of way.

1. Install this Package ([http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb"))

2. Open a Terminal

3. ```
sudo apt-get update
```4. ```
sudo apt-get install enemy-territory
```5. Start Enemy Territory once and create a User

6. Download True Combat Elite 0.49 and the 0.49b Patch
    [http://www.filefront.com/6002126/True-Combat-Elite-.049/](http://www.filefront.com/6002126/True-Combat-Elite-.049/)
    [http://www.truecombatelite.com/files/tce049b_all_os_fixed.zip](http://www.truecombatelite.com/files/tce049b_all_os_fixed.zip)

7. Extract TCE 0.49 and put the Folder "tcetest" in "/home/yourusername/.etwolf

8. Extract the TCE 0.49b Patch and put the Content of the Folder in the "tcetest" Folder

9. Now TCE should be listed as a Mod in Enemy Territory

10. (Optional) Update Punkbuster with [http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

11. Have Fun :P

---

### Post by The_Accursed_One on 2010-11-03
Got all the way to the extraction and then this guide dead-ended. I CANNOT find the folder. Like, at all. Do I just type manually where I want to extract the files to? And if so, how?

But besides that, that is a great guide. Got me all the way to the extraction so I'm not complaining at all. Thank you so much.

---

### Post by realzippy on 2010-11-03
/home/*yourusername*/Downloads   ??


or can't you find /home/yourusername/.etwolf ?

..when doing it with nautilus (file manager) press ctrl +h to show "hidden" files (those with a "." in front of like ".etwolf")

---

### Post by The_Accursed_One on 2010-11-03
Yeah, I can't find it in my home folder or my downloads folder. I'll check once more once I get home but this morning it was trying to evade me. :P

---

### Post by WienerWuerstel on 2010-11-03
> **The_Accursed_One said:**
> Yeah, I can't find it in my home folder or my downloads folder. I'll check once more once I get home but this morning it was trying to evade me. :P

When you download the TCE .zip with Firefox OR Chrome the File should be in /home/yourusername/Downloads (like any normal Download). Or just just move the Mouse to the Places Menu in the Upper Panel and select Downloads.

---

### Post by The_Accursed_One on 2010-11-04
I'm talking about the .etwolf folder. I found a folder called enemy_territory in usr/share/games/ but I can't write to that location without sudo so I'm still just as stuck.

---

### Post by WienerWuerstel on 2010-11-04
> **The_Accursed_One said:**
> I'm talking about the .etwolf folder. I found a folder called enemy_territory in usr/share/games/ but I can't write to that location without sudo so I'm still just as stuck.

It's in your Home Folder. Just press ctrl+h and you will see the .etwolf folder.

---

### Post by The_Accursed_One on 2010-11-04
I swear to you it is NOT there. I've looked for at least an hour now. It is simply not there.

---

### Post by The_Accursed_One on 2010-11-04
Okay wow. bs. Just found it. Thanks for the help all. I love you :3

---

### Post by Shpadoinkle on 2010-11-04
open a terminal and type ```
sudo nautilus
``` then enter your password
navigate to home/"your username" then press ctrl + h and you should see the .etwolf folder.

---

### Post by ahood on 2010-11-07
> **WienerWuerstel said:**
> 1. Install this Package ([http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb"))

2. Open a Terminal

3. ```
sudo apt-get update
```4. ```
sudo apt-get install enemy-territory
```5. Start Enemy Territory once and create a User

6. Download True Combat Elite 0.49 and the 0.49b Patch
    [http://www.filefront.com/6002126/True-Combat-Elite-.049/](http://www.filefront.com/6002126/True-Combat-Elite-.049/)
    [http://www.truecombatelite.com/files/tce049b_all_os_fixed.zip](http://www.truecombatelite.com/files/tce049b_all_os_fixed.zip)

7. Extract TCE 0.49 and put the Folder "tcetest" in "/home/yourusername/.etwolf

8. Extract the TCE 0.49b Patch and put the Content of the Folder in the "tcetest" Folder

9. Now TCE should be listed as a Mod in Enemy Territory

10. (Optional) Update Punkbuster with [http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

11. Have Fun :P

Unfortunately, the above instructions fail for me. I am running 9.04 (Jaunty) and the package 'enemy-territory' will not install. The following error message occurs....

> Err [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/games enemy-territory 2.60b-1~getdeb2
  404 Not Found
Failed to fetch [http://archive.getdeb.net/ubuntu/pool/games/e/enemy-territory/enemy-territory_2.60b-1~getdeb2_i386.deb](http://archive.getdeb.net/ubuntu/pool/games/e/enemy-territory/enemy-territory_2.60b-1~getdeb2_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

The above message indicates the package is unavailable for installation. Although the playdeb website indicates true-combat-elite is available for 9.04, maybe they dropped support for this release?

Is there another way to install?

DrH

---

### Post by realzippy on 2010-11-07
*The above message indicates the package is unavailable for installation*

..their server seems to be down in the moment.
when going to:[http://archive.getdeb.net/](http://archive.getdeb.net/)
it says:

[I]Recovering services...
Thanks for your patience. 
[/I]

..try again later.

---

### Post by The_Accursed_One on 2010-11-09
I got it completely installed. But its not to my liking so I took it off. My graphics card couldn't support it so I was like screw it. Surprisingly I put Unreal Tournament on my Windows system and it works like a charm? Weird because it has better graphics than TCE. Hmm.

---

### Post by WienerWuerstel on 2010-11-09
> **The_Accursed_One said:**
> I got it completely installed. But its not to my liking so I took it off. My graphics card couldn't support it so I was like screw it. Surprisingly I put Unreal Tournament on my Windows system and it works like a charm? Weird because it has better graphics than TCE. Hmm.

What Graphics Card do you have and do you use the Open or the Proprietary Drivers?

---

### Post by jakejw93 on 2010-11-10
errors i get after doing the instructions :

failed to load character files : characters/temperate/axis/soldiercharacter for axis soldier

And

Following packs missing :
nq/nq_vl.2.9_3.pk3
nq/nq_b_vl.2.9_5.pk3
etmain/purefrag.pk3


Any help will do, thanks in advance!

---

### Post by jakejw93 on 2010-11-14
Anybody?

---

### Post by g-raf on 2011-02-02
I recently installed tcetest through a .run file that I downloaded. Everything works except this: I try to join a server and the pk3 map files aren't downloading. It fails to connect me to any servers and a few times it just crashed. Then I found myself back on the desktop. Anyone have some advice for me?

---

### Post by Blabry on 2011-02-03
Hah...Thank u for instriction...I just have made to install it all works....BUT.... When i open Wolfenstain Enemy Teritory and go to mod, load added mod and its works....but i see only half of screen... I open configurantion for game and tryed diferent resolutions...allways the same... anybody have some idea what to do?

Btw Neewbe to Linux at all :D ):P

---

### Post by Jeloo on 2011-06-02
I have a same problem! :(
Until I lunch the mod it works fine but since I lunch etc I loose a part of the screen.
It works but the right part of the screen is hidden...
Please anybody know how to solve this?

Here is something strange  :

```
----- finished R_Init -----
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/joseph/.etwolf/tcetest/ui.mp.i386.so
Sys_LoadDll(/home/joseph/.etwolf/tcetest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xb3d93f40  
Sys_LoadDll(ui) succeeded!
WARNING: reused image ui/assets/fadebox.tga with mixed glWrapClampMode parm
execing profiles/Jelo/etconfig.cfg
```

The first line ```
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/joseph/.etwolf/tcetest/ui.mp.i386.so
``` copy ui.mp.i386.so in tce folder and thus remove the ui.mp.i386.so of tce...
I made a verification: before launching tce mod from et I have /home/joseph/.etwolf/tcetest/ui.mp.i386.so which is 411Kio and after I have  /home/joseph/.etwolf/tcetest/ui.mp.i386.so which is 340Kio.

Why does tce remove ui.mp.i386.so since ui.mp.i386.so is part of the tce049b_all_os_fixed patch? :confused:

---

### Post by Jarramundi on 2011-06-13
> **Jeloo said:**
> I have a same problem! :(
Until I lunch the mod it works fine but since I lunch etc I loose a part of the screen.
It works but the right part of the screen is hidden...
Please anybody know how to solve this?

Here is something strange  :

```
----- finished R_Init -----
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/joseph/.etwolf/tcetest/ui.mp.i386.so
Sys_LoadDll(/home/joseph/.etwolf/tcetest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xb3d93f40  
Sys_LoadDll(ui) succeeded!
WARNING: reused image ui/assets/fadebox.tga with mixed glWrapClampMode parm
execing profiles/Jelo/etconfig.cfg
```

The first line ```
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/joseph/.etwolf/tcetest/ui.mp.i386.so
``` copy ui.mp.i386.so in tce folder and thus remove the ui.mp.i386.so of tce...
I made a verification: before launching tce mod from et I have /home/joseph/.etwolf/tcetest/ui.mp.i386.so which is 411Kio and after I have  /home/joseph/.etwolf/tcetest/ui.mp.i386.so which is 340Kio.

Why does tce remove ui.mp.i386.so since ui.mp.i386.so is part of the tce049b_all_os_fixed patch? :confused:

I am also only seeing the left hand side of my screen, and if I change the resolution in options, it is still missing. Please anyone I have searched high and low for a fix but found nuddings.

---

### Post by Jeloo on 2011-06-14
this message is useless but i don't know how to remove it.
Sorry :(

---

### Post by Jeloo on 2011-06-14
Yeah that's really annoying :P
I tried to subscribe ont the TCE's forum commuity and I received this email :

> 
Welcome to TrueCombatElite.com Forums
 
Please keep this email for your records. Your account information is as follows:
 
----------------------------
Username: ***
Password: ****
----------------------------
 
Your account is currently inactive, the administrator of the board will need to activate it before you can log in. You will receive another email when this has occured.</quote>
and I'm still waiting... :|:???::(](*,)

---

