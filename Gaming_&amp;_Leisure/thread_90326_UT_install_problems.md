---
title: "UT install problems"
date: 2005-11-14
forum: Gaming &amp; Leisure
---

### Post by mrpixels0 on 2005-11-14
i got an error but i have never seen this one before:

Verifying archive integrity...OK

Uncompressing Unreal Tournament version 428 

Linux installtrap: usage: trap [-lp] [arg signal_spec ...]

well, i guess it is not an error but it stops at the last line and doe's nothing, doe's any one know what the installer is looking for ?.

Note: this has worked on other versions of linux suse,mandrake,redhat ect, this is the first time i have seen this before in linux.

thanks for any help you can provide.

Mr.pixels0

---

### Post by tjotser on 2005-11-15
I have UT   on two cds (GOTY)
I always use this script :
[http://www.princessleia.com/UT.html](http://www.princessleia.com/UT.html)
hope this helps

---

### Post by mrpixels0 on 2005-11-15
[QUOTE=tjotser]I have UT   on two cds (GOTY)
I always use this script :
[http://www.princessleia.com/UT.html](http://www.princessleia.com/UT.html)
hope this helps[/QUOTE]
Hi, there tjotser ! :)
thanks for the reply but the procedure there is for Debain distros like Sarge,woody, potato ect. some of the commands listed do not exist in Ubuntu's version of Debian.

i got away from woody becuase of a lot of problems were slow to be fixed mainly security issues but that was back in 93 or 94.

but also the instructions are for a "normal edition of GOTY"  (the red dics), mine is a version of UT99 (the Blue disc) that came with my Creative Labs sound card and there for when i use the ut-install-436-GOTY.run script it tells me the to put the CD in the cdrom and click begin install but when i do it doe's not  "SEE" the cd and refuses to complete the install of the game. 

now if you could tell me exactly how you did it preferably with Ubuntu version 5.04 which is what i am using now, i would be very greatful to you.

Mrp

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

### Post by BLTicklemonster on 2005-11-16
Try this: [http://ubuntuforums.org/showthread.php?t=74623](http://ubuntuforums.org/showthread.php?t=74623)

ONce installed, you just type ut 

even niftier, create a launcher (rt click on desktop, choose create launcher) and the command is 

/home/yourwhatever/ut/System/ut

and I have mine set to launch from the terminal

---

### Post by mrpixels0 on 2005-11-16
well i have tried all the methods known to man and still no way to get it to work :(, it keeps asking for CD 1, even though CD1 is mounted in the drive and i am root. below is a screen shot link maybe there is somthing am not doing i don't know what else to do :(.

[ATTACH]3634[/ATTACH]

all the programs i install or compile have gone smoothly and by the numbers this the first time i have had this much trouble with installing somthing, i would like to take the time and thank everyone for thier help and thier patience with me.

Mr.pixles0

---

### Post by BLTicklemonster on 2005-11-16
Try this:

[http://liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run](http://liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run)

and see if that one will work.


(you are installing ut game of the year 432, right?)

---

