---
title: "Alien Arena"
date: 2007-11-11
forum: Gaming &amp; Leisure
---

### Post by jordank on 2007-11-11
anyone know if there are ever any alien arena servers open? When i search for a server there are none. is this a multiplayer game, or just a network thing?

are there any free online multiplayer games that i can download from synaptics?

---

### Post by FG123 on 2007-11-11
I notice the version of AlienArena listed in Synaptic is 6.05, but the current version of the game is actually 6.10 (the repositories don't normally have major upgrades for programs), which means few people would be running servers for the old version so it's no surprise you can't find any multiplayer games with it.

If you're up to the task of downloading the game yourself: [http://red.planetarena.org/](http://red.planetarena.org/)

As for other free multiplayer games on Synaptic, I hear Battle for Wesnoth is pretty cool.

---

### Post by Zelphien on 2007-11-11
I currently play AlienArena and there are loads of servers.

If you have trouble not finding a server either do the following:

1) Refresh the server list
2) Restart AlienArena
3) Reboot your Computer


I downloaded AlienArena in Add/Remove Programs of Ubuntu 7.10 Gusty Gibbon. 

It works fine to me and runs great, just sometimes i get some lag and my game stops for a moment(probably due to my hardware)

If you still have problems, I advise you DONT install it from Add/Remove Programs of Ubuntu and download it from the actualy site [here]("http://red.planetarena.org")

---

### Post by Frak on 2007-11-11
You need the new version. The one in the repos is highly outdated.

---

### Post by jordank on 2007-11-12
when you installed alien arena from add/remove, did it come with all the updates? or how do i update it?

---

### Post by FG123 on 2007-11-12
Don't... use... synaptic. It will only install version 6.05, and it will not be updated through it.

Just download the zip file from the downloads section in the link I gave you. It's exactly the same way as getting the game in Windows - in both platforms you download the same zip file, extract and play. Very simple.

---

### Post by jordank on 2007-11-12
zip files work in linux?

---

### Post by jordank on 2007-11-12
where do i extract everything to? i downloaded and just extracted to desktop for now. but it just sits there. what do i do with the zip?

---

### Post by FG123 on 2007-11-12
It's just a zip file. Zip files can be read by ANYTHING, from a Mac to a friggin Amiga. Linux isn't that crap. :)

As for the game, the zip contains executables for Linux, assuming you downloading the Linux mirror version of course. I think it's enough to just go into the folder where you extracted the game and double click on "crx.sdl". It's JUST like Windows, nothing major.

---

### Post by jordank on 2007-11-12
the crx.sdl apparently does nothing when i open it.  Any ideas?

---

### Post by Frak on 2007-11-12
> **jordank said:**
> the crx.sdl apparently does nothing when i open it.  Any ideas?
You may want to run it in the terminal and give us the output.

---

### Post by jordank on 2007-11-12
jordan@jordan-laptop:~/Desktop/alienarena2007$ ./crx.sdl
./crx.sdl: error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory


that's from the terminal.

i find it weird, because i downloaded from the site give to me, and just extracted to my desktop. when i double click crx nothing happens.  What am i doing wrong?

---

### Post by Frak on 2007-11-12
> **jordank said:**
> jordan@jordan-laptop:~/Desktop/alienarena2007$ ./crx.sdl
./crx.sdl: error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory


that's from the terminal.

i find it weird, because i downloaded from the site give to me, and just extracted to my desktop. when i double click crx nothing happens.  What am i doing wrong?
```
sudo aptitude install curl
```

Linux software is different than Windows or OS X software, in that it shares dependant libraries instead of using seperate instances of the same file.

---

### Post by jordank on 2007-11-12
alright, that works. it now lets me run the crx and crx.sdl.  Now after that, it doesnt actually install the game, but rather just lets me play.  So it's location is actually right on my desktop, i wanted it to just update the alien arena i have in my 
applications >games>alienarena.  So now i have 2 different versions of the game. One that sits on my desktop, and one in the foresaid directory.
How do i 
either replace the one in my applications>games>alienarena with the new one
or
update the one i have?

---

