---
title: "[SOLVED] Wolfenstein: Enemy Territory... No sound :("
date: 2007-12-18
forum: Gaming &amp; Leisure
---

### Post by piratesmack on 2007-12-18
I downloaded and installed Wolfenstein: ET version 2.6, but there is no sound.

```

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/steven/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/steven/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/steven/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae35cf40  
Sys_LoadDll(ui) succeeded!
```

I'm using Gutsy

Any ideas?

Thanks

---

### Post by piratesmack on 2007-12-18
Oh sorry, it looks like something like this was posted before. I found the fix here:
[http://ubuntuforums.org/showthread.php?t=271075](http://ubuntuforums.org/showthread.php?t=271075)

---

### Post by ahaslam on 2007-12-19
Simply setting the sound quality to the highest setting often works as well ;)

---

### Post by piratesmack on 2007-12-19
Thanks

---

### Post by Homunculi on 2008-01-01
or you can just run a command from the terminal line 

this worked for me 

:~$wolf +set s_initsound 0

---

### Post by billybag on 2008-08-17
[http://community.enemyterritory.com/forums/showthread.php?t=20147](http://community.enemyterritory.com/forums/showthread.php?t=20147)

---

### Post by Doctoxic on 2008-11-26
> **ahaslam said:**
> Simply setting the sound quality to the highest setting often works as well ;)


:lolflag:

thanks

worked for me

doc

---

### Post by mag1strate on 2008-11-26
Thanks guys! I have been trying to find a fix for this problem!:)

---

### Post by budluva04 on 2009-02-19
yes i can also confirm in jaunty 9.04 setting volume to the highest setting gets sound working, restart et for it to take effect

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
<snip>
---------------------------------------------------------------------------------

---

### Post by Rhemat on 2009-07-30
So far, none of the solutions that I've tried have not worked for me.  I found this when I ran W:ET in terminal:

------- sound initialization -------
not initializing.
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/haunter/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/haunter/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/haunter/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xad770f40  
Sys_LoadDll(ui) succeeded!

I don't know how much of that is relevant, or if you need more info.  Just let me know.  Thanks in advance.

---

