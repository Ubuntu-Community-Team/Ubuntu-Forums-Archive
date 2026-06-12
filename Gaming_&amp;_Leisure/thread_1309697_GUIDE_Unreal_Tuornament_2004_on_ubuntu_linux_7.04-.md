---
title: "GUIDE: Unreal Tuornament 2004 on ubuntu linux 7.04--&gt;9.10"
date: 2009-11-01
forum: Gaming &amp; Leisure
---

### Post by shosholoza on 2009-11-01
[color=green]UPDATED 1 NOV 2009[/color]

  **_WORKS ON UBUNTU 7.04-7.10-8.04-8.10-9.04-9.10 32-64bit_**


Here the original link of my guide (of course in italian :P )
[GUIDA UNREAL TOURNAMENT 2004 Ubuntu 32-64bit 7.04-9.10 NO CEDEGA NO WINE](http://forum.ubuntu-it.org/index.php?topic=83243.0)

[color=darkred]##(For those who use kubuntu use sudo kate instead of sudo gedit or on lxde leafpad )[/color]

Pre-requirements:
You must have 3D acceleration activated
[color=blue]
--------------------FOR UBUNTU 9.10 KARMIK KOALA------------------------[/color]

because the libstdc++5 is no longer present in the karmik repositories, you need to download in your home, the rigth version for your architecture, from jaunty packages.
Here the link

[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

and then install it

for 32 bit) ```
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_i386.deb
```
for 64 bit) ```
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_amd64.deb
```
	
and then go to step **B**


**A)** Now, need to install some libraries, open terminal or Konsole and type:```
sudo apt-get install libstdc++5 libggz2
```

**B)** download the patch 3369 for linux, from [http://treefort.icculus.org/ut2004/ut2004-lnxpatch3369-2.tar.bz2](http://treefort.icculus.org/ut2004/ut2004-lnxpatch3369-2.tar.bz2) on the your home.

**C)** Insert the first cd on the cd-rom drive, open the terminal and launch installation game (rigth click on icon-cd on desktop-unmount and eject directly by your dvdrw drive)

```
sh /media/cdrom0/linux-installer.sh
```

**** Agree the licence, and select with spacebar

[img]http://i225.photobucket.com/albums/dd36/ettino/OpzioniinstallazioneUT2k4suubuntu.png[/img]

[b]Installation base 
SDL 12 And OpenAL source code[/b]

**as the destination folder of the game write /home/yourhome/games/ut2004** ...obviously yourhome...

change the cds (5) when prompted and when the installation is finished [color=red]DONT LAUNCH THE GAME[/color]

**D)** install the patch 3369; open terminal and type

```
tar xfvj ut2004-lnxpatch3369-2.tar.bz2

```
```
cd UT2004-Patch
```
```
cp -R * /home/yourhome/games/ut2004
```


**This point is necessary only for ubuntu 64bit**

**E)** Open startup script with the text editor:
```
gedit /home/yourhome/games/ut2004/ut2004
```

 and change at line 46 this:
      **if [ -x "${UT2004_DATA_PATH}/ut2004-bin" ]**
      with           
      **if [ -x "${UT2004_DATA_PATH}/ut2004-bin-linux-amd64" ]** 

      and at line 49 this:
      **exec "./ut2004-bin" $***
      with
      **exec "./ut2004-bin-linux-amd64" $*** 

  in poor words add [color=blue]-linux-amd64[/color], because the script launch the correct binary of ut2k4.
	
The game, now is installed, and last thing to do, is create a launcher: right click on desktop-create a launcher

set the right path directory of executable
/home/yourhome/games/ut2004/ut2004

[img]http://i225.photobucket.com/albums/dd36/ettino/LanciatoreUT2K4.png[/img]

and icon path is
/home/yourhome/games/ut2004/ut2004.xpm

[img]http://i225.photobucket.com/albums/dd36/ettino/IconalanciatoreUT2K4.png[/img]


