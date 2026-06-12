---
title: "how to make sound in wolfenstein work?"
date: 2008-02-22
forum: Gaming &amp; Leisure
---

### Post by internetishere on 2008-02-22
How can i get my sound to work in wolfenstein enemy territory
ive had it working before i  used like a 5line command or sumtin i dont remember what it was though can anyone help me out?
the original comand went sumtin similar to this i think

killall sumtin
sudo -i
i think echo sumtin went here
then i think it was exit or something
then et
and it worked i need to reenter whatever that command was or another command that might work can someone help me?

---

### Post by Dark Aspect on 2008-02-22
> **internetishere said:**
> How can i get my sound to work in wolfenstein enemy territory
ive had it working before i  used like a 5line command or sumtin i dont remember what it was though can anyone help me out?
the original comand went sumtin similar to this i think

killall sumtin
sudo -i
i think echo sumtin went here
then i think it was exit or something
then et
and it worked i need to reenter whatever that command was or another command that might work can someone help me?

[http://ubuntuforums.org/showthread.php?t=362231](http://ubuntuforums.org/showthread.php?t=362231)

Worked for me.

---

### Post by Dark Aspect on 2008-02-22
> **internetishere said:**
> How can i get my sound to work in wolfenstein enemy territory
ive had it working before i  used like a 5line command or sumtin i dont remember what it was though can anyone help me out?
the original comand went sumtin similar to this i think

killall sumtin
sudo -i
i think echo sumtin went here
then i think it was exit or something
then et
and it worked i need to reenter whatever that command was or another command that might work can someone help me?

[http://ubuntuforums.org/showthread.php?t=362231]("http://ubuntuforums.org/showthread.php?t=362231")

Worked for me.

Edit:Ugh I am sorry for some reason the forum double posted my post can a mod please delete one..sorry!!

---

### Post by LordBanter on 2009-05-14
Hi, 

I was going nuts with this Wolfenstein Enemy Territory sound issue. I have installed the game, but the sound was not working at all. I have tried almost all available solutions from the Internet. None worked. However I have managed to make one solution work properly for me and voila! I HAVE SOUND & MUSIC NOW! :))) Read on how I made it:

1. I have downloaded this script: [http://nullkey.ath.cx/~stuff/et-sdl-sound/wolfsp-sdl-sound.gz]("http://nullkey.ath.cx/%7Estuff/et-sdl-sound/wolfsp-sdl-sound.gz"). (Alternative mirror: [http://members.lycos.co.uk/lordbanter/wolfsp-sdl-sound.gz](http://members.lycos.co.uk/lordbanter/wolfsp-sdl-sound.gz) )
2. The script was not working from scratch. I have had to edit it manually. First locate where your Wolfenstein installation directory is (via locating et.x86 file. The dir/folder where the file is, is your installation dir. In my case it was /usr/local/games/enemy-territory )
3. Now open downloaded script wolfsp-sdl-sound file with text editor (on my Mandriva I just used KWrite, but for Ubuntu just use distro default one)
4. At the beginning of the file you will find disabled grey text/comment. There will be such a text (search for it): "*# You can set this in GAME_PATH environment variable*" and just underneath the variable GAME_PATH="". 
5. Remove the hash (#) from before the GAME_PATH variable. The text may become colorful as it is no longer disabled comment.
6. Now type in your full path to Wolfenstein installation dir between inverted comas. In my case it looked like this: GAME_PATH="/usr/local/games/enemy-territory"
7. Now go down the file, and locate another variables which are GAME_BIN and GAME_DIR.
8. Change value of GAME_BIN to GAME_BIN='et.x86'
9. Change value of GAME_DIR to your Wolfenstein installation dir only (not a path!). In my case it was: GAME_DIR='enemy-territory'.
10. That's it!
11. Now drag and drop your edited "wolfsp-sdl-sound" file into the console window and execute it by pressing ENTER. Voila! The Wolfenstein is running with SOUND now!
12. [applause] ;)

The main problem with Linux is this damned console/script thing. I mean how they are going to beat Windows, as main Windows advantage is GRAPHICALLY operated environment, not TEXT operated one! This must be changed and all console commands/scripts should have GRAPHICAL (icon to click) equivalent.

Enjoy! 

Banter

---------------------------------------------------------------------------------
Brand new advanced Amiga compatible! Visit [www.natami.net]("http://www.natami.net")
---------------------------------------------------------------------------------

---

