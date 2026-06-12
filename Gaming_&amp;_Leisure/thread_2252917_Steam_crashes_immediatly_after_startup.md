---
title: "Steam crashes immediatly after startup"
date: 2014-11-15
forum: Gaming &amp; Leisure
---

### Post by irongolem0982 on 2014-11-15
so i just installed steam and i go to open it and i see the icon appear in the launcher then the screen goes black (like it always does when i launch something) and nothing happens then steam dissapears. no error messeges or anything

im on ubuntu 14.04 64bit

im going to try it on lubuntu after i post this just to see if any difference.

i have already searched and searched and i found all of one article with the same problem as me. but with no soulotion.

i have tried various soulotions for similar problems but to no avail. (i have installed many many packages... not sure anyomre which ones...)

i am new to ubuntu, i do know the basics and some commands but please be specific.

thanks in advance!!!!
David (sorry my name is not IRON... that is my gamer name)

UPDATE:
i just ran it through terminal and got this:
owner@David-Asus:~$ '/home/owner/Desktop/steam.desktop' 
/home/owner/Desktop/steam.desktop: line 1: [Desktop: command not found
/home/owner/Desktop/steam.desktop: line 3: for: command not found
/home/owner/Desktop/steam.desktop: line 4: fg: no job control
/home/owner/Desktop/steam.desktop: line 8: FileTransfer: command not found
/home/owner/Desktop/steam.desktop: line 8: Game: command not found
/home/owner/Desktop/steam.desktop: line 10: Community: command not found
/home/owner/Desktop/steam.desktop: line 10: Library: command not found
/home/owner/Desktop/steam.desktop: line 10: Servers: command not found
/home/owner/Desktop/steam.desktop: line 10: Screenshots: command not found
/home/owner/Desktop/steam.desktop: line 10: News: command not found
/home/owner/Desktop/steam.desktop: line 10: Settings: command not found
/home/owner/Desktop/steam.desktop: line 10: BigPicture: command not found
/home/owner/Desktop/steam.desktop: line 10: Friends: command not found
/home/owner/Desktop/steam.desktop: line 12: [Desktop: command not found
/home/owner/Desktop/steam.desktop: line 22: steam://store: No such file or directory
/home/owner/Desktop/steam.desktop: line 24: [Desktop: command not found
/home/owner/Desktop/steam.desktop: line 33: steam://url/SteamIDControlPage: No such file or directory
/home/owner/Desktop/steam.desktop: line 35: [Desktop: command not found
/home/owner/Desktop/steam.desktop: line 45: steam://open/games: No such file or directory
/home/owner/Desktop/steam.desktop: line 47: [Desktop: command not found
/home/owner/Desktop/steam.desktop: line 57: steam://open/servers: No such file or directory
/home/owner/Desktop/steam.desktop: line 59: [Desktop: command not found
/home/owner/Desktop/steam.desktop: line 62: unexpected EOF while looking for matching `''
/home/owner/Desktop/steam.desktop: line 108: syntax error: unexpected end of file
owner@David-Asus:~$ 

lubuntu has the same problem.

---

### Post by dannyboy79 on 2014-11-15
how did you install steam?

---

### Post by irongolem0982 on 2014-11-15
i did it through ubuntu software center the first time, then after that failed i did it through terminal (not sure what i typed...), then i tried it agian after steams last major update through ubuntu software center.

---

### Post by oldrocker99 on 2014-11-15
You might try downloading the Steam client from steampowered.com. Then, to make sure the installation is right, type this into the console:
```
sudo dpkg -i steam_latest.deb
```
You'll get an error message (because dependencies are missing). Fix it with this:
```
sudo apt-get -f install
```
This should get it installed correctly, and it will (hopefully) run fine.

---

### Post by irongolem0982 on 2014-12-03
it works! apparently steam updated. thanks for your help!

---

