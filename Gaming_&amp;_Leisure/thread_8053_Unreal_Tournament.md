---
title: "Unreal Tournament?"
date: 2004-12-13
forum: Gaming &amp; Leisure
---

### Post by v79 on 2004-12-13
Hey Guys

Recently installed UT on windows, and now i'm trying for ubuntu. I downloaded an installed (v. 436) from the net, and it installed fine. But I can't get it to run:

$ /usr/local/games/ut/ut
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
appError called:
ReadFile beyond EOF 0+4/0
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down

Google hasn't been very forthcoming on this one. None of the solutions suggested seem to apply to these errors. Can anyone help?

Ta

V79

---

### Post by Mumbly on 2004-12-14
Try this website:

[http://www.icculus.org/](http://www.icculus.org/)

These guys are the ones that ported UT to Linux for  Epic Games, so they might be able to help.

---

### Post by fuzzix on 2004-12-19
I remember issues with UT installer and the map files post install - they were installed in a compressed format. If the Maps directory contains a bunch of *.unr.uz files that's the problem. If so, try this script:

```
#!/bin/bash

INSTALLDIR=***CHANGE THIS TO YOUR UT INSTALL DIRECTORY***

cd $INSTALLDIR/System

for i in `ls ../Maps/*.unr.uz`
do
ucc decompress ../Maps/$i -nohomedir
done

rm ../Maps/*unr.uz
mv *.unr ../Maps
```

Hope I got the syntax - it's from memory. I also had permissions issues - chmod all the datafiles +r. If you can handle the new Google Groups interface try that - it has more help than the web search. If you read Usenet you could try loki.games.ut on news.lokigames.com, but I doubt that group is very active these days.

---

### Post by blah09 on 2005-02-10
did you ever manage to get it to run?

i keep getting the following error:
```
$ ut
dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?
```

---

### Post by Kakalto on 2005-02-10
I'm not sure if this is applicable or not, but I used [this guide](http://www.princessleia.com/UT.html) to install UT GOTY, and it worked great.

Hope that helps.

---

### Post by Stratus on 2005-02-25
I tried the guide above, and I still get the same error blah09 got!

Can anybody else shed some light on this?

---

### Post by bored2k on 2005-02-25
[QUOTE=Stratus]I tried the guide above, and I still get the same error blah09 got!

Can anybody else shed some light on this?[/QUOTE]



private message sent stratus

---

### Post by TheOtherShoe on 2005-03-12
[QUOTE=blah09]did you ever manage to get it to run?

i keep getting the following error:
```
$ ut
dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?
```[/QUOTE]
You need to set the UT_DATA_PATH variable to point to ut's system files. Try the following command before running ut:
```
export UT_DATA_PATH=/usr/games/ut/System
```
If that doesn't work try this:
```
export UT_DATA_PATH=/usr/local/games/ut/System
```
or replace the path value with the one that is correct for your system.

---

### Post by Shantanu80 on 2005-10-19
[QUOTE=TheOtherShoe]You need to set the UT_DATA_PATH variable to point to ut's system files. Try the following command before running ut:
```
export UT_DATA_PATH=/usr/games/ut/System
```
If that doesn't work try this:
```
export UT_DATA_PATH=/usr/local/games/ut/System
```
or replace the path value with the one that is correct for your system.[/QUOTE]

Still getting the same error
dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?

Hey Stratus its me Pron here... i'm stuck right where you were mate.. but as I can see you did manage to sort it out.. i'm failing miserably lol.. Catch you on MSN someday
Cheers

---

### Post by Crazy Man on 2005-10-22
Tried the export, now getting the root-parent's error.

---

### Post by NiceGuy on 2005-10-27
I've just written a guide about this: [http://ubuntuforums.org/showthread.php?t=82987]("http://ubuntuforums.org/showthread.php?t=82987")

Hope it helps!

---

### Post by BLTicklemonster on 2005-11-01
[http://ubuntuforums.org/showthread.php?t=74623](http://ubuntuforums.org/showthread.php?t=74623)

There's how I did it.

---

### Post by Biased turkey on 2005-11-16
I tried to install UT-GOTY butthat didn,t work so I downloaded UT from:
[ftp://sunsite.dk/mirrors/lokigames/patches/ut/ut-install-436.run](ftp://sunsite.dk/mirrors/lokigames/patches/ut/ut-install-436.run)

Then followed the install procedure:
As sudo
mount /cdrom ( I don't think it was necessary, can't remember )
sudo bash ut-install-436.run

I still have to type:
export UT/DATA_PATH=/usr/local/games/ut/System

then type:
ut
to start the game.

I have 2 rigs ( both with Ubuntu 5.10 ) and installed UT on both of them.
The one with an Nvidia Geforce 6600 works nicely, the other one with a radeon 9600 is giving some sound proble, but the graphics are OK.

I'm not an UT fanatic, just install it, fire a few rounds to test my graphic card installation then exit the game.

---

### Post by weise on 2007-01-25
Hi,

I installed Ubuntu 6.10 x86_64.

I installed ia32-libs, ia32-libs-gtk, ia32-libs-openoffice.org, ia32-libs-sdl, ia32-sun-java5-bin, lib32asound2, lib32gcc1                                      , lib32ncurses5, lib32stdc++6, lib32z1.

I installed UT99 with sucess.

When I run ut, I get the following error:

> 
jurandy@weise:/usr/local/games/ut/System$ linux32 ./ut 
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
appError called:
Class Actor Member Owner problem: Script=48 C++=52
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down


Is there any way I can make it work???

Weise

---

### Post by weise on 2007-01-26
I resolved the problem.

The [www.liflg.org](www.liflg.org) create a new ut99 installer with 64bit support.

I downloaded [http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run]("http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run")
and installed ut99.

When I ran the game I got the following error:

> "/usr/local/bin/ut: 29: Syntax error: Bad substitution"

I applied this patch:

> --- ut.tmp      2007-01-26 11:28:00.000000000 -0200
+++ ut  2007-01-26 11:54:57.000000000 -0200
@@ -26,7 +26,7 @@
     
     if [ -L "$path" ]; then
         ll="$(LC_ALL=C ls -l "$path" 2> /dev/null)" &&
-       echo "${ll/* -> }"
+       echo "$ll" | sed -e "s/.* -> //" | sed -e "s/\*//"
     else
        return 1
     fi


And the game ran with sucess.

Weise

---

### Post by TremerePuck on 2007-03-13
I'm getting the same error myself.

```
"/usr/local/bin/ut: 29: Syntax error: Bad substitution"
```

How does one go about applying this patch?

---

### Post by celettu on 2007-03-13
No patch is needed. Just type

```
sudo dpkg-reconfigure bash
```

and answer "no".

Edgy uses dash instead of bash...

---

### Post by AJB2K3 on 2007-03-16
I fixed mine bady by installing all mods on XP then ripping the whole install to cd and copying the files to Ubuntu install

---

### Post by eternalwolfman on 2007-04-28
hi! i just attempted to install ut (standard version) and it seemed to install fine. however, when i open up terminal, go to my ut directory, and type ut, i get the message "bash: ut: command not found"
when i type dir, in that directory, it shows that the file ut is there. im not sure whats going on =\

-greg.

---

