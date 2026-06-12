---
title: "Quake Dilema"
date: 2006-11-22
forum: Gaming &amp; Leisure
---

### Post by Xyhthyx on 2006-11-22
Hi, I'm having a troublesome dilema with Quake 1 on Edgy. I've untar'd the latest ezQuake into a folder called 'ezquake' in my home directory (~/ezquake/). Inside I made my 'id1' folder and placed the pak0 and pak1 files from my original Quake, so far so good. I hop on the terminal and cd to my 'ezquake' folder and run ./ezquake-gl.glx and it starts up just fine.

After this I have 2 problems:
1. My settings are never saved, no configs are made or modified.
2. I can run the game only if I cd to the directory and run ezquake-gl.glx. If I am in a different directory and run it I get a missing file error (for example, running it from my desktop folder: ~/Desktop$ ~/ezquake/./ezquake-gl.glx   <-- this results in a missing wad file error I would not normally get running it from the ezquake folder).
3. The client has an in-game server browser that doesn't display any servers. I assume this is so because it cannot read the servers from a text file they are saved in.

Everything is in my home folder, doing everything without sudo. Even running the game as sudo it still doesn't save my settings etc. I even ran the windows version through wine and got the same trouble. Any help is greatly appreciated.

---

### Post by aidanr on 2006-11-22
1. the command to save your config settings is "writeconfig [configname]" (without quotes)

2. i've a file /usr/local/bin/quake which contains
```
#!/bin/sh 
# Needed to make symlinks/shortcuts work. 
# the binaries must run with correct working directory 
cd "/home/aidan/games/quake/" 
exec ./glx
```
and the glx file contains
```
export LD_PRELOAD=/lib/libpthread.so.0
./fuhquake-gl.glx -mem 32 -democache 32768 -nomdga -current -fullscreen -conwidth 1440 -conheight 900 -particles 8192 -ruleset smackdown +cfg_load opengl.cfg -norjscripts -gamma 0.7
```
both are executable, i think the important thing here is that the quake executable in /usr/local/bin changes directory to the quake folder first

3. [xqf]("http://www.linuxgames.com/xqf/") works very well for finding servers
in the ***xqf->preferences->games*** putting in "quake" for the command line option doesn't work so you have to put in the full path including options and also have to put in the working directory, for me it's 
```
Command Line: /home/aidan/games/quake/fuhquake-gl.glx -mem 32 -democache 32768 -nomdga -current -fullscreen -conwidth 1440 -conheight 900 -particles 8192 -ruleset smackdown +cfg_load opengl.cfg -norjscripts -gamma 0.7
Working Directory: /home/aidan/games/quake/
```


edit:// actually come to think of it, having "quake" and "glx" is pretty pointless, think i'll just merge the two

---

### Post by Xyhthyx on 2006-11-22
Thank you very much, your workarounds worked profectly. I guess I was counting on ezquake to keep a default config file but it doesn't, I need to manualy save it and autoexec it on startup. The script for launching the game works perfectly. And the in-game server browser, turns out I just needed to press the spacebar to retrieve the list (I thought it would do it auto but I guess not). Thanks for your help.

---

### Post by aidanr on 2006-11-22
no problem, happy fragging;)

---

