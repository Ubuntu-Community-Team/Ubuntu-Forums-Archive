---
title: "&quot;Docking Station&quot; cannot create executable link."
date: 2006-05-23
forum: Gaming &amp; Leisure
---

### Post by Clay85 on 2006-05-23
Hello all. I hope I'm in the right forum for this! (I'm fairly new to Ubuntu in general, also.)

I'm trying to install a game - I found it in the ubuntu wiki - called "Docking Station". All went flawlessly untill:

[quote=Enzo's Terminal]Docking Station InstallBlast
----------------------------

Installing off filesystem /home/enzo/Downloads/dockingstation_195_64/.

Checking for updates...

Current linux_x86_glibc21 build: linux_x86_glibc21_64
Latest linux_x86_glibc21 build: linux_x86_glibc21_64
Nothing to update for linux_x86_glibc21

[B]Making 'dockingstation' executable link...
Directory /home/enzo/bin doesn't exist, or is a file.
You could try making it and running the script again.


enzo@reboot:~/Downloads/dockingstation_195_64$ dockingstation[/B]
dirname: missing operand
Try `dirname --help' for more information.
enzo@reboot:~/Downloads/dockingstation_195_64$
[/quote]

I'm not at all sure what this means. I could guess that it can't make the 'docking station icon' for some reason (Yes, I am from Windows). But, I don't know how to fix that even if that is my problem.

I'm using [this website]("http://creatures.treesprite.com/Upgrades5.html") and I am on the step where it says
[quote=TreeSprite Website]After initial installation, just type dockingstation to check forupdates and run the game.[/quote]

Any hints or a pointing-in-the-correct-direction would be greatly appreciated. (Please use small words!)

---

### Post by XAsmodeanX on 2006-05-24
Looks like it needs to put something in the bin folder in your home directory but it didn't automatically make it for you.  Kind of strange.  Try in the terminal the command 'mkdir bin' while in your home directory (you can get there by typing just 'cd' while in a terminal).

Try reinstalling and see if you get the same error.

---

### Post by Clay85 on 2006-05-24
Now it's a different error. I guess that means I'm making progress...
```

Docking Station InstallBlast
----------------------------

Installing off filesystem /home/enzo/Downloads/dockingstation_195_64/.

Checking for updates...

Current linux_x86_glibc21 build: linux_x86_glibc21_64
Latest linux_x86_glibc21 build: linux_x86_glibc21_64
Nothing to update for linux_x86_glibc21

File /usr/local/bin/dockingstation is already a symbolic
link to a different place.  The installer is trying
to make a link to /usr/local/games/dockingstation/dstation-install.
The current link is:

lrwxrwxrwx 1 root root 48 2006-05-23 18:59 /usr/local/bin/dockingstation -> /usr/local/games/dockingstation/dstation-install

[B]Either delete this link, or install the link to
another directory by setting BIN_DEST to a path
before running this script.

e.g. INSTALL_DEST=~/DockingStation BIN_DEST=~/bin ./dstation-install[/B]


enzo@reboot:~/Downloads/dockingstation_195_64$ 

```
How do I link to another somethingorother. Oh I'm just confused now. Let me copy and paste this e.g. and see if that works...

Okay, copied and pasted. I believe it installed (?).... Now when I try to run it I get this:
```
enzo@reboot:~/Downloads$ ls
bin                            gtk+-2.8.9-setup-1.zip
dockingstation_195_64          NVIDIA-Linux-x86-1.0-8762-pkg1.run
dockingstation_195_64.tar.bz2  spca5xx-20060501
gimp-2.2.11-i586-setup.zip     Torrent
gimp-gap-2.2.0-setup.zip       ubuntu-sticker.tar.bz2
gimp-help-2-0.9-setup.zip
[B]enzo@reboot:~/Downloads$ cd dockingstation_195_64
enzo@reboot:~/Downloads/dockingstation_195_64$ dockingstation
dirname: missing operand
Try `dirname --help' for more information.
enzo@reboot:~/Downloads/dockingstation_195_64$[/B]

```

---

### Post by Perfect Storm on 2006-05-24
Have you tried installing it as global? (sudo sh XXXXXXXX.sh)?

---

### Post by XAsmodeanX on 2006-05-24
Alright, try uninstalling the whole thing and begin again.  It looks like the first install something went wrong and it created some bad symbolic links as well as didn't make a bin folder for you.  Best thing to do right now is probably to clean up the mess and try to reinstall.  If the first time it throws out that error message about bin then do the same as before (ie 'mkdir bin') and then run it.  When it runs again, if it throws out that error about the symbolic link then delete the sym link that it's throwing a fit about (ie 'rm /usr/local/bin/dockingstation') and try and let it sort itself out that way.

See if any of that helps.

---

### Post by Clay85 on 2006-05-24
[QUOTE=Artificial Intelligence]Have you tried installing it as global? (sudo sh XXXXXXXX.sh)?[/QUOTE]

What does global mean?
I don't think I have any .sh files. What is .sh?

---

### Post by Clay85 on 2006-05-24
[QUOTE=XAsmodeanX]Alright, try uninstalling the whole thing and begin again.  It looks like the first install something went wrong and it created some bad symbolic links as well as didn't make a bin folder for you.  Best thing to do right now is probably to clean up the mess and try to reinstall.  If the first time it throws out that error message about bin then do the same as before (ie 'mkdir bin') and then run it.  When it runs again, if it throws out that error about the symbolic link then delete the sym link that it's throwing a fit about (ie 'rm /usr/local/bin/dockingstation') and try and let it sort itself out that way.

See if any of that helps.[/QUOTE]

I'm not sure how to go about uninstalling it. I know there is a nifty command to uninstall programs and all of their little... whatcha-callem...libraries? But I don't know the command or which file to use the command on. :-/

---

### Post by Perfect Storm on 2006-05-24
> What does global mean?
I don't think I have any .sh files. What is .sh?

By placing the game so every user account can benefit from the install.


Firstly download DS from here: [http://www.webpetz.com/creatures/dockingstation.php](http://www.webpetz.com/creatures/dockingstation.php) to your Desktop

Then:
```
cd Desktop 
tar xvfj dockingstation_195_64.tar.bz2
cd dockingstation_195_64
gedit dstation-install

```

Change all the **$11** to **$10** (there should be two of them) and save the file. Afterwards Save and exit.

```
sudo sh dstation-install 
```
Run this code twice, so it updates your DS.

To play it:
```
dockingstation nocheck 
```

If you want to know more about Creatures 3: Internet Edition (Full version, not just DS) Check here at Ubuntu Game List: [http://doc.gwos.org/index.php/Simulation_Games](http://doc.gwos.org/index.php/Simulation_Games)
For Howto install it check Ubuntu Gamers Arena - [http://gaming.gwos.org/](http://gaming.gwos.org/)

about uninstall your previous you should find an uninstall script (.sh) in the DS folder. Likely you have to do this:

```
cd /into/the/DS/folder
sh XXXXXXXX.sh

```

---

### Post by Clay85 on 2006-05-24
yay! Thank you so much! I'll try to install this after I eat lunch. :D

Yay for Ubuntu Gaming!
I need a life... :(

---

### Post by Clay85 on 2006-05-24
Docking Station InstallBlast
----------------------------

Checking for updates...

--14:11:20--  [http://downloads.ds.creatures.net/installblast/ports/live_linux_x86_glibc21.txt](http://downloads.ds.creatures.net/installblast/ports/live_linux_x86_glibc21.txt)
           => `/tmp/dsbuild.bz2.txt.q9Ez04'
Resolving downloads.ds.creatures.net... failed: Name or service not known.
Error performing wget

Docking Station failed to update from the internet. Either you
are not connected to the internet or the update server is down.
Please connect to the internet and try again.

You can run the game without checking for updates by typing
dockingstation nocheck. Note: You need to connect to the internet
anyway to make a new world once the game has started.

enzo@reboot:~/Desktop/dockingstation_195_64$ dockingstation nocheck
dirname: missing operand
Try `dirname --help' for more information.
enzo@reboot:~/Desktop/dockingstation_195_64$ dockingstation
dirname: missing operand
Try `dirname --help' for more information.
enzo@reboot:~/Desktop/dockingstation_195_64$

what does missing operand mean?

I tried to run it from ALT+F2 and it autocompletes it for me, but nothing happens when I press enter. So, I imagine that means the game is installed...

I'm going to try to uninstall it and re-install it. I can't find any .SH files, still. I'll figure it out.

---

### Post by Perfect Storm on 2006-05-24
Not quiet sure, but I looked it up - [http://en.wikipedia.org/wiki/Operand](http://en.wikipedia.org/wiki/Operand)

---

### Post by Clay85 on 2006-05-24
I decided to run the game on my WinXP machine to see what was up. I had the same server error, but I don't understand why the nocheck thing doesnt' take care of that.

At any rate, the game is more complicated to play than it is to install! I'm not sure I want to keep chugging at this if the game is going to be this complicated to play. o.O

Thanks for your help. I'll learn how to install programs some day... McWORLD!!

---

### Post by Seven_Six_Two on 2008-10-24
try editing /usr/local/games/dockingstation and changing all occurrences of $11 to $10 just like you did in the installer. It worked for me in 8.04.

---

### Post by calvimm on 2009-06-28
hi i found this forum and did all of the suggested things mentioned but i'm still having troubles.


Docking Station InstallBlast
----------------------------

Installing off filesystem /home/calvimmm/Desktop/dockingstation_195_64/.

Checking for updates...

Current linux_x86_glibc21 build: linux_x86_glibc21_64
Latest linux_x86_glibc21 build: linux_x86_glibc21_64
Nothing to update for linux_x86_glibc21

Making 'dockingstation' executable link...

Current global build:
Latest global build: dsbuild 195
Updating to latest version
Updating global data to latest version

Getting files from dsbuild 195/global/ to /home/calvimmm/DockingStation
Converting images to local format                                               
Finished global update

Rerunning to check for network updates
trap: 119: SIGINT: bad trap


calvimmm@Calvin:~/Desktop/dockingstation_195_64$ 


that is my latest error message and the final one that i keep receiving regardless of the path i take to get there. HELPP

---

### Post by ncweber on 2009-09-13
I realize that this info is three years old, but I felt the need to point out that none of the advice makes any reasonable sense to a non-Linux user or new Linux user.  It's the kind of thing the Softies and the Macphiles are constantly going on about.  People who want to use Linux as a desktop OS DO NOT want to have to deal with command line.  It's like learning another language, and that kind of thing becomes more difficult as you get older.

Here it is, 2009, and people still can't install this program.  Myself included.  And the LAST thing I want to do is muck about with some command language I don't know and possibly screw up my machine when all I wanted to do was play a simple game.

I apologize if this is coming across as a rant.  Frustration does that to a fella.  I like Ubuntu.  I really do.  Helluva lot better than Linspire where I came from.  But at least with Linspire, I NEVER had to use the command line.

In any case...anybody ever get this fraggin' game to work?  I notice a couple of errors on part of the people offering solutions.  They say to look at the .sh file.  News flash, fellas.  There is no .sh file.  You start with a dockingstation.run file that you have to make executable, then then that is supposed to unpack and install in one fell swoop.  Only it doesn't, and no one seems to know why.

---

