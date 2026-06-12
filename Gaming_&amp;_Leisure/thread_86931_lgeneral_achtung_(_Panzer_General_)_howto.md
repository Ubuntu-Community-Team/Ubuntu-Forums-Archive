---
title: "lgeneral achtung ( Panzer General ) howto"
date: 2005-11-06
forum: Gaming &amp; Leisure
---

### Post by Biased turkey on 2005-11-06
1)Using synaptic install:
lgeneral
lgc-pg

Lgeneral package installs:
a) lgeneral ( binary  executable ) in /usr/games
b) /usr/share/games/lgeneral folder
c) doc in /usr/share/doc/lgeneral

lgc-pg installs:
a) lgc-pg ( binary executable ) in /usr/bin
b) /usr/share/games/lgc-pg folder
c) /usr/share/doc/lgc-pg folder
d) man in /usr/share/man/man6

2) open a console and type "lgeneral" just to check that the binary is working.
Remember, we don't have any installed scenario yet
Exit the game.

3) from 
[http://lgames.sourceforge.net/index.php?project=LGeneral](http://lgames.sourceforge.net/index.php?project=LGeneral)
download "pg-data.tar.gz"
Untar and unzip it to your home directory.
You now have the "pg-data" folder in your home dir


4) Installing the data:
Obviously, the person who created the lgc-pg Ubuntu package ( thanks to him/her ) did a few small mistakes, but we'll correct them.
So, with the "sudo nautilus" command open the pg-data folder and rename the following files:
flags.shp to FLAGS.SHP
tacicons.shp to TACICONS.SHP
explode.shp to EXPLODE.SHP
tacmap.shp to TACMAP.SHP
scenstat.bin to SCENSTAT.BIN

Now, we are ready to install the data using the lgc-pg program.
lgc-pg needs 2 directories:
a) the source  directory ( where the pg-data dir is located. In our case, our home directory )
b) the destination directory ( where to install the data, in our case, /usr/share/games/lgeneral )
So, open a console and type ( in 1 line )

sudo lgc-pg -s /home/YourHomeDirectory/pg-data -d /usr/share/games/lgeneral

If successful, that's the message you should get:
LGeneral Converter for Panzer General (DOS version) v0.32
Copyright 2002 Michael Speck
Released under GNU GPL
---
Settings:
  Source: /home/bourdouj/pg-data
  Destination: /usr/share/games/lgeneral
  Use Individual Palettes
Converting:
  nation database...
  nation flag graphics...
  unit data base...
  unit graphics...
  terrain database...
  terrain graphics...
  maps...
  scenarios...
Done!

---

### Post by pappo on 2005-11-11
Does this game require that you own Panzer General cdrom ?

---

### Post by Biased turkey on 2005-11-13
[QUOTE=pappo]Does this game require that you own Panzer General cdrom ?[/QUOTE]

Oups, sorry, I forgot about that post.
To answer your question: No, You don't need to own the Panzer General CDROM.
The PG data are available at the link I mentioned in the item 1) of my post.
The name of the data file to download is:
pg-data.tar.gz

---

### Post by pappo on 2005-11-13
I downloaded the pg-data and followed your instructions to run the lgc-pg executable to convert the data.

lgeneral loads and I see the game screens, but there is nothing in the campaigns or scenario menus.
I checked /usr/share/games/lgeneral/campaigns and scenarios directories and nothing is in them.

I tried downloading some of the custom scenarios but cannot get them to work either.

Any help would be appreciated.

pappo

---

### Post by Biased turkey on 2005-11-14
[QUOTE=pappo]I downloaded the pg-data and followed your instructions to run the lgc-pg executable to convert the data.

lgeneral loads and I see the game screens, but there is nothing in the campaigns or scenario menus.
I checked /usr/share/games/lgeneral/campaigns and scenarios directories and nothing is in them.

I tried downloading some of the custom scenarios but cannot get them to work either.

Any help would be appreciated.

pappo[/QUOTE]

I agree, the campaigns directory is empty, but at least I got some scenarios in the /usr/share/games/lgeneral/scenarios directory.
Did you get any error message when running the data installation script ( item 7 ) ?

---

### Post by pappo on 2005-11-17
Here is the results from doing item 7:

pappo@ubuntu:~/lgeneral/lgeneral-1.2beta-9/lgc-pg$ sudo /usr/bin/lgc-pg -s /home/pappo/lgeneral/pg-data -d /usr/share/games/lgeneral
Password:
LGeneral Converter for Panzer General (DOS version) v0.32
Copyright 2002 Michael Speck
Released under GNU GPL
---
Settings:
  Source: /home/pappo/lgeneral/pg-data
  Destination: /usr/share/games/lgeneral
  Use Individual Palettes
