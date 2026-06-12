---
title: "need help installing UT2004"
date: 2010-11-13
forum: Gaming &amp; Leisure
---

### Post by Sanhime on 2010-11-13
Using ubuntu 10.10
I'm following the installation instructions show here:
[http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

I go through the usual installation process, left all settings default.

Please enter the installation path [/usr/local/games/ut2004] 
Do you want to install symbolic links to a directory in your path? [Y/n] y
Please enter the path in which to create the symbolic links [/usr/local/bin] 
'Base Install' option will be installed.
Option: 'English' ? [Y/n] y
Option: 'SDL12 and OpenAL source code' ? [N/y] y
Do you want to install startup menu entries? [Y/n] y
Installing to /usr/local/games/ut2004/
64134 MB available, 5342 MB will be installed.

Continue install? [Y/n] y
Please enter your CD key [] ************************
Installing ut2004 binary ...
 100% - /usr/local/games/ut2004//ut2004
Installing Base Install ...
 100% - /usr/local/games/ut2004//ut2004.xpm
 100% - /usr/local/games/ut2004//System/libSDL-1.2.so.0
 100% - /usr/local/games/ut2004//System/openal.so
 100% - /usr/local/games/ut2004//System/ucc-bin
 100% - /usr/local/games/ut2004//System/ut2004-bin
 100% - /usr/local/games/ut2004//Help/UT2004Logo.bmp

Please mount the Unreal Tournament 2004 Play Disc CDROM.
Choose Yes to retry, No to cancel [N/y] y

Please mount the Unreal Tournament 2004 Play Disc CDROM.
Choose Yes to retry, No to cancel [N/y] 


And it keep repeatingly ask me to mount the disc, but the game is in my driver and is mounted.  And it is mounted otherwise I would never had gone up to this point of the install.

Any solutions?  Thanks!

---

### Post by Ligerzero_942 on 2010-12-14
I have the same issue, I tried making then mounting the .iso but still receive that message.

---

### Post by sohail_linux on 2010-12-14
may it was unmounted after certain steps , check it out whether its mounted or not use  mount in terminal to see.

---

### Post by Ligerzero_942 on 2010-12-14
I'm pretty sure it remained mounted as I still had the little disk icon that appears on the Desktop and the files were in the mount location.
Code I used:
> sudo mount -o loop UT2004.iso /media/<mountlocation>

---

### Post by handy on 2010-12-14
You need to upgrade UT2k4, after which includes an automatic NoCD patch from the developers amongst a lot of other improvements to the game.

You shouldn't have much trouble finding the upgrade on the net.

[I]**[edit:]** Hmm, I just noticed that you are failing before what I wrote above is applicable. Dunno what the solution is, it has never happened to me?

Sorry I can't be of any more help.[/I]

---

### Post by R33D3M33R on 2010-12-15
What version are you trying to install? CD/DVD? Try to manually copy the files/folders from the iso to /usr/local/games/ut2004/ and then copy over the latest megapack and patch.

The structure should look like this:

Animations/ (*.ukx.uz2)
Manual/
Maps/ (*.ut2.ux2)
Music/ (*.ogg)
Sounds/ (*.uax.uz2)
StaticMeshes/ (*.usx.uz2)
System/
Textures/ (*.utx.uz2)

More here: [http://forums.epicgames.com/showthread.php?t=558146](http://forums.epicgames.com/showthread.php?t=558146)

---

