---
title: "Zandronum opens in Tiny window with no maximize"
date: 2020-04-28
forum: Gaming &amp; Leisure
---

### Post by jcdenton1995 on 2020-04-28
Hello all,

- Toshiba Satellite -C870D-11X
- AMD® E2-1800 apu with radeon(tm) hd graphics × 2
- Ubuntu 18.04 LTS 64bit with GNOME 3.28.2 desktop

I've installed Zandronum for Ubuntu and have been having some problems with it.

I can run it by double clicking the executable in "/usr/games/zandronum" however it opens in a very small window with no option to maximize.

if I want to run the brutal doom mod with it I cant right click "brutalv21.pk3" and select "open with other application > Zandronum" as nothing happens, but rather I have to open a terminal and run "Zandronum -file brutalv21.pk3" but when I do that, the game opens and runs fine except again its in a tiny window with no option to maximize. 

my questions are...


[LIST=1]
[*]Can anyone tell me how to run the brutal doom mod without having to open a shell (i.e graphically) 
[*]Can anyone tell me how to run the game in a maximized window? 
[/LIST]

Thanks!

---

### Post by mastablasta on 2020-04-29
> **jcdenton1995 said:**
> 


[LIST=1]
[*]Can anyone tell me how to run the brutal doom mod without having to open a shell (i.e graphically)
[*]Can anyone tell me how to run the game in a maximized window?
[/LIST]


create a launcher and enter that command. you might need to add additional command to run it in full screen. if Znadonum has a console you can sometimes load mods through that as well.

i forgot which one was the last one i tried. but, is Zandronum more oriented towards multiplayer with server lists etc?

anyway i plan to give Doomday engine a try. it brings doom to a new level. i used to play jdoom before on winXP.

---

### Post by Holger_Gehrke on 2020-04-29
1. How did you install zandronum ? If you installed it according to [the instructions]("https://zandronum.com/download#instubuntu"), a .desktop file should have been put in /usr/share/applications/zandronum.desktop. This file provides the integration into the graphical environment, both by putting an item into the Activities view of the desktop and by putting the program into the list of applications to open files with. Works without any problems on my system (XUbuntu 18.04, but the mechanism for integration is the same between Gnome and XFCE).

2. Zandronum is a source port of Doom, which was written for MS-DOS. Since DOS-Programs could not rely on the OS to do anything graphical for them, they did everything themselves. Because of that history you have to configure the size of the window or the resolution in fullscreen mode inside the program (Main Menu->Options->Set Video Mode).

Holger

---

### Post by jcdenton1995 on 2020-04-29
I installed the way that is outlined on the website, the .desktop file is there as I had to add "%F" to the details of some part of it in order to have it show up as an application that other files can be run with.

Thanks for the heads up on the resolution issue, I have only previously played zandronum on windows and I don't seem to remember having the same issue, maybe because windows stretches the resolution to fill the screen? I cant fully remember.

I obviously didn't install Ubuntu to play games but now I can see why people say it requires some tweaking sometimes to work, thanks for taking the time to reply!

---

### Post by jcdenton1995 on 2020-04-29
Well Zandronum calls itself a Multiplayer oriented source port, and maybe it is, but the single player seems really good, although it is the only sourceport I have ever tried. I did play some multiplayer but it was all co-op and very few deathmatch servers so I kind of binned it, which was strange as I would have expected the other way around, but having played very few games online, and those I have played pretty much been COD, perhaps I just hadn't come across a community like the DOOM one before.

---

### Post by mastablasta on 2020-04-30
try doomsday engine. i like the special effects, the openGL grpahics and 3D models.

yes, linux requires some tweaking if you run windows or DOS based games on it. makes sense since t's a different OS. if you load linux games, then all you do is install and run. similarly with these ports. if they were properly made, they work out of the box.you just add the files and they work. but if not and if they are not maintained (updated) then you need to add, remove or change something.

btw COD plays on linux well wine or play on linux out of the box. so far i installed COD2, COD:4MW, and COD:MW2. CoD2 needed some small tweak if i remember correctly, the other two are platinum, so just install and it works.

ports that will run windows games natively in linux and that i tried are: Quake 4, Doom 3, OpenTTD and OpenMW (for Morrowind). apart from OpenMW and OpenTTD, the Doom3 and Quake4 both need some small tweaks and a change to config file.

next one on my list is OpenRA (to play Red alert and C&C natively).

Proton and Lutris provide good scripts, so that all necessary tweaks for windows games are done automatically in the background.

---

### Post by jcdenton1995 on 2020-05-01
Thanks, I suppose that does make sense. Because I'm totally new to Ubuntu, totally new to Linux in fact, it's a huge chore configuring games, but I'm hoping the learning curve is steep and fast (but I have a feeling it wont be)

I've played some open RA and it plays quite nicely even on my steam engine of a laptop, but unfortunately I don't play it much as straining to see all the tiny units gives me headaches :D

---