Converting:
  nation database...
  nation flag graphics...
  unit data base...
  unit graphics...
/home/pappo/lgeneral/pg-data/TACICONS.SHP: file not found

---

### Post by pappo on 2005-11-17
I went back and checked pg-data and found that TACICONS.SHP was in lowercase in my pg-data directory so I changed it to upper case.  I also did the same for EXPLODE.SHP, TACMAP.SHP, and SCENSTAT.BIN and then it worked.

When I reran the "item 7" command, this was the result:

 sudo /usr/bin/lgc-pg -s /home/pappo/lgeneral/pg-data -d /usr/share/games/lgeneral
LGeneral Converter for Panzer General (DOS version) v0.32
Copyright 2002 Michael Speck
Released under GNU GPL
---
Settings:
  Source: /home/pappo/lgeneral/pg-data
  Destination: /usr/share/games/lgeneral
  Use Individual Palettes
Converting:
  nation database...
  nation flag graphics...
  unit data base...
  unit graphics...
  terrain database...
  terrain graphics...
  maps...
  scenarios...
Done!
.................................
Then when I checked my scenarios directory it looked like this:
 ls /usr/share/games/lgeneral/scenarios/pg
Anvil       Berlin       Caucasus     ElAlamein  Kursk         Moscow42     Sealion40    Torch
Anzio       BerlinEast   Cobra        France     LowCountries  Moscow43     Sealion43    Warsaw
Ardennes    BerlinWest   Crete        Husky      MarketGarden  NorthAfrica  SealionPlus  Washington
Balkans     Budapest     D-Day        Kharkov    MiddleEast    Norway       Sevastapol
Barbarossa  Byelorussia  EarlyMoscow  Kiev       Moscow41      Poland       Stalingrad


Thanks for all your help.

pappo

---

### Post by Biased turkey on 2005-11-20
So, you did it Herr General.
I found it strange that some of your Panzer-general fils are in uppercas.My data files were all lower-case so I didn't have that problem.
Where did you download the data files from ?
There are som axtra scenarios an campaigns at:
[http://lgames.sourceforge.net/index.php?project=LGeneral&sub=Scenarios]("http://lgames.sourceforge.net/index.php?project=LGeneral&sub=Scenarios")
As I was born in Belgium , I'll try to install the Bastogne ( Battle of the Bulge ) tonight and try to sink the Bismark too.

---

### Post by pappo on 2005-11-23
Biased Turkey

Thanks for all your replies and assistance.
Yes, it was strange about the "case issue".
I downloaded the files from the location in your original post.  
Oh well, it works now and that is fine with me.  It is great to play these strategy games on the computer.  No dice rolling and pages of manuals to read.

I did download some "extra" scenarios when I was at that original download site, but I cannot seem to get them to work.
What do you do to add these extra scenarios ??  Do you use the lgc-pg command for them as well.

I don't know if you celebrate Thanksgiving where you live, but if you do let me wish you a good day.

Regards,

Pappo

---

### Post by tim15856 on 2005-11-24
Perhaps someone can help me to get this to work. I installed the game through Synaptic. I then downloaded both files from sourceforge. After I unzip them, I have two folders; pg-data and lgeneral-1.2beta-9. Inside the lgeneral folder is a folder named lgc-pg, but no executable of that name. Could someone please help this poor newbie?

---

### Post by Clunsford on 2005-11-24
thanks for the help!

---

### Post by Biased turkey on 2005-11-24
[QUOTE=tim15856]Perhaps someone can help me to get this to work. I installed the game through Synaptic. I then downloaded both files from sourceforge. After I unzip them, I have two folders; pg-data and lgeneral-1.2beta-9. Inside the lgeneral folder is a folder named lgc-pg, but no executable of that name. Could someone please help this poor newbie?[/QUOTE]

I apology, maybe I forgot to mention some extra steps in the process.
Like in the item 1) how to create the lgc-pg binary:
Let's assume that the lgeneral-1.2beta-9.tar.gz was untar and unzip in our home directory:
1a) "cd" ( to be sure we are in our home dir )
1b) "cd lgeneral-1.2beta-9" ( we are in the lgeneral dir now )
We'll now compile the lgeneral source to extract the lgc-pg binary
1d)" ./configure"
1e) "make"
1f) "sudo make install"

Tonight, I'll remove  the Lgeneral package, reinstall it , write down every step so I can edit my original post.
I don't want my HOWTO to confuse more than it helps.
The only reason why we have to compile the lgeneral source is to extract the data installer, we don't need the rest because that was installed when using synaptic to install the lgeneral package.

So, if you can hold on a few more hours :)
Or try it by yourself with those few extra details

I have to admit that it took me 2 hours to have a workable Lgeneral.

---

