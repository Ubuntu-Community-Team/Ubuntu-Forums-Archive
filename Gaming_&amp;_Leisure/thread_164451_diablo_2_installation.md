---
title: "diablo 2 installation"
date: 2006-04-22
forum: Gaming &amp; Leisure
---

### Post by kookookachooo on 2006-04-22
hi, i just recently moved to linux, choosing to wipe out windows. so im practically a N00b in the linux world.i have read the other  diablo installation threads and they dont seem to be helping me. i need help setting up and dling wine. could someone give me a step by step guide to help me install wine to install diablo2? and LoD? thanks in advanced.

---

### Post by gondilon on 2006-04-22
to install wine, you can use synapyic by setting it up to get packages from the debian server ( the example site in the box that pops up when you create a new repositroy.) To install diablo 2 , just run the installer with wine. FOr more help go to the wine games web page at the link below:
[http://www.winehq.com/site/about](http://www.winehq.com/site/about)

---

### Post by nashife on 2006-04-22
I also can't install diablo with wine... it always tells me to insert a cd when I enter wine /media/cdrom1/install.exe.

Does anyone know how to solve this issue? the installer claims that the cd is not inserted when it clearly is inserted.  If it wasn't inserted, i wouldn't be able to perform any command on the install.exe file.

---

### Post by tarasbulba on 2006-04-23
Hello,i have found something about your problem from somewhere( i can't remember where):
> From CD you need to launch the wine configuration utility first.

winecfg

Once you've done that switch to the "Drives" tab. Click on "Add" to create a new drive and write down the drive letter somewhere, you'll need it later. Now highlight your newly created drive entry and expand the info by clicking on "Show Advanced". Now enter the path of your CDROM's mountpoint in the "Path" field and select CDROM as "Type". Finish the setup by pressing the "Apply" button and then exit the configuration utility by pressing "OK". Insert the first WoW disk and mount your CD. Then open a Console and type in the command to launch the install.

wine d:\setup.exe

Where d:\ is only a example. You have to replace the "d" with the drive letter you assigned during the wine configuration. If you're asked to insert the second CD simply unmount your CDROM, insert the second one and go on with the Diablo install - it will recognize the CD's properly now. 

---

### Post by kookookachooo on 2006-04-23
thanks, When i typed in winecfg and i got a :

Warning: could not find DOS drive for current working directory '/home/richard', starting in the Windows directory.

the wine config proceeded and i jsut ignored that, i was wondering whats that mean?

Afterwards i went to the drivers tab and made the driver but what do i put for path? "/cdrom/"? well i typed that in and put autodetect for "the label and serial". i applied and closed the box. Waht do you mean by mounting it? i skipped that part and procceeded, the diablo install came up, blah blah blah and after i entered the cdkey there was an error:

exp1:Error 0x000000003: path not found

Could someone tell me what to do? thanks in adv.

---

### Post by tarasbulba on 2006-04-27
Hello again,you should look at [http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine]("http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine")
if you setup wine correctly.I can install and play Diablo II LOD 1.11b perfect.

---

### Post by Griff on 2006-04-28
And after wine is installed go here:
[http://appdb.winehq.org/appview.php?versionId=49](http://appdb.winehq.org/appview.php?versionId=49)

After you've installed D2 and possibly LOD; go here for the latest patch:
[http://www.blizzard.com/support/?id=mdt0387p](http://www.blizzard.com/support/?id=mdt0387p)
Download the patch from above and save anywhere.  Double click to install.

See you on the realms.  8)

---

### Post by RobyX on 2006-04-28
There is just way to many problems and obstacles to get thru installing games on Linux, if you want to go thru all the frusteration and such to get a half working game that might not even work properly. Or you can get a duel boot with win2k/xp just to play games.

---

### Post by Griff on 2006-04-29
[QUOTE=RobyX]There is just way *too* many problems and obstacles to get thru installing games on Linux, if you want to go thru all the frustration and such to get a half working game that might not even work properly. Or you can get a dual boot with win2k/xp just to play games.[/QUOTE]
This isn't a debate thread.  And, btw, some of us derive satisfaction from our triumphs over little 'obstacles' like the one above.  We try to better our computing experience, which is what I was trying to help the fellow ubuntu user above accomplish.  Dual booting to allow D2 play is absurd.  Anyway, back to the topic at hand.

I hope the wine install goes well.  If you're having problems with wine, I belive my last install of it actually came from arnieboys Automatix.  The Automatix app can actually install a multitude of things besides wine like video codecs and Open Office 2.0, but you could just use it for wine.  Here's the link if you still need it:
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

PS:  After D2 install we'll have to configure the ports on your comp to allow D2 to access the 'net (assuming you want bnet play).  Post back when you're ready to go further or if you have probs with wine/d2 install.

-Griff

---

### Post by KrazyPenguin on 2006-04-29
Please visit my website at:

[http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine](http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine)

For a more detailed approach to installing Diablo.
This install works for Dapper, but I haven't tested it on Breezy
Let me know how it goes.
Thanks,
KrazyPenguin

---

### Post by rivers.marcelo on 2011-04-12
quero saber se alguem tem o arquivo de instalação do jogo Diablo II p/ me enviar.

---

