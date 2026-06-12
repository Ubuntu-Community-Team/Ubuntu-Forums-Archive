---
title: "Creatures Docking Station"
date: 2009-06-05
forum: Gaming &amp; Leisure
---

### Post by chs1010 on 2009-06-05
Hi all, im new on this forum so be nice :P XD

only joking i bet youre all really friendly, anyway, for the problem im having, how on earth do i get creatures installed on my netbook, it has the right specs and ive followed the installation instructions i found exactly but something still seems to be wrong, maybe one of you guys could help

im quite new to linux, i had fedora before but im now on xubuntu which ive heard is the same as ubuntu but a little cut down for lighter computers

i managed to install the game to my home directory but where do i execute the command to run the game, the guide says to say it after the initial installation but it didnt work, anyone who can shed a little light on what i may have done wrong please make my day lol

thanks in advance :D

---

### Post by mocoloco on 2009-06-05
First try running it from a terminal.  Easiest way to do that is browser to the folder it's installed in, right-click in a blank area and select "Open Terminal Here".
Then type in whatever command it tells you to start the game, but preceeded by "./" (that's period slash). For example 
```
./creatures.sh
```

If you don't know what file to execute, type "ls" (meaning list) and any file name in green is executable, so you can do ./<filename> to execute it.
If you get any errors post them here.  If it works we can see about adding it to the menu for easier launching.  Also, where is this guide you're referring to, it it somewhere available online?

---

### Post by chs1010 on 2009-06-07
OK, i searched through for any form of executable or shell script to run the game, it says to run dockingstation but theres no file like that in there, the only executables do different things like convert images (part of the modification part of the game)

also, the guide is [here]("http://www.gamewaredevelopment.co.uk/downloads_more.php?id=448_0_8_0_M13") and [here]("http://creatures.amberz.net/") (this one you need to click on docking station under downloads at the side), if anyone else wouldnt mind to try to see if it works for them id be grateful, even if its just to see how to run the darn game XD

yeah it appears the run script doesnt exist or install properly

---

### Post by chs1010 on 2009-06-11
anybody?? lol

please T_T

---

### Post by chs1010 on 2009-06-20
BUMP!!! lol

come on people, please

---

### Post by Naiki Muliaina on 2009-06-20
32 bit Ubuntu install guide. The menu adding bit will be different as your using XFCE.

[http://gwos.org/doku.php/guides:32bit:creatures3#creatures_3_internet_edition](http://gwos.org/doku.php/guides:32bit:creatures3#creatures_3_internet_edition)

Hope that helps

---

### Post by chs1010 on 2009-06-20
ok thanks

how would i go about using an archive thing, tarball i think it is, because the game has a free version and i dont have a CD

how would i change the first part about copying from cd to accomodate this?

---

### Post by Naiki Muliaina on 2009-06-20
The game doesnt have a free version, if it is free, its a pirated version.

---

### Post by chs1010 on 2009-06-20
it does have a free version, docking station, if its free for windows im pretty sure its gonna be free for linux

---

### Post by calvimm on 2009-06-27
hi.
i am trying to install docking station as well on ubuntu 8.04 and i have no idea what is wrong.

i went through the terminal actions and it started installing.

at some point it said:

Updating linux_x86_glibc21 to latest version

Getting files from ports/linux_x86_glibc21_64/ to /home/calvimmm/DockingStation
Finished linux_x86_glibc21 update                                              
Relaunching new version of script
trap: 119: SIGINT: bad trap


and it stopped. there is a new directory for Docking Station in my home folder but i can't open the game... any suggestions?

---

### Post by chs1010 on 2009-06-29
so you can install it and not run it either? lol

its like there is a file missing even when its installed that runs the game

---

### Post by ncweber on 2009-09-13
So, no one's bothered to come up with a solution to this problem?  I wanted to run Creatures Docking Station on Linux as well.  I have Ubuntu Netbook Remix 9.04 and I followed what little instructions that Linux Game Publishing provided.  I downloaded the dockingstation.run file and made it executable.  I ran the executable file in Terminal and it extracts into the tmp directory just fine, but after that, I get row after row of "cannot remove file" and permission denied even after I've logged in as a super user.  If I could log what terminal spits out (too fast to read), then maybe that could help.

Anyone know how I go about doing that?

---

### Post by Perfect Storm on 2009-09-13
```

sudo apt-get install libgtk1.2
cd ~/Desktop
wget http://updatefiles.linuxgamepublishing.com/creatures/new_installer.run
chmod +x new_installer.run
sudo ./new_installer.run
```

If you want the extra goodies from the CD;
```
cd /media/cdrom0/magmanorns
sudo cp -r MagmaNornEggs.agents "/usr/local/games/creatures3/My Agents"
```


64-bit; [http://gwos.org/doku.php/guides:64bit:creatures_3](http://gwos.org/doku.php/guides:64bit:creatures_3)

---

### Post by Bitslinger on 2010-11-14
I've tried installing Creatures Docking Station via Wine because the old Linux installer seemed to be missing from the official website.  I've had various problems and have worked through them but I'm stuck with a requirement for libgtk-1.2.so.0.

I installed that old version and I have the file in /usr/libs/ but Docking Station still will not run properly.

```
dockingstation nocheck/usr/local/bin/dockingstation: line 83: type: creatures3: not found

Creatures 3 is not installed (you can buy it, or you can
buy Creatures Internet Edition, which has Docking Station
and the Magma Norns bundled with it, see the web site
http://ds.creatures.net for more info)

Querying language
/usr/local/games/dockingstation/langpick: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

I created a symlink to the file...

```
/usr/local/games/dockingstation$ ln -s /usr/lib/libgtk1.2.so.0 libgtk1.2.so.0
```

...but that didn't effect anything.

How can I make Docking Station recognize my installation of libgtk 1.2?

Thanks,
~bitslinger

---

### Post by Perfect Storm on 2010-11-14
It also need libglib version 1.2.

But there's a new installer for the game at LGP. Sadly their harddiscs had major breakdown.

[http://www.happypenguin.org/](http://www.happypenguin.org/)

---

### Post by GoGoGulliver on 2010-11-15
I got it to install successfully using the tarball... and managed to play it exactly once before it wouldn't start up again.

Anyway, nice to see another Creatures fan hereabouts. Good luck!

---

### Post by Vilentviolet on 2010-12-09
You guys have successfully managed to smoke me out of my lurking hole to join in on this...excitement! I've had Ubuntu going on my little Eee PC for a month or two now successfully, and until now I've resorted to fixing bugs and tweaking configurations here and there by myself.

I've played Creatures since I was in the 5th grade (and I'm now in my mid-20's) and I still find myself nostalgically coming back to the series from time to time when I'm not engaged in other aspects of my life. Well I also tried installing Docking Station on my computer, and I have gotten it going with near-complete success. The issue I am trying to fix is the sound. I can apparently run everything in the game just fine, but I keep getting a "sound initialisation failed (game will run silently)" popup error upon launching.

Okay... When I installed, I also ran into the missing libgtk1.2 error, which I fixed by downloading it manually with the help of this advice: [http://titan2x.wordpress.com/2010/07/18/installing-libgtk-1-2-on-recent-versions-of-ubuntu/]("http://titan2x.wordpress.com/2010/07/18/installing-libgtk-1-2-on-recent-versions-of-ubuntu/")
Only thing is that you should NOT use ```
sudo apt-get install libgtk-1.2
``` like it suggests you should... You should use:
```
sudo apt-get install libgtk1.2
```

And whenever you run into the bad trap errors, just run the same string of code again. Chances are something needed to refresh itself, and a second/third time worked for me.

When you're about to install, type this instead of what it originally suggests you to type:
```
sudo ./dstation-install nocheck
```
The "nocheck" at the end is very important, since the DS servers are not the same as they used to be and bypassing the updating process will help you finish the installing process correctly.

If you've gotten this far, then to run DS simply type 
```
dockingstation nocheck
```
into the terminal. Let me know if the sound works for you guys or not!

---

