---
title: "no sound in wolfenstein"
date: 2007-07-13
forum: Gaming &amp; Leisure
---

### Post by mr.farenheit on 2007-07-13
i successfully installed wolfenstein enemy territory but now have no sound. i made sure it wasn't a sound card error because i still have audio from my media players and also from viewing web content. is there something that is disabling sound in 3d mode? plz help

---

### Post by wana10 on 2007-07-13
try this in terminal 'killall esd; et'

---

### Post by mr.farenheit on 2007-07-14
it gives an error saying command et not found

---

### Post by Doctoxic on 2007-07-14
[https://help.ubuntu.com/community/EnemyTerritory]("https://help.ubuntu.com/community/EnemyTerritory")

---

### Post by LordBanter on 2009-05-14
Hi,

I was going nuts with this Wolfenstein Enemy Territory sound issue. I have installed the game, but the sound was not working at all. I have tried almost all available solutions from the Internet. None worked. However I have managed to make one solution work properly for me and voila! I HAVE SOUND & MUSIC NOW! )) Read on how I made it:

1. I have downloaded this script: [http://nullkey.ath.cx/~stuff/et-sd](http://nullkey.ath.cx/~stuff/et-sd) [...] -sound.gz. (Alternative mirror: [http://members.lycos.co.uk/lordban](http://members.lycos.co.uk/lordban) [...] l-sound.gz )
2. The script was not working from scratch. I have had to edit it manually. First locate where your Wolfenstein installation directory is (via locating et.x86 file. The dir/folder where the file is, is your installation dir. In my case it was /usr/local/games/enemy-territory )
3. Now open downloaded script wolfsp-sdl-sound file with text editor (on my Mandriva I just used KWrite, but for other distro just use default one)
4. At the beginning of the file you will find disabled grey text/comment. There will be such a text (search for it): "# You can set this in GAME_PATH environment variable" and just underneath the text there will be the variable called GAME_PATH="".
5. Remove the hash (#) from before the GAME_PATH variable. The text may become colorful as it is no longer disabled comment.
6. Now type in your full path to Wolfenstein installation dir between inverted comas. In my case it looked like this: GAME_PATH="/usr/local/games/enemy-territory". It is like this by defauld, so you may just use it, if you haven't change installation dir.
7. Now go down the file, and locate another variables which are GAME_BIN and GAME_DIR.
8. Change value of GAME_BIN to GAME_BIN='et.x86'
9. Change value of GAME_DIR to your Wolfenstein installation dir only (not a path!). In my case it was: GAME_DIR='enemy-territory'. It's default folder (directory/catalog whatever you call it...) so if you haven't change it during installation, use that one.
10. That's it!
11. Now drag and drop your edited "wolfsp-sdl-sound" file into the console window and execute it by pressing ENTER. Voila! The Wolfenstein is running with SOUND now!
12. [applause]

The main problem with Linux is this damned console/script thing. I mean how they are going to beat Windows, as main Windows advantage is GRAPHICALLY operated environment, not TEXT operated one! This must be changed and all console commands/scripts should have GRAPHICAL (icon to click) equivalent.

Enjoy!

Banter

---------------------------------------------------------------------------------
Brand new advanced Amiga compatible! Visit [www.natami.net](www.natami.net)
---------------------------------------------------------------------------------

---

