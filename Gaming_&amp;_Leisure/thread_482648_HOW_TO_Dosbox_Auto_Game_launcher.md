---
title: "HOW TO: Dosbox Auto Game launcher"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by Jest3r on 2007-06-23
[SIZE="4"]Launch old dos games from a shortcut.[/SIZE]
First How To + Post :)

**End Result.**
Have a shortcut on your desktop that is able to launch dos games.. then clean up after you exit the game.

**Assumptions**
You use wine.

Install dosbox
```
sudo apt-get install dosbox
```

Download/install your old dos game.
I will use Rescue Rover. 

Download and unzip
```

mkdir ~/.wine/drive_c/rrover
cd ~/.wine/drive_c/rrover
wget http://www.doomwadstation.com/wolf/rescuerover.zip
unzip rescuerover.zip
ls -l

```

Create shortcut code.
```

vi rrover-link

```

Paste in this line.
> 
#!/bin/bash
#Start Rescue Rover
dosbox -c "mount c: /home/$LOGNAME/.wine/drive_c" -c "c:" -c "cd RROVER" -c "start" -c "exit"
exit 0

Create link on desktop
```

chmod 750 rrover-link
cd ~/Desktop
ln -s  ~/.wine/drive_c/rrover/rrover-link "Rescue Rover" 
chmod 750 "Rescue Rover" 

```

Done.

---

### Post by Dark Aspect on 2007-06-23
Thanks a lot I have always had problems with get Dos applications to load I will try this.

---

### Post by Jest3r on 2007-06-23
Let me know if it works -

---

### Post by dfreer on 2007-06-25
Just wondering... why do you need wine, and why do you put the game in the wine directory?

---

### Post by Dokatz on 2007-06-25
That sounds all great and stuff man, But I totally just use the terminal Dosbox command...Works really great if you just make an icon.

Heres what it says under command on launcher for Jazz Jackrabbit
```

dosbox /home/peter/games/jazz/JAZZ/JAZZ.EXE -fullscreen
```

Anything wrong with this method? Cause it works pretty great.

[IMG]http://i45.photobucket.com/albums/f56/Dokatz/launcher.png[/IMG]

---

### Post by Shizuka on 2008-05-05
hmmm. question: rescue rover is the game I'd like to get to play, but instead of wanting a shortcut I only just want to get the game into the dosbox from the downloaded file I have. i guess that's not a question, here goes: how does one move the downloaded file into the dosbox to get it to play. in mac os x (which i am running) 'open with' doesn't allow dosbox as an option.

---

### Post by grossaffe on 2008-05-05
I just wrote batch files and ran them in dosbox

---

### Post by Perfect Storm on 2008-05-05
I recommend using Dosbox Game Launcher instead, it also makes it easy to fine tune dosbox for each game via frontend.

---

### Post by grossaffe on 2008-05-05
> **Artificial Intelligence said:**
> I recommend using Dosbox Game Launcher instead, it also makes it easy to fine tune dosbox for each game via frontend.

yeah, about that. has anyone else had a problem where the dosbox commands to change mouse sensitivity, or anything else of that nature, don't work?  Otherwise I would just have the batch files have commands that customize dosbox for each game, but the commands don't do a thing.

---

### Post by Shizuka on 2008-05-06
thanx DBGL worked like a charm!

---

### Post by DoktorSeven on 2008-05-06
I use Zenity as a launcher:

```

#!/bin/bash

cd /media/sdb6/dosgames
ZGAME=`zenity --list --text="Choose a game" --column="Game" "Ultima III" "Ultima IV" "Ultima V" "Ultima VI" "Eye of the Beholder"`

case $ZGAME in
"Ultima III")
	cd Ultima/ULTIMA3
	dosbox ULTIMA.COM
	;;
"Ultima IV")
	cd Ultima/ULTIMA4
	dosbox ULTIMA.COM
	;;
"Ultima V")
	cd Ultima/ULTIMA5
	dosbox ULTIMA.EXE
	;;
"Ultima VI")
	cd Ultima/ULTIMA6
	dosbox ULTIMA6.EXE
	;;
"Eye of the Beholder")
	cd forgottenrealms/eye
	dosbox start1.exe
	;;
esac

```

---

### Post by ekravche on 2008-05-11
Thanx, this helped a lot

> **Jest3r said:**
> [SIZE="4"]Launch old dos games from a shortcut.[/SIZE]
First How To + Post :)

**End Result.**
Have a shortcut on your desktop that is able to launch dos games.. then clean up after you exit the game.

**Assumptions**
You use wine.

Install dosbox
```
sudo apt-get install dosbox
```

Download/install your old dos game.
I will use Rescue Rover. 

Download and unzip
```

mkdir ~/.wine/drive_c/rrover
cd ~/.wine/drive_c/rrover
wget http://www.doomwadstation.com/wolf/rescuerover.zip
unzip rescuerover.zip
ls -l

```

Create shortcut code.
```

vi rrover-link

```

Paste in this line.


Create link on desktop
```

chmod 750 rrover-link
cd ~/Desktop
ln -s  ~/.wine/drive_c/rrover/rrover-link "Rescue Rover" 
chmod 750 "Rescue Rover" 

```

Done.

---

### Post by astarr on 2009-09-21
I used the following code for Ubuntu 9.04 as a shortcut to open games in Dosbox:
> dosbox -c "mount c ~" -c C: -c "cd \games\dos\orion2" -c "ORION2.EXE"

~ is my home folder
\games\dos\orion2 is where my game is located, Master of Orion 2
ORION2.EXE is the executable

Dosbox should open up and begin executing all fo the commands after the dosbox command.

---

### Post by rCXer on 2009-09-22
Wow really cool suggestions so far. Thanks Jest3r! 
I just associate all *.com files with dosbox.  Wouldn't suggest this with *.exe files because the might be windows programs...

Basically all you have to do is...
[LIST]
[*] Right click on any *.com file and select "Properties".
[*] On the "Open With" tab click "Add" and then "Use Custom Command". 
[*] Type the command "dosbox -noautoexec -exit", and then click "Add".
[*] Then select it in the "Open With" tab before clicking "Close".
[/LIST]
The changes should take effect after restarting Ubuntu.

---

