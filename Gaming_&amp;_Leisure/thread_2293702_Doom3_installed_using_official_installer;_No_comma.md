---
title: "Doom3 installed using official installer; No command 'doom3' found"
date: 2015-09-07
forum: Gaming &amp; Leisure
---

### Post by em3raldxiii on 2015-09-07
So I followed the tutorial here:  

[https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3)

Everything went without any trouble.  Accepted the license, tried the default directory, and tried a different directory, copied all the .p4k files from my ancient retail CDs.

At the end of the tutorial, it says to run the game with this simple command:

```
doom3
```

I am presented with this output:

```
$ doom3
No command 'doom3' found, did you mean:
 Command 'doom' from package 'prboom-plus' (universe)
 Command 'doom' from package 'doomsday' (universe)
 Command 'doom' from package 'chocolate-doom' (multiverse)
doom3: command not found



```

I am no Linux noob, but rifling through the directories did not net me a handy dandy binary file to run manually.  So what am I missing?

I've searched and searched *Tha Googz*, to no avial:  Every tutorial assumes the game will run with the simple **[FONT=courier new]doom3[/FONT]** command.

---

### Post by brian-mccumber on 2015-09-07
Did you try to search for Doom in your dashboard? It looks to me like that tutorial did not work as expected.

---

### Post by efflandt on 2015-09-07
I followed instructions at [http://anton.logvinenko.name/en/blog/how-to-play-doom-3-on-linux.html](http://anton.logvinenko.name/en/blog/how-to-play-doom-3-on-linux.html) to install doom3-demo? Did you remember to include "sudo " prefix when running the installer (any errors?). I have not installed full doom3 yet (need to see if my pak files are on my old PC), but I ran the doom3-demo installer and it it ended up in my $PATH:```
efflandt@XPS-8100-1404:~$ which doom3-demo
/usr/local/bin/doom3-demo

efflandt@XPS-8100-1404:~$ echo $PATH
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```But to get audio you need to install **alsa-oss** (or **alsa-oss:i386** in 64-bit Ubuntu) per [http://ubuntuforums.org/showthread.php?t=1705760](http://ubuntuforums.org/showthread.php?t=1705760) except substituting **doom3** where it has **quake4**, and once you set that up run the game as **aoss doom3**.

PS: I installed full doom3 version per link in my first paragraph, added everything to its "base" directory from my old WinXP/Ubuntu 10.04 PC, set up audio so that works with **aoss doom3**. And it starts fine with sound for introduction, but I guess I need to root around my basement for the original CD because it is asking for the CD key. Or I wonder if buying it for $10 on Steam would give a CD key? Strange that Steam developing its own SteamOS from Linux only has Windows versions of these classic games, even though ID Software provided Linux versions. But maybe it is due to needing something extra to get audio in current Linux distros.

I have been running Linux for over 20 years (since before I had Win95) due to easier CGI script development/testing for apache on a SunOS ISP and think I was using Linux when I spent many hours playing Quake II CTF. I even installed Quake III on a Raspberry Pi running its Debian wheezy called Raspbian (although, I had to compile it for ARM cpu) and figured out how to get that SD card to boot right into Quake III.

---

### Post by em3raldxiii on 2015-09-07
@brian-mccumber: Yep, checked.  No go :(

@efflandt:  I vaguely remember using SUDO because it wouldn't run without it.  However, I'll definitely check out the tutorial you linked - while it might be based on the same original documentation, there might be something subtle that's different.  Thanks for the link.  I'll report here with my results :D

---

### Post by troy7 on 2015-11-11
I have the same problem as originally posted.  I ran the install file with sudo and copied the pak files - but no doom3.  I did a sudo find / -name doom3 and found nothing.  I ran the install script again watching for any errors - saw none.  One thing I did do different during install is when I ran sudo apt-get install ia32-libs I was told to install lib32z1 lib32ncurses5 lib32bz2-1.0 - which I did.  I am running Ubuntu 14.04 64 bit.  Thanks.

---

### Post by Kale_Freemon on 2015-11-13
I have to run it with the following command.

```
aoss doom3
```

---

### Post by troy7 on 2015-11-14
OK - I got it going.  I type what I did - perhaps it will help the next guy?

First, I got the wrong doom...run file.  After running, I had a doom-sdk folder in /user/share/games.  This must be for a different game?  Anyway, I used the web page instructions at [http://www.cyberciti.biz/faq/linux-install-doom3-game/](http://www.cyberciti.biz/faq/linux-install-doom3-game/) - this site also tells me where to get the install file - I only followed step #1 there.  The instructions from [https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3) are crap and should be removed.

Then I copied my pak files into /usr/local/games/doom3/base.  Even though there are files already in there, you have to put the 4 pak files.  I got my pak files from piratebay - my CD is long gone.  Then, as I tried to run doom3 for the first time - got errors.  What I did to solve my errors is put the error message into google and found the appropiate sudo apt-get install 'something' there.  For example, if it said I was missing gl.h, i searched on need gl.h for ubuntu.  Finally, I got to a point where it ran, but asking for CD key.  The cracks and keys out there are a waste of time.  As the prompt for key was shown, I typed Ctrl-Alt-~ to get a command window.  In that window I typed map game/site3 <enter> - don't type enter.  Wait about 20 seconds and your in.  You will be starting at site3 - where ever that is in the game.  Just hit new game and adjust settings.

---

### Post by troy7 on 2015-11-14
One final note - all that work and the game is terrible - in my opinion.  I liked Doom and Doom II, but Doom 3 is just a zombie game.  Also, I found the game play/reactiveness way too slow - spend too much time maneuvering that shooting.

---

