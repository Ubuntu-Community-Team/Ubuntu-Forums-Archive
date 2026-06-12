---
title: "When I install a native linux game..."
date: 2007-05-05
forum: Gaming &amp; Leisure
---

### Post by chocomoojuice on 2007-05-05
Should I install the game to my home folder, or should I start the install file with sudo from terminal and install it to the default directory (usr/local/...)?  I would usually go with the latter.... but since I'm installing World of Padman, and the following [forum topic]("http://ubuntuforums.org/showthread.php?t=427205") suggested: 
> launch the game ONLY from: Application -> Games -> World of Padman
I am a little hesitant to.  This is because I realize that I'll need to launch the game with sudo rights, and the only way I can think of doing that is via the terminal.

P.S.
I would've posted this in the beginners section, but it's regarding a game, so sorry if this is a dumb question :(

---

### Post by MonkeyBoy on 2007-05-05
I ran the installer without sudo and the game auto installed to my home directory but as a hidden directory.  It made itself a games menu launcher and seems to work just fine without sudoing anything.

---

### Post by scotty2hott2k on 2007-05-05
iirc it is a 'bug' in the installer, if you install the game with sudo (and the installer) but don't click play now (or similar) but quit the installer, everything will be fine and you will be able to play without using sudo.

---

### Post by Perfect Storm on 2007-05-07
Installation guide: [http://gaming.gwos.org/e107_plugins/content/content.php?content.63](http://gaming.gwos.org/e107_plugins/content/content.php?content.63)

---

### Post by crane on 2007-05-07
I would suggest you install it to /usr/local/games.
Use sudo and run the installer but do not launch the game.(refert o the how to linked above)
Reason I suggest this it simple. Once you have installed and you run it as a user, it will create a hidden file in your home directory called .wop or something like that. (I don't recall the name) Then your configs and files can be dumped there. Then if something every goes horribly wrong with the game just delete the hidden folder in your home directory and restart the game. It will creat a new folder and you will be back to a default install.

I used to do the same thing with quake3, 4, UrT, .doom3 and more. What I would do was install a new map into the hidden directory and play. Once I was sure the file caused no problems I would move it to /usr/local/games/quake3.baseq3 or where ever it needed to go.

Just my .02

---

