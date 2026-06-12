---
title: "The Mana World - Ubuntu Package testing."
date: 2006-08-13
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2006-08-13
Okay. I've been talking to the devs on Them Mana World Project and the gonna put my .deb package up and support it.
I just need someone (as many as possible) to test my package to see if I screw something up (mainly the dependecy list).
Build for i386 Dapper.

[The Mana World 0.0.20](http://www.filelodge.com/files/room38/1059449/Ubuntu/tmw_0.0.20-ubuntu2_i386.deb)

Oh please report back.

---

### Post by dkitty on 2006-08-13
Schweet. A .deb for TMW would be very nice. I removed my installation and tried your .deb but got this when attempting to run:

```
$ tmw
tmw: error while loading shared libraries: libphysfs-1.0.so.0: cannot open shared object file: No such file or directory

```

---

### Post by Perfect Storm on 2006-08-13
Okay, thanks.

Just install 

```
sudo apt-get install libphysfs-1.0-0
```

Will be corrected next time.
If you get new errors just post back.

---

### Post by dkitty on 2006-08-13
It worked like a charm. I played for a bit to be sure. No errors. Well done.

---

### Post by Perfect Storm on 2006-08-13
Thanks. :KS

---

### Post by Perfect Storm on 2006-08-14
Okay, error corrected. It can be downloaded from my first post.

---

### Post by ShirishAg75 on 2006-08-14
Can somebody provide the latest screenshots of the game. I saw the project page at [sourceforge]("https://sourceforge.net/forum/forum.php?forum_id=594553") & the latest u have there is 0.12. I don't know whether u're the creator or one of the maintainers either way if somebody can put the latest screenshots tht would be good enough. Thnx in advance.

---

### Post by Lord Illidan on 2006-08-14
Here's a screenie...
[http://wiki.themanaworld.org/index.php/Image:Tmw_0.0.20.png](http://wiki.themanaworld.org/index.php/Image:Tmw_0.0.20.png)

I dunno what this is about...it seems rather redundant, but power to them!

---

### Post by Perfect Storm on 2006-08-14
> **shirishag75 said:**
> Can somebody provide the latest screenshots of the game. I saw the project page at [sourceforge]("https://sourceforge.net/forum/forum.php?forum_id=594553") & the latest u have there is 0.12. I don't know whether u're the creator or one of the maintainers either way if somebody can put the latest screenshots tht would be good enough. Thnx in advance.

No, I just helping out where I can in diffrent projects etc.

---

### Post by qrm on 2006-08-14
it wants to remove libsd1.2debian-all and i have  weird feeling that it relates to my cinelerra installation. I dont have the courage to install tmw atm :D

---

### Post by Perfect Storm on 2006-08-14
Well, ir shouldn't. There's no of the related dependecy which are refering to removing it.

```
libasound2 (>= 1.0.10-2ubuntu4 ), 
libcurl3 (>= 7.15.1-1ubuntu2 ), 
libguichan0 (>= 0.4.0-4ubuntu2  ), 
libogg0 (>= 1.1.3-0ubuntu3 ), 
libsdl1.2debian-alsa (>= 1.2.9-0.0ubuntu2 ), 
libsdl-image1.2 (>= 1.2.4-1 ), 
libsdl-mixer1.2 (>= 1.2.6-1.1 ), 
libsdl-net1.2 (>=  1.2.5-6 ), 
libssl0.9.8 (>= 0.9.8a-7build1 ), 
libstdc++6 (>= 4.0.3-1ubuntu5 ), 
libtiff4 (>= 3.7.4-1ubuntu3.2 ), 
libvorbis0a (>= 1.1.2-0ubuntu2 ), 
libvorbisfile3 (>= 1.1.2-0ubuntu2 ), 
libphysfs-1.0-0 (>= 1.0.0-5 ), 
libxext6 (>= 2 )
```

I have both cinelerra and TMW installed side by side plus the dependency.

Can anyone else confirm it wants to remove a file?

---

### Post by qrm on 2006-08-14
[[IMG]http://imagesocket.com/thumbs/Screenshot64e.png[/IMG]](http://imagesocket.com/view/Screenshot64e.png)

---

### Post by dkitty on 2006-08-14
Nice desktop! :cool: 

I had no problems on my little Gateway P2 laptop running xubuntu 6.06. However, the package had problems with libtiff4 when I tried to install on a P3 desktop running ubuntu 6.06. There was something about needing libtiff4 v3 and not v3.2.

---

### Post by Perfect Storm on 2006-08-14
and you ran a full update of ubuntu?

---

### Post by Perfect Storm on 2006-08-14
> **qrm said:**
> [[IMG]http://imagesocket.com/thumbs/Screenshot64e.png[/IMG]](http://imagesocket.com/view/Screenshot64e.png)

Which extra package will it install?

---

### Post by qrm on 2006-08-14
I have problems with cinelerra too :P exact the same package etc, i dont know if I should sort the tmw isue first or cinelerra issue first :) Ok, heres the full list of extra packages it would install:

[[IMG]http://imagesocket.com/thumbs/Screenshota50.png[/IMG]](http://imagesocket.com/view/Screenshota50.png)

PS: im still not sactisfied with my xmms skin, ive been trying to get my desktoop looking neat for couple of weeks and now i see success ahead, buts thats just a lil offtopic :D

---

### Post by Perfect Storm on 2006-08-14
Strange...

Try install each package manually one by one to figure out if there's one who's trying to remove your libsdl.


off-topic
Try with Audacious instead of xmms. Xmms have been halted for some years. Audacious is the newest flashy thing at the moment. [http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

---

### Post by qrm on 2006-08-14
thanks for the audacious tip, ill check it out :)

I just went the easy way and installed tmw, everything works flawlessly. Nice work!

---

### Post by Perfect Storm on 2006-08-14
But it uninstall libsdl-all?

---

### Post by qrm on 2006-08-14
according to synaptic it uninstalled the libsdl1.2debian-all but the libsdl1.2debian and libsdl1.2debian-alsa packages are left untouched

---

### Post by dkitty on 2006-08-14
Please ignore my bit about libtiff4. I did a fresh install on a virtual machine and your deb worked flawlessly so long as I had the universe repository enabled. Nice work and thank you.

---

### Post by Perfect Storm on 2006-08-15
Tadaaaa. The package made it on The Mana World download page: [http://themanaworld.org/downloads.php](http://themanaworld.org/downloads.php)

---

### Post by andnobodyslept on 2006-09-20
First off thanks for creating the deb package. I'm just wondering if you are working on the update to 0.0.21? I have installed .20 and it runs fine for a while (enough for me to make it to level 4) and then has been crashing as soon as I connect to the server. I'm not sure if this is due to update or if there is something I'm missing.
Thanks.

Edit
here's the error message when the game crashs
Error: Animation: Could not find graphics/sprites/item008.xml!

---

### Post by Perfect Storm on 2006-09-20
I'm looking into a .21 version, but having some troubles with due to some weird things regarding guichan.

---

### Post by andnobodyslept on 2006-09-20
Ya I've been haveing some problems compiling the game from source, it configures just fine and then there are problems during make. I assume it is due to the guichian problem as well.
Keep up the hard work.

---

### Post by dkitty on 2006-09-20
Ditto the guichian problems on my end. No luck so far.

---

### Post by Perfect Storm on 2006-09-21
It seems it may be that they have chanched to newer libs requirements for TMW, but havn't corrected the configure file.


One of the devs had made a .deb package [http://forums.themanaworld.org/viewtopic.php?t=1870&highlight=guichan+error](http://forums.themanaworld.org/viewtopic.php?t=1870&highlight=guichan+error)
But it doesn't work. I suspect it's made on Debian Etch. It might work on Ubuntu Edgy.
Also that TMW have moved from guichan 0.4.0 to 0.5.0 might be the course of the problem.
I'll see if I can get in contact with one of the devs on IRC

---

### Post by Perfect Storm on 2006-09-21
For compiling TMW by yourself you need the latest version of Guichan (even though the configure script doesn't say so): [http://guichan.sourceforge.net/downloads.shtml](http://guichan.sourceforge.net/downloads.shtml) No bones to do so.

Here's a solution, by moi1392, it doesn't solve dependency though:
Uninstall your previous version of guichan and guichan -dev and TMW.
Install guichan v. 0.5.0 here: [http://vally8.free.fr/pamoi/guichan_0.5.0-1_i386.deb](http://vally8.free.fr/pamoi/guichan_0.5.0-1_i386.deb)
install it.
Install the tmw: [http://vally8.free.fr/pamoi/tmw_0.0.21-1_i386.deb](http://vally8.free.fr/pamoi/tmw_0.0.21-1_i386.deb)


Thanks go to moi1392 for the package and pauan to pintpoint me to the solution on themanaworld IRC @ freenode.

---

### Post by rolando2424 on 2006-09-21
Hello, I just register the forum to tell that the game worked for me (play it a while to see if it crashed...).

It crashed me the first time I played, but it was because I used the download in the first page, not this last one.

Perhaps you should change the download that is in the first post of this topic.

---

### Post by andnobodyslept on 2006-09-22
After uninstalling and installing the new guichan and useing the link provided by AI, I have the game up and running without any of the glitches I experinced earlier.

---

### Post by forcesofhabit on 2006-09-22
How do I uninstall TMW after doing a manual install? That is downloading the source, and what not?

The icon is even in my applications... but there's nothing mentioned of it in the add/remove section.

I want to do this of course, so I can use the Deb install.

---

### Post by Perfect Storm on 2006-09-22
unpack the source.
cd /into/the/source
sudo make uninstall

---

