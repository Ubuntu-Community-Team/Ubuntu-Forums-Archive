---
title: "All i want to do is play vdrift"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by CameronCalver on 2006-06-12
Ok on the cover disk of linux format i got the game vdrift and i downloaded it it is vdrift.tar.bz2 and then i extracted it and these are the files that came out 
Data                      Docs                           vdrift   (executable) and vdrift-install.sh

so this is what i tryed

cameron@ubuntu:~$ cd /home/cameron/downloads/vdrift
cameron@ubuntu:~/downloads/vdrift$ sh vdrift-install.sh
This script installs the VDrift binary and data into the proper places.
Make sure you run it as a root-level user.

Usage:
vdrift-install.sh /path/to/vdrift/binary /path/to/vdrift/data

Example:
vdrift-install.sh /usr/games/bin /usr/share/games/vdrift

Here the vdrift exectuable will be /usr/games/bin/vdrift and the data will go
in /usr/share/games/vdrift. Make sure that the binary directory is in your PATH.
For help or more information visit <http://vdrift.net/>

cameron@ubuntu:~/downloads/vdrift$


so then i did  sudo sh vdrift-install.sh /usr/games/bin /usr/share/games/vdrift

and it installed to those files but how do i get into the game?

---

### Post by Brynster on 2006-06-12
if its a good installer then i would guess at there being an icon in the games drop down menu. If thats not there i would suggest opening a terminal window and type vdrift at the prompt.

---

### Post by CameronCalver on 2006-06-12
nope didnt work any other suggestions

---

### Post by Footissimo on 2006-06-12
Have a look in usr/games/bin/ and see what vdrift binaries are there, then use ./[whatever_the_name_of_it_is]

edit: there is also ubuntu debs for both the program and the data - [here](http://sourceforge.net/project/showfiles.php?group_id=137283&package_id=150901&release_id=395251)

---

### Post by CameronCalver on 2006-06-12
ok im dling that now but still it shouldnt be that hard ubuntu needs gui for source files and ill tell u if it worked in 10 mins

edit actually more like tomorow lol i am now dling the data file 45 mb

---

### Post by tokez on 2006-06-12
try navigating to the vdrift directory that it installed to and locating a launcher there. you might have to do 'sudo chmod +x launchername' then do ./launchername and it should run.

also, you can copy the launcher from the installation folder to /usr/bin. that way when you type the name in a console it launches it. the installer might not have made these necessary links or copies.

i just noticed that the dir the executable should be in is /usr/bin/games/vdrift

---

### Post by benplaut on 2006-06-12
first of all, those aren't source files.  They are pretty close to a windows MSI.  Second, Dapper Drake 6.06 has a graphical tool for it, gdebi.  It's configured to use it by default.

Third, their debs are broken :P

---

### Post by CameronCalver on 2006-06-12
cameron@ubuntu:~$ cd /home/cameron/downloads/vdrift cameron@ubuntu:~/downloads/vdrift$ sudo chmod +x vdrift
Password:
cameron@ubuntu:~/downloads/vdrift$ ./vdrift
./vdrift: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
cameron@ubuntu:~/downloads/vdrift$


wel?

and i donloaded the data package from sourceforge and the deb whwen i run the deb it says could not find vdrift-data so when i download vdrift-data.zip where do i extract it to so the .deb will find it

---

### Post by thelusiv on 2006-06-26
I'm a dev for this game. I'll let you guys in on a little secret, we're about to release a new version. The current Ubuntu packages work for 5.10, but not 6.06. I'll be installing Dapper soon and building a new package after the new VDrift is released.

Don't forget, [vdrift.net](http://vdrift.net/) has forums. :)

On a side note, wouldn't it be nice if these guys at least sent us poor developers a copy of their publication since we're helping them sell it with the game on their cover CD? :rolleyes:

---

### Post by Gorbachev on 2006-06-26
Holy crap! That game looks awesome. I hope it is truly a simulation.

Kind of how arcade air combat games somehow get put under "Flight Simulation", whilst only MS2004 and IL2 belong under that genre category :p

---

### Post by CameronCalver on 2006-06-26
sweet cant wait till the 6.06 version is released and try to make it a .deb

---

### Post by thelusiv on 2006-07-24
Hey everybody, you might have noticed a new version of [VDrift](http://vdrift.net/) is out, we have now prepared some autopackages that work pretty well on lots of different operating systems. We're having some difficulty building debs at the moment, so go ahead and try the .package files. There are two versions, full and minimal, the only difference is the size of the files and the number of cars/tracks included. 

For this version you'll need to make sure you install FreeALUT (package is called libalut0 in Apt), along with the usual SDL, SDL_image, SDL_net, OpenAL, and of course some kind of GLX :)

[vdrift-2006-07-08-full.x86.package](http://prdownloads.sourceforge.net/vdrift/vdrift-2006-07-08-full.x86.package?download) (140 MB) 
[vdrift-2006-07-08-minimal.x86.package](http://prdownloads.sourceforge.net/vdrift/vdrift-2006-07-08-minimal.x86.package?download) (23 MB)

See [this article](http://vdrift.net/article.php/2006-07-08-linux-src-autopackage-release) for more info on the release.

---

### Post by mikexgough on 2006-08-05
Nice work fella,  the package file worked ok on my dapper set up, I tried the deb but no go , got rid and installed the full package, great game and one that I have wanted for a long time

---

### Post by Paerez on 2006-08-05
Just a note:
The installer failed when I didn't have alut (which makes sense) but it never told me that it was because of a lack of ALUT, so I had no idea what was wrong. This thread pointed me in the right direction, but I wanted to suggest putting a check/warning for ALUT. It's installing now, then I am gonna play :D

---

### Post by d351GuJu on 2006-08-27
This is one of the best racing game I have ever played on linux :D , the controls are little complex at first if you are using only mouse, but once you start playing it, you will enjoy it!

---