### Post by Frak on 2007-11-12
> **jordank said:**
> alright, that works. it now lets me run the crx and crx.sdl.  Now after that, it doesnt actually install the game, but rather just lets me play.  So it's location is actually right on my desktop, i wanted it to just update the alien arena i have in my 
applications >games>alienarena.  So now i have 2 different versions of the game. One that sits on my desktop, and one in the foresaid directory.
How do i 
either replace the one in my applications>games>alienarena with the new one
or
update the one i have?
You could place the game in your home directory, put a trailing . in the name (remember this), view all hidden items, goto system > preferences > Main Menu > Games > Alien Arena > right click > edit > enter the path to the crx.sdl e.g. ~/.directory_where_game_is_placed > close > close > play.

---

### Post by jordank on 2007-11-12
how do i give it an icon? the zip folder came with an icon it is supposed to use, how do i set this icon to be used in the menu?

---

### Post by Frak on 2007-11-12
> **jordank said:**
> how do i give it an icon? the zip folder came with an icon it is supposed to use, how do i set this icon to be used in the menu?
Drag and drop.

---

### Post by jordank on 2007-11-13
okay. when i go into "edit menus" from righclicking applications, i right click Alien Arena, and select properties. from there, i put in to the command line:
/home/jordan/.alienarena2007/crx.sdl

nothing happens when i click on applications>games>alien arena.
Why doesn't this work? Do i need to take off /home/jordan?  or what should the directory in the command line read?
The above is the proper directory to the game.

---

### Post by Frak on 2007-11-13
> **jordank said:**
> okay. when i go into "edit menus" from righclicking applications, i right click Alien Arena, and select properties. from there, i put in to the command line:
/home/jordan/.alienarena2007/crx.sdl

nothing happens when i click on applications>games>alien arena.
Why doesn't this work? Do i need to take off /home/jordan?  or what should the directory in the command line read?
The above is the proper directory to the game.
try placing sh or bash in front of the line.

---

### Post by jordank on 2007-11-14
Hrmm. hate to bring this thread back from the dead, but i had to reinstall ubuntu.  I went to the site posted on page 1 of this thread and downloaded alien arena 6.10.  However, after extracting to my desktop, the crx and crx.sdl files do not launch alienarena.  I did the 
sudo aptitude install curl, but even after that it still does nothing when i run crx or crx.sdl.
Is it absolutely essential that i download 6.05 from the synaptics manager? or can i just use the download from the site given? if so, why isn't it working?

---

### Post by FG123 on 2007-11-14
I think we've mentioned several times that the Synaptics version is OLD, and hence useless. If neither the crx or crx.sdl files seem to work, run them (preferably crx.sdl as it tends to work better) using the terminal as you did before, and tell us what the programs say when they run.

It's obvious they're reporting an error of some kind, but you have to tell us what it is. First thing that comes to mind - when you reinstalled, did you use the Restricted Drivers Manager to install the proper drivers for your card? If not, then you are probably lacking OpenGL support and the game certainly won't like that.

---

### Post by jordank on 2007-11-14
jordan@Jorcomp:~/Desktop/alienarena2007$ ./crx.sdl
./crx.sdl: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory
jordan@Jorcomp:~/Desktop/alienarena2007$ 

it's obvious i need some libraries, but which ones?

---

### Post by FG123 on 2007-11-14
It tells you exactly which one. Run the following and try the game again:

sudo apt-get install libxxf86dga1

---

### Post by Frak on 2007-11-14
> **jordank said:**
> jordan@Jorcomp:~/Desktop/alienarena2007$ ./crx.sdl
./crx.sdl: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory
jordan@Jorcomp:~/Desktop/alienarena2007$ 

it's obvious i need some libraries, but which ones?
I'm not in Ubuntu right now, but if you get an error like that, run
```
apt-file **.so_file_here**
```
in your case
```
apt-file libXxf86dga.so.1
```
and it will give you the correct dependencies to install.

---

### Post by jordank on 2007-11-14
jordan@Jorcomp:~$ sudo apt-get install libXxf86dga1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxxf86dga1 is already the newest version.
The following packages were automatically installed and are no longer required:
  dbus-x11
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Does this seem odd? It claims it does not need to be upgraded, yet the crx.sdl still will not run.

Very confusing.

---

