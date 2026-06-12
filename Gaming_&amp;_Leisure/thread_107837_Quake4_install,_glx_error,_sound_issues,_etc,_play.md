---
title: "Quake4 install, glx error, sound issues, etc, play by play"
date: 2005-12-24
forum: Gaming &amp; Leisure
---

### Post by barfos on 2005-12-24
I wanted to get quake4 working with ubuntu.  For me this meant a couple of annoying problems.  I fixed it, I'm sure some of you all have fixed it too, but in case no one posted the solution, here it is, play by play.

1
First you need the quake4 retail cds and the cd key.  Then you need to find the file quake4-linux-1.0.2147.12.x86.run which will install the game on your linux machine using the windows game data found on the cds.  [Here]("ftp://ftp.idsoftware.com/idstuff/quake4/linux/") is the id software ftp directory with the file in it.  There's a newer version there, but I didn't know about it at the time, so I used the one shown above.  Perhaps its a good idea for you to use the newest version, but keep in mind that I didn't.

All the steps here after need to be done as root (meaning use sudo), which will cause a problem later.  That's ok because it fixable!

2
The directions I followed after this point are on [this](http://www.linux.com/article.pl?sid=05/11/07/1547208)  page (the first thing on google search for 'quake4 on linux').  You need to copy the .pk4 files from all 4 cds to your /usr/local/games/quake4/q4base/  directory.  With your luck, this directory probably doesn't exist yet. So...

```
sudo mkdir -p /usr/local/games/quake4/q4base
#stick in your cds one by one and do
sudo cp /media/cdrom0/Setup/Data/q4base/*.pk4 /usr/local/games/quake4/q4base/
#for each cd
```

note that the path of your cdrom depends on how you mount the drive, i think ubuntu auto mounts the cdrom as shown above.  Also for cd's 2 3 and 4, the asterisk trick to copy all the pk4's in one go didn't work for me.  So I just copied each pk4 file one by one!  Maybe you know some better way. Also note that I had to umount the cdrom whenever i needed to eject.  ie "sudo umount /media/cdrom0" or something similar.

3
Next you need to change the permissions of some of the files you just copied.  The ones from cd's 2 3 and 4 aren't readable or executable by anyone but root (700).  This is fine unless you want to run the game as a normal user.  Since thats what you want to do, that means you need to change the permissions!

```
sudo chmod 755 /usr/local/games/quake4/q4base/*.pk4
```

4
Next you need to run the install script that you found at idsoftware.com or on the internet somewhere.  I'm pretty sure you need to run it as root, so...

```
sudo sh ~/Desktop/quake4-linux-1.0.2147.12.x86.run
```

Of course if you put the file somewhere else besides your desktop, you need to say something slightly different.  Also of course you might have use a different version than me!  Read the legal stuff very carefully all the way to the end and then accept them both.  This post will hopefully still be here when you are 61 years old 8).

5
I saw on the Id software's faq that debian users probably need to replace their libsdl1.2debian-oss package with libsdl1.2debian-alsa, and shouldn't use libsdl1.2debian-all.  I didn't have any trouble with sound at any point, but I switched to the alsa one before running quake4.  This also fixed another portion of my cooperative sound issues, like running gaim, xmms, and enigma etc at the same time, but now theres a weird lag in the sound during enigma.  Anyway...

6
Here's where it got fishy.  For me, the installer placed a directory .quake4 in my home folder.  When I tried to run the game, the game tried to write to that folder, but couldn't and crashed.  Trick is: the folder is owned by root.  Change the owner like this

```
sudo chown -R yourname /home/yourname/.quake4
sudo chgrp -R yourname /home/yourname/.quake4
```
where yourname is your user name.  -R makes everything in the folder also yours.

7
You might be ready to play now!!! However I was not. Attempt to run the game by typing quake4.  If it works hurray.  This is where I and some other people in the forum had the inmfamous glx, couldn't get visual error crash thing.  If you check on [this]("http://zerowing.idsoftware.com/linux/doom/Doom3FrontPage?action=show&redirect=FrontPage#head-37a70860392f09490de7dde78bea00dba55c707a") page, it says you need a 24bpp desktop.  Use your h4x0r skillz and that idsoftware page as a reference to understand the output of "glxinfo"  and see if your current color depth is 24bpp or not.  Hint: if quake crashed on you with the glx cant get visual problem, you probably don't have the depth high enough!  Fix it like this...

