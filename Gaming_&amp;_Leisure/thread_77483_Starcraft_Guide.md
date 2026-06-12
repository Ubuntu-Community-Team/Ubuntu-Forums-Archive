---
title: "Starcraft Guide?"
date: 2005-10-16
forum: Gaming &amp; Leisure
---

### Post by programgeek on 2005-10-16
Can some Ubuntu Genius here guide me through installing starcraft+ broodwar on Breezy?  Then after that play with me all night?

---

### Post by psychicdragon on 2005-10-17
Hey,

I've recently managed to get Starcraft working near flawlessly in Breezy after a little bit of tweaking. Battle.net works fine except that the font's are a little messed up.

The first thing you need is Cedega. You can get it by paying these guys: [Transgaming]("http://www.transgaming.com/") or from CVS by following [this guide]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45"). It takes a little while but is quite straight forward to install.

Run cvscedega for the first time to create the config file. Then open ~/.transgaming/config in your favorite text editor. Most of the default options seem to work fine with Starcraft but there is one option you'll have to change or Battle.net will crash on you. 

In the [fonts] section add this line:```
"FreeType" = "N"
```It should already be there but commented out.


Now you can install Starcraft from the CD:
```
cvscedega /media/cdrom/setup.exe
```
Repeat this with the Brood War CD if you have it.


To run Starcraft:
```
cvscedega "/home/david/.transgaming/c_drive/Program Files/Starcraft/starcraft.exe"
```


If you notice poor performance like the mouse moving really slowly. Launch Starcraft like this instead:
```
nice -n 20 cvscedega "/home/david/.transgaming/c_drive/Program Files/Starcraft/starcraft.exe"
```This forces Cedega to have the highest priority which seems to solve the slowdown issue.

---

### Post by reub2000 on 2005-10-17
Vanilla wine can be used to run starcraft, and wine is completly free. WIne can also run many other blizarrd games, IE6, and a bunch of other windows apps. Add the universe repository to apt. (Pretty simple using synaptic.) The install wine using "apt-get install wine" or install using synaptic. Or get a more update to date version from winehq.com.

First configure wine by running "winecfg". For audio in starcraft go to the audio tab, and set hardware acceleration to "Emulation" and enable driver emulation. Also make sure to set up your cd drives in the drives tab. The autodetect button should work for the drives.

---

### Post by Iesos on 2005-10-26
I'm realy new at linux.
With that said...
Can someone give me a realy detailed "How to" for starcraft installation becouse non of all i have found works. And please, dont give me any sugestions about some software i have to buy, couse i allready bought Starcraft, and its not worth spending more money (especially if they are not blizzard).
So please, can someone give me a good link or how to!

---

### Post by blackant on 2005-11-17
Hope to see a step by step guide on wine.
Can anyone help?

Thanks.

---

### Post by kemik on 2005-11-26
it's been said above, but here goes:


1: install wine => 'sudo apt-get install wine'
2: run winecfg => 'winecfg'
3: in winecfg => autodetect sound and autodetect drivers, then exit winecfg
4: insert Starcraft CD.. rightclick executable "setup.exe" and choose open with Wine Windows Emulator
5: repeat step 4 but with Broodwar cd.

---

### Post by blackant on 2005-11-26
[QUOTE=kemik]it's been said above, but here goes:


