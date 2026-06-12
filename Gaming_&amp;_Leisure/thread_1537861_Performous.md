---
title: "Performous"
date: 2010-07-24
forum: Gaming &amp; Leisure
---

### Post by Stanich on 2010-07-24
So, I've got plenty of songs for UltraStar, and want to add them to performous. But I don't have access to any of these folders.
/usr/local/share/games/ultrastar/songs/[FONT=monospace]
[/FONT]/usr/share/games/ultrastar/songs/
 I mean I can see them, but I can't add other folders in it. :S

---

### Post by ronnielsen1 on 2010-07-24
> Performous looks for songs in the following paths: 
 DATADIR/songs/
~/.ultrastar/songs/
/usr/local/share/games/ultrastar/songs/
/usr/local/share/games/fretsonfire/data/songs/
/usr/share/games/ultrastar/songs/
/usr/share/games/fretsonfire/data/songs/

[http://wiki.performous.org/index.php/Songs](http://wiki.performous.org/index.php/Songs)

~/.ultrastar/songs/ ~/ is your home
. means a hidden config file

Browse to your home file in nautilus, choose the View Tab > Show Hidden files
Scroll down to .ultrastar folder (If not there, create folder .ultrastar
Create another folder inside the .ultrastar folder named songs
Place all songs in the songs folder

> So, I've got plenty of songs for UltraStar, and want to add them to  performous. But I don't have access to any of these folders.
/usr/local/share/games/ultrastar/songs/[FONT=monospace]
[/FONT]/usr/share/games/ultrastar/songs/
 I mean I can see them, but I can't add other folders in it. :S 	

You can always type gksudo nautilus in a terminal to get full control but it's a lot better to keep the config files in your home

---

### Post by Stanich on 2010-07-24
But I cannot create folder in Home neither. I am so confused now. :S

Unless Home means Administrator.

Got it now.

---

### Post by ronnielsen1 on 2010-07-24
> But I cannot create folder in Home neither. I am so confused now.

That's not right. Is this a regular install or a wubi? (Not sure if it makes a difference)

Go to Places > Home Folder

In the Window that opens, right click > add new folder

What does it do?

---

### Post by ronnielsen1 on 2010-07-25
Did it work or did you give up?

---

### Post by Admac on 2012-03-29
if you type "gksudo nautilus" into the terminal it will ask for you password than it will open the home directory as root (i.e. means you can add / delete folders in that window) goto usr/share/games/performous, now that ive hellped you maybe you can help me,  i downloaded performous ,
i have downloaded about 1000 song txt files which i have put into the apropriate folder share/games/performous/songs .
 when i open performous i now have a list  of artists and songs i can choose from and if i select one, the lyrics  scroll past at the right time and i can see the mic is picking up my  vocals as the bar moves when i try to sing into it but i cannot here the  song playing (yes my sound is working i can hear the menu music in performous)
i have tried renaming an mp3 with the exact same title as one of the txt  files thinking i might have to put the music file in the same folder  with the same name as the txt file but it didnt work, has anyone managed  to get this program working properly, i am a bit new to linux but a  fast learner oh and i am running ubuntu 11.10

---

### Post by CharlesA on 2012-03-29
Back to sleep you go...

---

