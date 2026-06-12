---
title: "loki installer......"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by techno-mole on 2007-05-27
ok, while reading through various threads and posts i found mention of the loki installer, i also found a link to it aswell (at least a link for it for doom3) so can someone tell me if this installer will work for a variety of games or just ones that will run on linux (eg doom3 quake 4)
cheers.
ps - to the moderators you may want to delete my thread about doom3, i knew the installation of the demo was too easy, i had no sound and couldnt actually start it properly, but never mind.
cheers

---

### Post by sethmahoney on 2007-05-27
It works with a variety of games, some of which run natively, some of which run through wine, and some of which run through cedega.  If you look on their website, there's a list of games that have loki installers.

---

### Post by techno-mole on 2007-05-27
so its not a program that you install and then install games through, each game has its own loki installer ?
also one other question, ive used the installer for doom3, but it wouldnt let me install the resurrection of evil expansion, even though the disc was mounted it just kept saying i needed to mount the disc, is there another way of getting the expansion to work ? like copying the base.pak files from the cd to a directory ?
cheers

---

### Post by DoktorSeven on 2007-05-27
> 
If you are also installing the Resurrection of Evil Expansion Pack,
you need to copy the following file to your d3xp/ directory
by default, /usr/local/games/doom3/d3xp

a883fef0fd10aadeb73d34c462ff865d  d3xp/pak000.pk4


[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

---

### Post by sethmahoney on 2007-05-27
> **techno-mole said:**
> so its not a program that you install and then install games through, each game has its own loki installer ?

Yes, each game has its own loki installer.  And to install some of them, you'll also have to have either wine or cedega installed.

---

### Post by techno-mole on 2007-05-28
regarding the roe expansion for doom 3, i used the loki installer to put doom3 on the system, and i just left the install path as it came up, so basically doom3 is installed in my home folder, and also according to the guide and from various things ive read there should have been a folder created in the doom3 directory when the game installed, but there isnt a folder with that name.
so if i create a folder in the doom3 directory and then copy the pak file over will that work ?
so for example doom3 is installed like this on my system - /home/techno-mole/doom3 and ive then created a folder in the doom3 directory - /home/techno-mole/doom3/d3xp so if i then copy the file over (pak 004 or something like that) fomr the roe disc will it work ? 
or have i got the paths wrong ?
cheers.
as for the loki installers, i also want to put never winter nights on the linux system, does anyone know if this has a loki installer ? or should i just do it using the files on bioware webiste (i have the game for windows)
and another question, if you want to un-install a game (eg doom3) that you installed with the loki installer how would you go about it ? would deleting the game files work ? or would you have to do it through terminal - eg - sudo apt-get remove doom3 type of thing.
cheers

---

### Post by sethmahoney on 2007-05-29
> **techno-mole said:**
> regarding the roe expansion for doom 3, i used the loki installer to put doom3 on the system, and i just left the install path as it came up, so basically doom3 is installed in my home folder, and also according to the guide and from various things ive read there should have been a folder created in the doom3 directory when the game installed, but there isnt a folder with that name.
so if i create a folder in the doom3 directory and then copy the pak file over will that work ?
so for example doom3 is installed like this on my system - /home/techno-mole/doom3 and ive then created a folder in the doom3 directory - /home/techno-mole/doom3/d3xp so if i then copy the file over (pak 004 or something like that) fomr the roe disc will it work ? 
or have i got the paths wrong ?
cheers.
as for the loki installers, i also want to put never winter nights on the linux system, does anyone know if this has a loki installer ? or should i just do it using the files on bioware webiste (i have the game for windows)
and another question, if you want to un-install a game (eg doom3) that you installed with the loki installer how would you go about it ? would deleting the game files work ? or would you have to do it through terminal - eg - sudo apt-get remove doom3 type of thing.
cheers

I don't know what you're referring to re: the Doom 3 installer, but yes, NWN has a native linux installer (which means you don't need to have wine or cedega).

---

### Post by techno-mole on 2007-05-29
i missed a bit out, what i was saying about the doom3 installer is that its meant to create a folder in the base folder, that folder is meant to be for the roe expansion pack, but it doesnt matter now as i created the folders myself and copied the base pak over and it worked, although im not sure how to run the expansion as the command for terminal didnt work, but apparently you can run it from the mods section, which i presume will come up when you start the game ?
cheers
ps - nwn installed really well and runs fine.

---

