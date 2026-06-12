---
title: "Wolfenstein: Enemy Territory has no Sound?"
date: 2012-06-01
forum: Gaming &amp; Leisure
---

### Post by namone on 2012-06-01
I know, there are tons of these forum posts and pages. I have tried every single one, none of them work! It is getting very frustrating...

Here is the log:

[HTML]------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/alex/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/alex/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/alex/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xed7dff40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ubuntu
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v1.152 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
[/HTML]

I also have tried everything on the Ubuntu Documentation.

---

### Post by idoitprone on 2012-06-01
> **namone said:**
> I know, there are tons of these forum posts and pages. I have tried every single one, none of them work! It is getting very frustrating...

Here is the log:

[HTML]------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/alex/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/alex/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/alex/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xed7dff40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ubuntu
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v1.152 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
[/HTML]I also have tried everything on the Ubuntu Documentation.

try
> /dev/dsp: No such file or directory
Could not open /dev/dsp
this is you problem. It expects open sound system api

try using the pulse audio wrapper

run this in terminal
```
padsp programName
```

---

### Post by namone on 2012-06-01
> **idoitprone said:**
> try

this is you problem. It expects open sound system api

try using the pulse audio wrapper

run this in terminal
```
padsp programName
```


Still no luck, I ran this command:

[HTML]padsp et[/HTML]

It started the game, but alas, no sound.

---

### Post by idoitprone on 2012-06-01
> **namone said:**
> Still no luck, I ran this command:

[HTML]padsp et[/HTML]It started the game, but alas, no sound.

you got me curious. I tried it too 

and this error still shows

```
/dev/dsp: No such file or directory
Could not open /dev/dsp
```I wonder if it is a bug with pulse audio oss emulation

you can the oss emulation modules
```

sudo modprobe snd_seq_oss snd_pcm_oss snd_mixer_oss
```

---

### Post by idoitprone on 2012-06-02
you can go the destructive route and change your sound system tol oss4 

[http://www.opensound.com/wiki/index.php/Building_OSSv4_from_source](http://www.opensound.com/wiki/index.php/Building_OSSv4_from_source)

note: it might end up bring your system to no sound, but it is very unlikely

---

### Post by garyzw on 2012-06-02
Hopefully you’ll be enjoying an Enemy Territory game with the sound of explosions and shots in your ears, but if the previous solutions didn’t do the trick do not despair, there’s still hope. I’ve found a different solution in this thread and it consists in the following:

a) Download this script: [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh") ([[URL="http://members.lycos.co.uk/lordbanter/wolfsp-sdl-sound.gz"]original download link]("http://nullkey.ath.cx/~stuff/et-sdl-sound/wolfsp-sdl-sound.gz")[/URL], [alternative download link]("http://nullkey.ath.cx/~stuff/et-sdl-sound/wolfsp-sdl-sound.gz")), created by Pyry Haulos.

b) Open it with a text editor and customize it to match your configuration: change the line «GAME_PATH=”/home/games/enemy-territory”» to point to the location of your Enemy Territory installation (most likely «GAME_PATH=”/usr/local/games/enemy-territor”»); in case your directory with the game files isn’t called «enemy-territory» like in the example you’ll also need to adapt the GAME_DIR variable.

c) Save this file somewhere on your computer, make it executable if needed (you can do this by right clicking on it, selecting “Properties” and under the “Permissions” tab of the dialogue that will show up checking the box to allow execution of the file). Done, now whenever you want to run the game just start it by running this file.

[http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/](http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/)

---

### Post by idoitprone on 2012-06-02
> **garyzw said:**
> Hopefully you’ll be enjoying an Enemy Territory game with the sound of explosions and shots in your ears, but if the previous solutions didn’t do the trick do not despair, there’s still hope. I’ve found a different solution in this thread and it consists in the following:

