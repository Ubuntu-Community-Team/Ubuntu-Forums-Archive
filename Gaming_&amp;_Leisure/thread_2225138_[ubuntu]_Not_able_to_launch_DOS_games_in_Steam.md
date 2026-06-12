---
title: "[ubuntu] Not able to launch DOS games in Steam"
date: 2014-05-20
forum: Gaming &amp; Leisure
---

### Post by claes2 on 2014-05-20
So I'm on Ubuntu 14.04 and have Steam installed with great results.  To my great delight, my favorite game of all time, Wizardry 7: Crusaders of the Dark Savant (an old DOS rpg from back in the day) is released for Linux on Steam.  I am able to install it, but no launch.  

My questions... 

...has anyone else been able to play DOS games in Ubuntu especially Steam and second do you know what if anything I need to do to get it to work?

...and if not through Steam (which I would prefer) can I play DOS games in some other way?  I can download the game from GOG.com if I can get it to work in Ubuntu, and I would really, really like to.

Thanks in advance!

Claes

---

### Post by MikeCyber on 2014-05-20
You should be able to run it with wine and not from steam gui.

---

### Post by adec2 on 2014-05-20
If its a DOS game you will need DOSBOX, do a google search for it. It emulates a full DOS system configurable through a dosbox config that will run your game. As long as it is a DOS game and not a windows game then you will need WINE. Have you checked if Steam provides a version of your game for dosbox too?

---

### Post by claes2 on 2014-05-20
> **adec2 said:**
> If its a DOS game you will need DOSBOX, do a google search for it. It emulates a full DOS system configurable through a dosbox config that will run your game. As long as it is a DOS game and not a windows game then you will need WINE. Have you checked if Steam provides a version of your game for dosbox too?

It's a DOS game, so I'm given to understand that Steam runs it by running a DOSbox for the user, but that's the whole reason for my post: it's not launching.  I haven't tried to run a DOSbox myself yet though, so that's my next step.  I'll update in a couple of days.

---

### Post by mastablasta on 2014-05-21
well clearly ther eis a steam issue here... :-P

otherwise just install dosbox and then you can use a frontend for it such as dbgl (unfortunatelly not in the repositories) to setup the game and launch it. or you can always use CLI DOS in dosbox

---

### Post by oldrocker99 on 2014-05-21
OK, I went in to my Wiizardry 7 Steam directory. 

cd DSAVANT
dosbox DS.EXE

and it did run, in a tiny little window, but it did run.

---

### Post by mastablasta on 2014-05-22
alt+enter i think is for fullscreen in dosbox

---

### Post by claes2 on 2014-05-23
> **oldrocker99 said:**
> OK, I went in to my Wiizardry 7 Steam directory. 

cd DSAVANT
dosbox DS.EXE

and it did run, in a tiny little window, but it did run.

Ok, I'm trying to make sense of this. Stay with me please. I found the local folder in Ubuntu with the DOSbox config file which apparently attempts to run this set of commands, very close to yours:

[autoexec]
mount C ".."   
C:
CD DSAVANT
CLS
DS.EXE
EXIT

This file is called dosbox_wiz7_launch_linux.conf and located here:

[IMG]http://i1252.photobucket.com/albums/hh569/claesbuntu/9e2edf45-f458-468e-8fb1-f24f76a0da54_zps8e376245.png[/IMG]

I am not as technical in Ubuntu as I used to be in DOS yet, but it looks to me (and I'm not sure) that it is trying to tell DOSbox to mount the previous directory as C, then in the next line it just says C:, then it changes to the DSAVANT folder which **is** in the previous directory, not sure what CLS does, then launches the program with DS.EXE, then exits when we exit the game.

Perhaps it's getting hung up on the mount command?  Is that config file even in proper syntax?  This must be where the hangup is.

---

### Post by mastablasta on 2014-05-23
CLS is "clear screen" command.

you can give absolute path into mount c to be sure it mounts the correct folder as c:\. otherwise it seems fine to me.

---

### Post by Andrew_Gilbert on 2014-12-03
First thing, fullscreen:
look for this header in your DOSBox conf file for the game
```

[sdl] 
fullscreen=true
fulldouble=false 

```
Next, autoexec:
Autoexec is a tricky thing, and I suspect the mount command needs to have a static path not a relative path.  
I don't know how steam works, sadly.  but I know how it would work in both cases.  If you are using the linux native version of DOSBox your it will look different than the windows native version of DOSBox.  So that you understand the different, I'll show you the formats for a game that I play.  
If it's Linux native:
```

mount c /home/me/.wine/drive_c/MOO12 
c: 
cd \MOO2 
orion2.exe 
exit 

```
But if is wine running the windows version of DOSBox, you replace /home/me/.wine/drive_c with C:\ and replace path / with \.
Like so:
```

mount c C:\MOO12 
c: 
cd \MOO2 
orion2.exe 
exit

```
So check the path tree to your DOS .EXE file, and DOSBox type, and you should be able to figure it out from there.

EDIT: To clarify, I use the Windows version, because it is more stable than the linux native, but both work, just with one command difference.

---