```
sudo gedit /etc/X11/xorg.conf
```

go to the "Screens" area of the file.  to find something like

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
```

Change the DefaultDepth to 24, save the file, and hope that works!  It worked for me, but I have not much experience with xorg.conf or its XFree86 cousins.  You need to restart the computer or press cntl alt backspace to kill (and hopefully auto-restart) the X server after this. (if it doesnt auto restart just type startx.)

8
Type quake4, or make a menu icon that does it for you.  Cross your fingers and pray to the gods of quake.  You will hopefully be playing quake4 now!  If all goes well your final challenge will be to enter the sacred CD key once you are in the game.

Hope this helps some people!
barfos

PS: now that i finished my report of all this, i'm actually going to play the game now!  I'm probably not that good anyway 8)

---

### Post by barfos on 2005-12-24
I started playing and got the crappy sound quality that I saw in some other posts.  The way I fixed it was to run quake so it used oss (instead of alsa?)

```
quake4 +set s_driver oss
```

I thought I was trying 'upgrade' my system by getting rid of oss related stuff and replacing it with alsa.  Oh well, it made quake4 sound better, hope this helps!

barfos

---

### Post by whitesox on 2006-01-15
that fix also works for doom 3
doom3 +set s_driver oss

---

### Post by Tichondrius on 2006-01-17
just ordered quake4, but I already played thru most of doom3 on Ubuntu and everything worked great, almost as fast as windows too. I can't even remember if I had any install issues at all with doom3 but in any case these simple fixes like changing the owner or sound options should work because the ID engines have proven to work well on linux in the past (also played RTCW and other ID games on linux).

---

### Post by Rulzern on 2006-01-19
Worked without issue here, I installed as user though.

I only had to do points 1, 2 (well, copying the files anyway, not any of the other stuff), 4 and 8 :p

---

### Post by Tichondrius on 2006-01-23
I just installed quake 4 and had absolutely zero problems. But I did not need to do any of the special steps, I only did 1,2,4,8.  Basically just copy the *.pk4 files from the dvd/cd to the hard drive as shown in step 2, and then run the installer  using sudo. Just remember that at the end of the install it gives you an option to start the game or exit. DO NOT START THE GAME FROM THE INSTALLER AT THE END OF INSTALLATION because this will run it as root and will mess things up by creating all the settings under root ownership. So simply exit the installer and start quake4 from the command line.

First time you run it it will ask for the registration key, and also you can change the resolution and other system options. The game worked flawlessly for me and it's really amazing. Already finished more than half of the single player campaign.

[http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

---

### Post by Mnemonicman on 2006-03-03
Installed the game and it works great. Using +set s_driver oss helped alot and it runs fine. The only problem if you could call it a problem is when creating a link to the quake4 executable. If I type it in the terminal I get sound but when I use the shortcut there is no sound. A simple annoyance but it would great to just use  a shortcut.

---

### Post by Coolit on 2006-03-05
[QUOTE=Mnemonicman]Installed the game and it works great. Using +set s_driver oss helped alot and it runs fine. The only problem if you could call it a problem is when creating a link to the quake4 executable. If I type it in the terminal I get sound but when I use the shortcut there is no sound. A simple annoyance but it would great to just use  a shortcut.[/QUOTE]

I just bought Q4 a few days ago and have the exact same problem as you, I get sound if I type quake4 in a terminal but no sound from the shortcut I created in the Gnome menu, I've also followed the guide as above, replacing oss (thanks for that).

Althought it's just a small issue can anyone suggest a fix?

Thanks in advance! :D 

P.S. same thing happens with doom3.

---

### Post by Tichondrius on 2006-03-05
You need to disable gnome sound server in the preferences->sound menu.

---

### Post by akiro.yamamoto on 2006-03-15
Sound:
Edit the Quake4Config.cfg file in your .quake4 directory in your home folder.
Look for a line similar to:
seta s_dsp "/dev/dsp"
Add 
seta s_driver "oss"
under that line, save the file and
Done.
That should load the correct driver each time Quake 4 is started, no need
to enter it manually everytime you start the game...
Hope this helps ;)

---