1: install wine => 'sudo apt-get install wine'
2: run winecfg => 'winecfg'
3: in winecfg => autodetect sound and autodetect drivers, then exit winecfg
4: insert Starcraft CD.. rightclick executable "setup.exe" and choose open with Wine Windows Emulator
5: repeat step 4 but with Broodwar cd.[/QUOTE]
I did manage to install, but it keep asking me for the cdrom when starting the game when the cdrom is already inside.. :(

---

### Post by cdsboy on 2005-11-27
Go back to the wine configure ("winecfg" in terminal) and go to the drives tab, then add a new drive, then click that drive and change the path to "/cdrom/" and the type to CD-ROM. and you should be set.

---

### Post by TherapyQuestionMark on 2005-11-30
[QUOTE=psychicdragon]

If you notice poor performance like the mouse moving really slowly. Launch Starcraft like this instead:
```
nice -n 20 cvscedega "/home/david/.transgaming/c_drive/Program Files/Starcraft/starcraft.exe"
```This forces Cedega to have the highest priority which seems to solve the slowdown issue.[/QUOTE]

I'm having some poor performance running it with wine 9.1. 
Is there a similar fix for wine?

---

### Post by stimpson on 2005-12-05
you can change the priority of any process by setting 'nice'
I suppose this starts wine with highest priority:

```

nice -n 20 wine "/home/david/.transgaming/c_drive/Program Files/Starcraft/starcraft.exe"
```

---

### Post by blackant on 2006-01-16
The latest problem I had is unable to connect to battlenet...:confused: 

It says something about unable os etc, then blank screen with only my mouse around. :( I couldn't get out and have to do a cold restart.

Anyone can offer advise?
Thanks.

---

### Post by blackant on 2006-01-16
I am able to get into the battlenet using the latest patch from blizzard but the colours in the chatroom is horrible.

Also the message is stacking over each other without any refresh...

Anyone can help?

---

### Post by Iesos on 2006-01-17
FINALY! I've just got starcraft working! Thanks guys!
But, I'm still not pleased. I cant play, it seems as my computer is too slow (but it isn't, its just a 700 MHz but thats plenty for starcraft). I tried to use nice, but it didnt help. Im thinking that some of the outprints of errors might give a clue. This is everything that wine/starcraft prints when i run it:

> Warning: the specified System directory L " c : \ \ windows \ \ system32" is not accessible.
Xlib:  extension " GLX " missing on display " : 0 . 0".
fixme : ddraw : Main_DirectDraw_SetCooperativeLevel (0x7fdf8e90) - > (0x 10022,00000013) fixme : xrandr : X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme : xrandr : X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme : x11drv : X11DRV_DDHAL_CreatePalette stub
fixme : wave : DSD_CreateSecondaryBuffer (0 x 7fdfa620,0 x 7fb1fcc4,c2,0,0 x 7fe2e40c,0 x 7fe2e51c,0 x 7fe2e3e8) : stub
fixme : wave : DSD_CreateSecondaryBuffer (0x7fdfa620,0x7fb1fc9c,80,0,0x7fe4ed34,0x7fe2e2d4,0x7fe4ed10) : stub
...
fixme : wave : DSD_CreateSecondaryBuffer (0x7fdfa620,0x7fb1fbb8,c2,0,0x7fe8fce4,0x7b90abac,0x7fe8fcc0) : stub

Can someone help me fixe these or get me in the right direction where I can find some sort of How To?

---

### Post by LordMelkor on 2006-02-24
I was able to get StarCraft BroodWar up and running just fine with wine, everything works fine, although it is a bit slow, even with high priority (i am using 1ghz system), but doesnt really affect gameplay.  I can connect and play games on battle net just fine BUT... i get the following problem on battlenet

When i connect to battle.net none of the backgrounds show up, and all the fonts seem to stack up on eachother (in layers... its trippy), so unless you know where to click you wont be able to enter games/ switch channels and such. Has anyone else encountered this problem.. and what is the fix?

---

### Post by blackant on 2006-02-24
I have the same problem as you... doesn't seem to be a fix for it. :(

---

### Post by LordRaiden on 2006-02-24
I have the same problem as well, but I've seen somewhere (i think the winehq site) saying that they know about the issue (something about improper repainting). I'm also using Warcraft 3 in OpenGL mode which works well.

I tried winex/cvscedega but I always get stuck at the very end (the config files get overwritten all the time). I'd try it again but i need a better install guide than just getting ./tools/wineinstall.

---

### Post by sYs^ on 2006-03-16
i have the same problem, when i try to connect to the battlenet, my starcraft simply shut down :\

any ideas?

---

### Post by polpak on 2006-03-16
[QUOTE=sYs^]i have the same problem, when i try to connect to the battlenet, my starcraft simply shut down :\

any ideas?[/QUOTE]

It's probably trying to load the patch from battle net. Try instead going to their website, and DL the patch from there. Then install it with wine and you shouldn't have any trouble.

---

### Post by pdobrev on 2006-03-16
I play SC via Wine with no problems except for I can't run it in fullscreen mode - the game screen stays 640x480 and the rest of the screen is just black.
Anyone has an idea why is that so?

---

### Post by sYs^ on 2006-03-17
polpak: i have the patch installed :\

but it's working perfectly with cedega, unfortunetly it isn't that fast like wine :\

---

### Post by RioMerc on 2006-04-13
I can't run bnet either, and It's the only reason I play SC, any fix?

((Sorry for ressurection))

---

### Post by Iesos on 2006-06-13
I haven't seen any fix. WineHQ has it as a know bug, and doesn't seem to do much about it (well, maybe they are, but not what I know of).

---

### Post by homerhomer on 2006-06-14
Hey, I was able to run Starcraft.

I'm running the latest wine from winehq (0.9.15)
fullscreen and everything

---

### Post by pdobrev on 2006-06-14
Even bnet?

---