a) Download this script: [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh") ([]("http://nullkey.ath.cx/%7Estuff/et-sdl-sound/wolfsp-sdl-sound.gz")[original download link]("http://members.lycos.co.uk/lordbanter/wolfsp-sdl-sound.gz"), [alternative download link]("http://nullkey.ath.cx/%7Estuff/et-sdl-sound/wolfsp-sdl-sound.gz")), created by Pyry Haulos.

b) Open it with a text editor and customize it to match your configuration: change the line «GAME_PATH=”/home/games/enemy-territory”» to point to the location of your Enemy Territory installation (most likely «GAME_PATH=”/usr/local/games/enemy-territor”»); in case your directory with the game files isn’t called «enemy-territory» like in the example you’ll also need to adapt the GAME_DIR variable.

c) Save this file somewhere on your computer, make it executable if needed (you can do this by right clicking on it, selecting “Properties” and under the “Permissions” tab of the dialogue that will show up checking the box to allow execution of the file). Done, now whenever you want to run the game just start it by running this file.

[http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/](http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/)

this command relies on the snd_xx_oss modules
echo "et.x86 0 0 direct" | sudo tee /proc/asound/card0/pcm0p/oss

hmmmm i didnt realize that this game have this much problems. I should of looked deeper, but I have a feeling tht a little too involved

---

### Post by garyzw on 2012-06-02
But the method does work-- I used it my self
Wonder why this problem was never fixed by ID?

> **idoitprone said:**
> this command relies on the snd_xx_oss modules
echo "et.x86 0 0 direct" | sudo tee /proc/asound/card0/pcm0p/oss

hmmmm i didnt realize that this game have this much problems. I should of looked deeper, but I have a feeling tht a little too involved

---

### Post by diehardlinux on 2012-10-15
> **idoitprone said:**
> try

this is you problem. It expects open sound system api

try using the pulse audio wrapper

run this in terminal
```
padsp programName
```

This command works for me in kubuntu 12.04 with the "etsound" patch.just ran the following command: padsp et-sdl-sound (sybolic link placed in /usr/bin/. 

note: you may have to change the etsound script to point to where you et file is installed.

now i just have to work on the video part to get the game working.

---

### Post by holastickboy on 2012-10-16
This problem has honestly been happening for years.

---

### Post by garyzw on 2012-10-16
I found an easy way to install Wolfenstein: Enemy Territory from the PlayDeb website

[http://www.getdeb.net/updates/Ubuntu/12.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/12.04#how_to_install)

Once you install he [getdeb]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1%7Egetdeb1_all.deb") package  you go here and click "install this now"

[http://www.playdeb.net/software/Enemy%20Territory](http://www.playdeb.net/software/Enemy%20Territory)

Once it is installed the game runs perfectly with sound.

---

### Post by Johnmac63 on 2013-07-11
> **garyzw said:**
> I found an easy way to install Wolfenstein: Enemy Territory from the PlayDeb website

[http://www.getdeb.net/updates/Ubuntu/12.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/12.04#how_to_install)

Once you install he [getdeb]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1%7Egetdeb1_all.deb") package  you go here and click "install this now"

[http://www.playdeb.net/software/Enemy%20Territory](http://www.playdeb.net/software/Enemy%20Territory)

Once it is installed the game runs perfectly with sound.




I installed it this way(had to use google chrome and not firefox) and game works great with sound, only problem is I can not find an etwolf folder on my computer or any config files, any time I open the game I have to make changes all over again eg screen resolution and any option changes.

---

### Post by garyzw on 2013-07-11
> **Johnmac63 said:**
> I installed it this way(had to use google chrome and not firefox) and game works great with sound, only problem is I can not find an etwolf folder on my computer or any config files, any time I open the game I have to make changes all over again eg screen resolution and any option changes.

The [COLOR=#000000]etwolf folder should be hidden under the Home directory--just unhide by using ctrl h and you should see it.[/COLOR]

---

### Post by dmn_clown on 2013-07-13
> **garyzw said:**
> Wonder why this problem was never fixed by ID?

Because Lennart Poettering hadn't destroyed sound on Linux when the last patch to this game was released.  If you don't mind getting your hands dirty you can checkout the source code from [https://github.com/id-Software/Enemy-Territory](https://github.com/id-Software/Enemy-Territory) and add the sdl sound driver from open arena.

---

### Post by tkmn on 2013-07-14
Check out ET: Legacy

[http://www.etlegacy.com/](http://www.etlegacy.com/)

---