### Post by tim15856 on 2005-11-24
[QUOTE=Biased turkey]So, if you can hold on a few more hours :)
Or try it by yourself with those few extra details.[/QUOTE]


I still have four hours until I get off of work, so I can wait :-) I really appreciate your help.

---

### Post by Biased turkey on 2005-11-24
[QUOTE=tim15856]I still have four hours until I get off of work, so I can wait :-) I really appreciate your help.[/QUOTE]

I  completely rewrote my original post ( check it ) because at that time I didn't know that Ubuntu includes the lgc-pg package too, I just discovered that tonight.
Tomorrow, I'll explain how to add new scenarios ( I just dit it 5 minutes ago and it works nicely ).
 See ya

Biased "Rommel" turkey :)

---

### Post by tim15856 on 2005-11-25
Very good. It's working now. Just need to get sound working. I found the sound files and they play fine in Totem. Also need to get some campaigns added. Thanks a lot for your help.

---

### Post by Biased turkey on 2005-11-25
[QUOTE=tim15856]Very good. It's working now. Just need to get sound working. I found the sound files and they play fine in Totem. Also need to get some campaigns added. Thanks a lot for your help.[/QUOTE]

I'm glad it works for you.
About that sound problem , I really can't help because the sound always worked nicely with any application.

Just to give you a moral support I'll tell you how to add extra scenarios:

1) Goto the Lgeneral website on the page where you can  download additional scenarios:
[http://lgames.sourceforge.net/index.php?project=LGeneral&sub=Scenarios]("http://lgames.sourceforge.net/index.php?project=LGeneral&sub=Scenarios")

2) Let's select a new scenario to download , Bismark 1.0 for example
To download a scenario right-click on the disk symbol, choose Save link document as... and save it somewhere to the scenarios directory of your LGeneral installation.

And voil&#224;

I didn't try a campaign because I'm not a Panzer general expert and can barely handle tough scenarios.

If you can get the Windows program "Panzer General Scorched Earth"  ( From Ubisoft ) don't miss that. It's Lgeneral but in 3D.
That program is discontinued but I got my version on Ebay ( The 1st time in my life I ever purchased some item on Ebay ) and I paid $ 8.00 for it.

P.S. I still suggest to download the Lgeneral source code "lgeneral-1.2beta-9.tar.gz" and unzip it because it contains some icons that can be used if you add Lgeneral to the games menu.

---

### Post by tim15856 on 2005-11-25
[QUOTE=Biased turkey]P.S. I still suggest to download the Lgeneral source code "lgeneral-1.2beta-9.tar.gz" and unzip it because it contains some icons that can be used if you add Lgeneral to the games menu.[/QUOTE]

Yep, that's where I got a png of a tank that I used in the menu.

---

### Post by DirtDawg on 2006-10-23
I've been trying to get this to work for awhile now and this method seems the most promising. But when I follow the instructions, when I enter the command:
```
 sudo lgc-pg -s ~/pg-data -d /usr/share/games/lgeneral 
```
a window opens labeled "??", which is completely black. Then the terminal prints:
```
 LGeneral Converter for Panzer General (DOS version) v0.32
Copyright 2002 Michael Speck
Released under GNU GPL
---
Settings:
  Source: ~/pg-data
  Destination: /usr/share/games/lgeneral
  Use Individual Palettes
Converting:
  nation database...
  nation flag graphics...

```
and freezes.

Any help would be appreciated. I'm more interested in just getting things to work than actually playing the game at this point :D

EDIT: I'm using a PPC, which may or may not be an important point.

---

### Post by braddcadd on 2006-11-22
message removed

---

### Post by tim15856 on 2006-11-24
> **DirtDawg said:**
> I've been trying to get this to work for awhile now and this method seems the most promising. 

Have you tried to install via Synaptic? It's in the repos now.

---

### Post by Ivkosky on 2010-06-24
Did everything according to HOWTO, also changing to upper case, but still:

> LGeneral Converter for Panzer General (DOS version) v0.32
Copyright 2002 Michael Speck
Released under GNU GPL
---
Settings:
  Source: /home/ivkosky/pg-data
  Destination: /usr/share/games/lgeneral
  Use Individual Palettes
Converting:
  nation database...
  nation flag graphics...
  unit data base...
  unit graphics...
  terrain database...
  terrain graphics...
  maps...
  scenarios...
/home/ivkosky/pg-data/SCENSTAT.BIN: file not found


Please help!

---

### Post by CKeizer on 2011-02-23
What does "sudo nautilus" enable me to do?

More to the point, why does lgc-pg fail to find files when I properly changed their names to all capitol letters?

Is there some special magic required to rename a file from lower case to upper case letters?

Thanks,

Colin Keizer

---

### Post by Perfect Storm on 2011-02-24
Necromancing. Thread closed.

---

