---
title: "Baldur's Gate 1"
date: 2006-01-07
forum: Gaming &amp; Leisure
---

### Post by Turtle.net on 2006-01-07
I installed Baldur's Gate (the first one with 4 cds) without any problem using wine ```
 $ wine --version
Wine 0.9.5
$ wine /media/cdrom0/setup.exe
``` No errors, no problems...everything seemed perfect.
According [http://frankscorner.org/index.php?p=baldursgate]("http://frankscorner.org/index.php?p=baldursgate") you have to > Once it's installed, go to the Movies directory and either rename or delete the MOVIECD1.BIF file.
Then type "touch MOVIECD1.BIF", this will create a file of that name with nothing in it.
You also must also edit Baldur.ini and change SoftBltFast=0 to SoftBltFast=1.
First thing : there was no Movies directory so I created one and created the false MOVIECD1.BIF file.

When I launch the game ```
$ wine ~/.wine/drive_c/Program Files/Black Isles/ Baldur's Gate/Baldur.exe
``` the launch window appears but this window freeze when I click Play and nothing more happens...
If I launch ```
$ wine ~/.wine/drive_c/Program Files/Black Isles/ Baldur's Gate/BGMain.exe
``` the game seems to launch, but as soon as I try to create a character there is an error and the game end...

Anyone has already installed this game ?

---

### Post by cb951303 on 2006-01-10
shouldn't you first cd to the game's directory and then run directly like ```
 wine game.exe 
```

---

### Post by Turtle.net on 2006-01-11
Maybe I'm wrong...but I think that the same thing than ```
wine completepath/game.exe
``` 
Do you think there is a difference ?

---

### Post by Mr_Grieves on 2006-01-11
[QUOTE=Turtle.net]Maybe I'm wrong...but I think that the same thing than ```
wine completepath/game.exe
``` 
Do you think there is a difference ?[/QUOTE]
Please try with CD first..
Check for game specific switches that may help.
What sound drivers are you using? If you're running WineOSS try WineALSA drivers. I've seen that resolve freezing/crashing issues in other games.

---

### Post by cb951303 on 2006-01-13
[QUOTE=Turtle.net]Maybe I'm wrong...but I think that the same thing than ```
wine completepath/game.exe
``` 
Do you think there is a difference ?[/QUOTE]
yes there is a difference.

---

### Post by akurashy on 2006-01-13
I don't know if this one can give you a hand

[http://www.liflg.org/?catid=7&gameid=18](http://www.liflg.org/?catid=7&gameid=18)

(Notice that there are configs to edit)

---

### Post by Turtle.net on 2006-01-13
Thanks for your help.
Now it's working I can play !!!!

---

### Post by Turtle.net on 2006-01-14
OK here is what I have done
```
cd /media/cdrom0
wine autorun.exe
``` and I selected "Install"
the installation was succesful.
After I verified the configuration of wine using winecfg, to verify thqt the CDrom was correctly detected (and designed as disk Z:).
I edited the Baldur's Gate configuration file ```
cd ~/.wine/drive_c/Program Files/Black Isle/Baldur's Gate
gedit Baldur.ini
``` to verify thqt the cdrom was designated as Z: and according to [http://frankscorner.org/index.php?p=baldursgate]("http://frankscorner.org/index.php?p=baldursgate") that  > [FONT=verdana][SIZE=2] You also must also edit Baldur.ini and change SoftBltFast=0 to SoftBltFast=1.[/SIZE][/FONT] 
I can either launch the game by 
```
cd /media/cdrom0
wine autorun.exe
``` or ```
cd ~/.wine/drive_c/Program Files/Black Isle/Baldur's Gate
wine BGMain.exe
``` Using the first possibility I cannot umount my disk during the game to change from CD1 to CD2.
Using the second possibility I can umount the disk but I cannot eject the disk :(

So I'm stuck
I cannot change from CD1 to CD2 during the game (to continue playing to follow the different missions...).

Any idea ?????

---

### Post by Sudokan on 2006-01-14
I don't know if this will help, but I had a similiar problem with many games until I ran across a thread suggesting that this be typed in a console

code:

sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'


After this I was able to always eject the cd, even when switching cd's during gameplay under wine. Hope this helps.

Sudokan

*The only Zen you can find on the tops of mountains is the Zen you bring up there.*  - Robert M. Pirsig

---

### Post by zaduma on 2006-01-16
Try making a full install of the game, then you dont need to change the CD's.

Unless of course they only introduced the "Full Install" Option in BGII, but i think they did have it in BGI

---