**********************************************************************************************
TRICK--> for switch to windowed mode when you play (function works up to Ubuntu 8.10):
open xorg.conf  

```
sudo gedit /etc/X11/xorg.conf
```

add option ServerFlags

```
Section "ServerFlags"
        Option "AllowDeactivateGrabs" "true"
EndSection
```

Now to minimize the window will need to press: Alt+Enter and then to release the mouse cursor Ctrl+Alt+/ numeric keypad.
To restore it instead, always Alt+Enter.

**********************************************************************************************

[color=blue]HOW TO IMPORT OLD SETTINGS[/color]

You can import your game settings, preferences maps etc. etc., from Feisty,Gutsy etc etc copying the folder [color=blue]**. Ut2004 **[/color] that is in your home in one of Hardy.

If you are coming from Windows instead i recommend you to copy only the files UT2004.ini and User.ini from the System folder of the game, in your /home/.ut2004/System (it's a hidden folder, to display in your home do CTRL + H).


**********************************************************************************************
[color=blue]SECOND PART[/color]: How to improve gameplay and graphics performance

We can edit UT2004.ini to improve yield in opengl.

read this: [ Beyond Unreal: The (un)OFFICIAL Better Performance and Gameplay Guide for UT2004 by DDRRE](http://forums.beyondunreal.com/showpost.php?p=1364885&postcount=1)

NOTE: If u have an integrated video card with shared memory, add the right amount of video memory in the UT2004.ini 
DetectedVideoMemory =.......

**++++++++++++++++++++++++++++++++++++++++++++++++++++++++**
[color=blue]THIRD PART[/color]:for add new monitor resolutions over 1024*768 on ut2004

open ut2004.ini

```
gedit ~/.ut2004/System/UT2004.ini
```

search the following lines

FullscreenViewportX=xxxx
FullscreenViewportY=xxxx


And instead of xxxx put your resolution (X) horizontal and vertical (Y).

[color=red]ATTENTION THERE ARE 4 LINES, to change.[/color].


[b]°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°
°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°°[/b]
                                          [color=blue]UNINSTALL[/color]


For uninstall ut2k4, simply remove the folder ut2004 in /home/yourhome/games

```
rm -r /home/yourhome/games/ut2004
```
or delete directly the ut2004 folder in your /home/yourhome/games folder

If you want to remove your settings,maps etc etc also delete the folder .ut2004 in your home.
```
rm -r /home/yourhome/.ut2004
```

---

### Post by shosholoza on 2009-11-01
Service post

---

### Post by deamon_knight on 2009-12-06
Helped Me alot! Should be stickied, or put somewhere it can be referenced. Also, Why do these libraries keep getting obsoleted? Why can't we maintain backward compatibility?

---

### Post by shosholoza on 2009-12-06
> **deamon_knight said:**
> Helped Me alot! **Should be stickied**, or put somewhere it can be referenced. Also, Why do these libraries keep getting obsoleted? Why can't we maintain backward compatibility?

I agree.

---

### Post by Xeora on 2009-12-26
I also endorse the Sticky idea.

:guitar:

You Rock

---

### Post by ridowan007 on 2010-01-31
I have install it on Kubuntu 9.10 without installing libstdc++5 . libggz2 was already installed. But the fps is low. In some level its so low that its impossible to play. But I have no problem playing it in XP 5 month ago in the same pc. Anybody could help???

My pc configuration :
cpu: Intel pentium 4 2Ghz
Agp card: Nvidia 6200 128 MB, 64 bit, 4x Agp
Driver: Nvidia binary(from Nvidia site) 190.53
OS: Kubuntu 9.10
Ram : 1.2 GB

I ran the ut's installer but gui installer appeared. I don't select SDL & OpenAL source code option there. Also install it on a ntfs partition(my root disk can't take another 5gb) . Also I don't have install the patch(My net is also very slow now ;) ).

---

### Post by jhansonxi on 2010-02-06
Attached is a UT2004 start script by NakedApe that autodetects the architecture.

You should also read **[this post by Lathilde]("http://ubuntuforums.org/showpost.php?p=6250055&postcount=3")** on how to enable shadows.

On my system (Ubuntu 9.10 Karmic Koala x86_64), to get UT2004 (64-bit) working and keep from hanging at exit, I renamed the following libs and symlinked them to the system versions:
/usr/local/games/ut2004/System/openal.so -> /usr/lib/libopenal.so.1
/usr/local/games/ut2004/System/libSDL-1.2.so.0 -> /usr/lib/libSDL-1.2.so.0

OpenAL may **[need adjustment]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/356206")** to get sound working:

echo 'drivers = oss' >~/.alsoftrc
echo 'refresh = 2048' >>~/.alsoftrc

Also note that the mod installer ucc-bin needs to be executed from the ut2004/System directory else it fails to find the required *.ini files.  You can create a script to run it from anywhere:

```
#!/bin/sh
dir=`pwd`
cd /usr/local/games/ut2004/System; ./ucc-bin umodunpack -x $dir"/$1" -nohomedir
cd $dir
```

---

### Post by bbqau on 2010-02-22
Hi people, 

I found this post when having errors installing Americas Army which is also an unreal 2 engine game. I have installed the libstdc++5 however am still getting errors on startup.

The .deb installed it to /usr/lib/libstdc++.so.5

Does the path the game scans differ or something as i cannot seem to run it, any advice what i could do assuming that both unreal 2004 and Armyops 2.5 are likely to use the same libs and act similarly.

---

### Post by jhansonxi on 2010-02-23
> **bbqau said:**
> Hi people, 

I found this post when having errors installing Americas Army which is also an unreal 2 engine game. I have installed the libstdc++5 however am still getting errors on startup.

The .deb installed it to /usr/lib/libstdc++.so.5

Does the path the game scans differ or something as i cannot seem to run it, any advice what i could do assuming that both unreal 2004 and Armyops 2.5 are likely to use the same libs and act similarly.Try running it from a terminal window or look at the hidden log file in your home directory .xsession-errors and see if it provides a specific error message about a missing or incompatible file.

To try to use a specific library use the "LD_PRELOAD" variable on the command line to load it before the games loads a different one.  Just search with Google on how to use it.

---

### Post by hawthornso23 on 2010-02-24
> **bbqau said:**
> Hi people, 

I found this post when having errors installing Americas Army which is also an unreal 2 engine game. I have installed the libstdc++5 however am still getting errors on startup.

The .deb installed it to /usr/lib/libstdc++.so.5

Does the path the game scans differ or something as i cannot seem to run it, any advice what i could do assuming that both unreal 2004 and Armyops 2.5 are likely to use the same libs and act similarly.

If you are running 64 bit ubuntu then it might have to go into lib32 instead.

---

### Post by Perfect Storm on 2010-02-24
Running ut2004 in 64-bit is a bit tricky. Though I have a guide here: [http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

---

### Post by Drecondius on 2010-05-02
I must say AI that even though you how to was helpful it still doesn't help my case, my issue is that the installer "REFUSES" to recognise the Mounted DVD.

---

### Post by Perfect Storm on 2010-05-02
Sounds like a non-ut2004 issue and more like a system issue.

---

### Post by Brebs on 2010-05-05
> **Drecondius said:**
> the installer "REFUSES" to recognise the Mounted DVD.
The huge annoyance is that UT2004 has been repacked several times, in different formats:

[http://bugs.gentoo.org/show_bug.cgi?id=159164](http://bugs.gentoo.org/show_bug.cgi?id=159164)
[http://forums.gentoo.org/viewtopic-t-526497.html](http://forums.gentoo.org/viewtopic-t-526497.html)

So, improve your installation script ;)

---

