---
title: "Smokin' Guns"
date: 2010-07-23
forum: Gaming &amp; Leisure
---

### Post by xpowerfulxx on 2010-07-23
I made it so it can run as a .exe or w/e (with the chmod +x smokinguns.x86) but now when I double click it, nothing happens! I have Ubuntu 10.04

---

### Post by pytheas22 on 2010-07-23
Try right-clicking and selecting "Open with Windows Program Loader" (or whatever sounds closest to that; I forget the exact wording).

---

### Post by xpowerfulxx on 2010-07-23
> **pytheas22 said:**
> Try right-clicking and selecting "Open with Windows Program Loader" (or whatever sounds closest to that; I forget the exact wording).
I tried that before but my monitor says that it can't support the video mode.

---

### Post by Sef on 2010-07-23
Moved to WINE forum.

---

### Post by ucal on 2010-07-23
Wait.  Smoking guns is a linux native game isn't it?  And the filename you gave is .x86 which makes me think you saying .exe was just a misnomer.  For future references, .exe is a windows filetype, and using it as a shorthand for executable could lead people helping you astray.  

So running it with wine is a bad idea.  

Try running it in the terminal (much like my advice before I realized this wasn't for wine >_>).

---

### Post by xpowerfulxx on 2010-07-23
> **ucal said:**
> Wait.  Smoking guns is a linux native game isn't it?  And the filename you gave is .x86 which makes me think you saying .exe was just a misnomer.  For future references, .exe is a windows filetype, and using it as a shorthand for executable could lead people helping you astray.  

So running it with wine is a bad idea.  

Try running it in the terminal (much like my advice before I realized this wasn't for wine >_>).
It said on the website to mark it as a .exe and double click it. Nothing happens with the .x86, and when I rune the Windows .exe in Wine the screen turns black and a message pops up saying that my monitor cannot support the video mode, so I have to restart.

---

### Post by ucal on 2010-07-23
> **xpowerfulxx said:**
> It said on the website to mark it as a .exe and double click it. Nothing happens with the .x86, and when I rune the Windows .exe in Wine the screen turns black and a message pops up saying that my monitor cannot support the video mode, so I have to restart.

Are you sure they didn't mean executable?  Renaming the file with a different (as in .x86 to .exe) doesn't change the file type, it just makes it a lot harder for the computer to open it.  I'm guessing that's what you did.  I would suggest changing it back to .x86, then right clicking on it, selecting properties from the right click menu, clicking on the permissions tab, and making sure the box about allowing the program to execute is checked.

---

### Post by xpowerfulxx on 2010-07-23
> **ucal said:**
> are you sure they didn't mean executable?  Renaming the file with a different (as in .x86 to .exe) doesn't change the file type, it just makes it a lot harder for the computer to open it.  I'm guessing that's what you did.  I would suggest changing it back to .x86, then right clicking on it, selecting properties from the right click menu, clicking on the permissions tab, and making sure the box about allowing the program to execute is checked.
OMFG l RIGHT CLICKED, WENT TO PROPERTIES, WENT TO PERMISSIONS, AND TICKED THE PART ABOUT EXECUTING IT AS A PROGRAM

---

### Post by ucal on 2010-07-23
Okay, I'm sorry.  It's just you kept using the term .exe, which is a windows filetype, and it confused me.  >________>  Though you need to turn down the caps lock.  It may be cruise control for cool, but it is kind of annoying.

---

### Post by xpowerfulxx on 2010-07-23
[IMG]http://img69.imageshack.us/img69/698/omfgidiot.png[/IMG]
Its not that hard

---

### Post by pytheas22 on 2010-07-24
Could you please try executing the Linux version of the application from the terminal and post the output.  The commands you'd need to run would be:
```

cd /home/kristopher/Downloads/SmokinGuns
chmod +x smokinguns.x86
./smokinguns.x86
```

This will hopefully provide more output about what's going wrong when you try to execute it and allow us to find a solution.  (My guess is that it's a 32-bit executable and you're using a 64-bit system, but that's just a guess.)

---

### Post by ucal on 2010-07-24
> **xpowerfulxx said:**
> [IMG]http://img69.imageshack.us/img69/698/omfgidiot.png[/IMG]
Its not that hard

Could you stop calling it a .exe then?  It isn't a .exe, and because you did call it that, your topic is in the wrong forum, where it's slightly less likely to get the help you need.  

Running it with wine won't help because it isn't a windows program.

Anyways, run it in the terminal and post the input you get here.  

```
cd ~/Downloads/SmokinGuns
./smokinguns.x86

```

---

### Post by xpowerfulxx on 2010-07-24
./smokinguns.x86: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

---

### Post by ucal on 2010-07-24
> **xpowerfulxx said:**
> ./smokinguns.x86: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

Okay, so you're missing a library.  You can install it in synaptic package manager.  Just search for libopenal.

---

### Post by xpowerfulxx on 2010-07-24
> **ucal said:**
> Okay, so you're missing a library.  You can install it in synaptic package manager.  Just search for libopenal.
I did and it says I already have it

---

### Post by ucal on 2010-07-24
> **xpowerfulxx said:**
> I did and it says I already have it

The package in synaptic is libopenal1 I guess.  Try this command

```
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
```

EDIT:  This creates a symbolic link between the two listed directorys, so any requests for libopenal.so.0 will be redirected to libopenal.so.1, which should work just fine for running the game.  I think that's how it works anyways.  More technically inclined users than myself could probably find a bunch of problems with my explanation.

---

### Post by xpowerfulxx on 2010-07-24
Well I did that and I still get the same error message in Terminal.

On a side note, what's the difference between 32 bit and 64 bit?

---

### Post by gradinaruvasile on 2010-07-24
> **xpowerfulxx said:**
> Well I did that and I still get the same error message in Terminal.

On a side note, what's the difference between 32 bit and 64 bit?

The link should point to the game installation folder (where the executable is).

Also, OpenAl can be disabled from an autoexec.cfg. But it works quite well, it can output to PulseAudio.

I dont know what version do you use, but i have the .zip (latest b1.1) from their site and its a ppoint and click thing to launch it - the executable is called SmokinGuns.i386.
This zip contains everything for all platforms, you just have to launch your native one.

More info here:

[http://forums.debian.net/viewtopic.php?f=16&t=12624&start=30](http://forums.debian.net/viewtopic.php?f=16&t=12624&start=30)

In a nutshell:
 You have to download the 1.0 full zip, unpack it then download the 1.1 beta 4 update and unpack it on the top of the previous one. All servers i have seen run this 1.1b4 version so you must do this if you want to play online.

You have to link the aforementioned openal .so file (then go into preferences and set it to whatever sound backend you want) to the folder where the executables are (.i386 or .x64 are the Linux natives).
It is possible to have to make the above launchers executable.

Some resolutions work only if set in an autoexec.cfg (or the games cfg) explicitly (i have 1680x1050 on a monitor and i have to set it by hand).
The game configs reside in your home folder. Example of setting resolution (1680x1050 in my case):

The file (USERNAME is of course your username):

```
home/USERNAME/.smokinguns/smokinguns/autoexec.cfg
```

Contains:

```
seta r_customheight "1050"
seta r_customwidth "1680"
seta r_mode "-1"

```

---

### Post by lisati on 2010-07-24
> **ucal said:**
> Could you stop calling it a .exe then?  It isn't a .exe, and because you did call it that, your topic is in the wrong forum, where it's slightly less likely to get the help you need.  

Running it with wine won't help because it isn't a windows program.

Anyways, run it in the terminal and post the input you get here.  

```
cd ~/Downloads/SmokinGuns
./smokinguns.x86

```

Exactly. Please don't call a binary file an ".exe" file otherwise many of us will think you're talking about something runs in Windows or maybe even MS-DOS, DOSEMU or Wine.

---

### Post by xpowerfulxx on 2010-07-24
> **gradinaruvasile said:**
> The link should point to the game installation folder (where the executable is).

Also, OpenAl can be disabled from an autoexec.cfg. But it works quite well, it can output to PulseAudio.

I dont know what version do you use, but i have the .zip (latest b1.1) from their site and its a ppoint and click thing to launch it - the executable is called SmokinGuns.i386.
This zip contains everything for all platforms, you just have to launch your native one.

More info here:

[http://forums.debian.net/viewtopic.php?f=16&t=12624&start=30](http://forums.debian.net/viewtopic.php?f=16&t=12624&start=30)

In a nutshell:
 You have to download the 1.0 full zip, unpack it then download the 1.1 beta 4 update and unpack it on the top of the previous one. All servers i have seen run this 1.1b4 version so you must do this if you want to play online.

You have to link the aforementioned openal .so file (then go into preferences and set it to whatever sound backend you want) to the folder where the executables are (.i386 or .x64 are the Linux natives).
It is possible to have to make the above launchers executable.

Some resolutions work only if set in an autoexec.cfg (or the games cfg) explicitly (i have 1680x1050 on a monitor and i have to set it by hand).
The game configs reside in your home folder. Example of setting resolution (1680x1050 in my case):

The file (USERNAME is of course your username):

```
home/USERNAME/.smokinguns/smokinguns/autoexec.cfg
```Contains:

```
seta r_customheight "1050"
seta r_customwidth "1680"
seta r_mode "-1"

```
I set it like you said and now it shows up in a white screen instead. No picture, just white. At least the monitor doesn't complain about video mode.

My monitor is a Dell E207WFP

---

### Post by pytheas22 on 2010-07-24
> I set it like you said and now it shows up in a white screen instead. No picture, just white. At least the monitor doesn't complain about video mode.

That sounds like it could be a compiz problem.  Try disabling desktop effects using the utility at System>Preferences>Appearance and see if that makes a difference.

---

### Post by xpowerfulxx on 2010-07-24
> **pytheas22 said:**
> That sounds like it could be a compiz problem.  Try disabling desktop effects using the utility at System>Preferences>Appearance and see if that makes a difference.
High settings - White screen
No settings - Black screen

---

### Post by pytheas22 on 2010-07-25
Maybe you'd have better luck using the installer from [here]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=FPS&page=2").

---

### Post by gradinaruvasile on 2010-07-25
I once had a problem with it because of broken openal so link and i got black screens just like you. Check the links.

In the game's cfg (/home/USERNAME/.smokinguns/smokinguns/q3config.cfg) the default openal lib is "libopenal.so.1":

ln -s /usr/lib/libopenal.so.1 /GAMEFOLDER/libopenal.so.1

Where GAMEFOLDER = the folder where the executable is.

Some info on the sounds:

[http://www.smokin-guns.net/viewtopic.php?t=1981](http://www.smokin-guns.net/viewtopic.php?t=1981)

I played on 2 computers without any problems (compiz isnt installed BTW). Also i have nvidia cards on both.

---

