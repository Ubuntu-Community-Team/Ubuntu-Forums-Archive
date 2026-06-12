---
title: "Return to Castle Wolfenstein Sound Problem"
date: 2013-05-15
forum: Gaming &amp; Leisure
---

### Post by gezeichnet on 2013-05-15
Hi,
I´m realy new to Linux as Desktop System, i used it as server or for smaller tasks.
Now I installed Ubuntu (12.04) and Elementary Luna on my Laptop and wanted to run some Games.

I followed [this]("http://wiki.ubuntuusers.de/Spiele/RTCW") instruction, to get it running, but i have the sound-issue on both systems. I tried similar fixes (like [this]("http://ubuntuforums.org/showthread.php?t=362231&page=17")), but i can´t get it to run with sound.

I dont know if i have to take alsa or pulse, libSDL and libSDL-dev are installed, but i dont know where, and i dont know how to refenernce them in a startup file.

Can Anyone please help me?

PS: i want to play RTCW, not Enemy Teretory.

---

### Post by garyzw on 2013-05-16
I use this script for Enemy-Territory: [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh") and it worked great maybe modify it a llttle and it should work with Return to Castle Wolfenstein?

a) Download this script: [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh") ([original download link]("http://nullkey.ath.cx/%7Estuff/et-sdl-sound/wolfsp-sdl-sound.gz"), [alternative download link]("http://members.lycos.co.uk/lordbanter/wolfsp-sdl-sound.gz")), created by [Pyry Haulos]("http://nullkey.ath.cx/").
 

b) Open it with a text editor and customize it to match your configuration: change the line «*GAME_PATH=”/home/games/enemy-territory”*» to point to the location of your *Enemy Territory* installation (most likely «*GAME_PATH=”/usr/local/games/enemy-territor”*»); in case your directory with the game files isn’t called «*enemy-territory*» like in the example you’ll also need to adapt the *GAME_DIR* variable.
 

c) Save this file somewhere on your computer, make it executable if   needed (you can do this by right clicking on it, selecting “Properties”   and under the “Permissions” tab of the dialogue that will show up   checking the box to allow execution of the file). Done, now whenever you   want to run the game just start it by running this file.

---

### Post by CatKiller on 2013-05-18
It's a long time since I did it, so I can't remember any details, but I recall that I had to sudo -i and echo something somewhere to get sound out of RtCW. It worked fine after that, but I had to do it again if I'd rebooted.

That probably doesn't help at all :)

---

### Post by gezeichnet on 2013-05-24
Thanks for your help,
but it doesnt work, can you please help me again, I'm realy new to linux espacially to gaming on Linux, i try to descipe what i did.

1. Downloaded you Script (wolfsp-sdl-sound)
2. changed the gamedir to "/usr/local/games/wolfenstein"

> 
GAME_PATH="/usr/games/local/wolfenstein/"

 
3. made it executable 
> 
chmod a+x wolfsp-sdl-sound.sh

is that right?

4. tried running it
> 
bash wolfsp-sdl-sound.sh

only running the following doesnt work?!
> 
wolfsp-sdl-sound


5. get some errors, nothing starts :(
> 
find: `/usr/lib32/': No such file or directory
[wolfsp-sdl-sound] info   : 32-bit libSDL.so is installed to /usr/lib/i386-linux-gnu/libSDL-1.2.so.0.11.3
[wolfsp-sdl-sound] info   : library is written to /tmp/et-sdl-sound.so
[wolfsp-sdl-sound] info   : launching the game...
wolfsp-sdl-sound.sh: line 1578: cd: /usr/games/local/wolfenstein/: No such file or directory
wolfsp-sdl-sound.sh: line 1582: ./wolsp.x86: No such file or directory
[wolfsp-sdl-sound] info   : done


i can follow some of these errors, when i type "cd /usr/games/wolfenstein/" in the terminal, i can access the gamedir, why cant it find the dir?
how can i fix the other errors?

here is my config in the sh file
> 
GAME_PATH="/usr/games/local/wolfenstein/"


# libSDL.so
#
# You can set this in LIBSDL environment variable
# LIBSDL=""


# Temporary directory
TMP_DIR="/tmp"


# Use 'find' if can't locate the game or libSDL otherwise
USE_FIND="yes"


# SDL audio driver
SDL_AUDIODRIVER="alsa"


# Just extract et-sdl-sound.so
ONLY_EXTRACT="no"




# Do not touch anything below this line!
SCRIPT_NAME='wolfsp-sdl-sound'
GAME_BIN='wolfsp.x86'
GAME_DIR='wolfenstein'


---

### Post by garyzw on 2013-06-25
gezeichnet,

Are you running this in a 64 bit system? If so I have Return to Castle Wolfenstein running perfectly natively in Linux. No sound issus at all. Let me know

---

