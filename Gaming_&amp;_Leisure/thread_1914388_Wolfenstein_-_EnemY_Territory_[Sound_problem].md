---
title: "Wolfenstein - EnemY Territory [Sound problem]"
date: 2012-01-24
forum: Gaming &amp; Leisure
---

### Post by ztealmax on 2012-01-24
:confused:[IMG]http://imag.malavida.com/mvimgbig/download/wolfenstein-enemy-territory-4176-1.jpg[/IMG]

Hello all been surfing the web all night testing all solutions i could find,  trying to find a solution to that i dont have any sound in ***Wolfenstein - Enemy Territory***

i have an soundblaster Live soundcard works great viewing youtube, playing mp3 etc.

however when starting the game *Wolfenstein - Enemy Territory* i have no sound
so i tried downloading a script called *et-sdl-sound* still no sounds, installed alsa-oss 
to emulate oss still no sound ingame.

Does anyone have a working solution to get the game sound working, what do i need to install?
Can i enable OSS-Emulation in Alsa-kernel somehow?

Please any help with this would be greatly apriciated

Sincerally
:KSMartin "Ztealmax"

---

### Post by ztealmax on 2012-01-24
update: also tried with built in realtek audio card it doesnt work either so im thinking it has to do with
OSS emulation?

---

### Post by ubudog on 2012-01-24
Have you read [this]("https://help.ubuntu.com/community/EnemyTerritory#Sound_Issues")?

Best,
ubudog

---

### Post by ztealmax on 2012-01-24
> **ubudog said:**
> Have you read [this]("https://help.ubuntu.com/community/EnemyTerritory#Sound_Issues")?

Best,
ubudog


Yea thanx trouble is when trying this:

tried first option got this message: 
/dev/dsp: Input/output error Could not find /dev/dsp
```
sudo -i echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss exit
```and checking there is no folder or file called **oss** anywhere whitin card0 etc
so get error messages

Been up all night with this lol, damn i need more coffee ;)

---

### Post by ubudog on 2012-01-24
> **ztealmax said:**
> Yea thanx trouble is when trying this:

```
sudo -i echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss exit
```and checking there is no folder or file called **oss** anywhere whitin card0 etc
so get error messages


I once had this problem myself with this game... it looks as if you need to install OSS (tread carefully here).  I'll give you some more info once I do some searching.

> **ztealmax said:**
> 
Been up all night with this lol, damn i need more coffee ;)

Hehe :lolflag:

---

### Post by ztealmax on 2012-01-24
Thanx [[COLOR=#d40000]**ubudog**[/COLOR]]("http://ubuntuforums.org/member.php?u=739457") ill wait eager for a reply with more info :popcorn:

---

### Post by ubudog on 2012-01-24
Ok, someone [here]("http://ubuntuforums.org/showthread.php?t=271075") found something that worked.  This is what they did:
```
sudo killall esd
sudo -i 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et
```

Do those commands one at a time, and see if it works.  :)

---

### Post by ztealmax on 2012-01-24
> **ubudog said:**
> Ok, someone [here]("http://ubuntuforums.org/showthread.php?t=271075") found something that worked.  This is what they did:
```
sudo killall esd
sudo -i 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et
```Do those commands one at a time, and see if it works.  :)

thanx but i dont have a folder or file called oss in pcm0p :confused:


get following error messages:
bash: /proc/asound/card0/pcm0p/oss: File or catalog dont exist
esd: no process found
//Rougly translated from Swedish

So iguess i need to install something more?

---

### Post by ztealmax on 2012-01-24
Ok an little update now, ive installed update from here:
wget [ftp://ftp.idsoftware.com/idstuff/et/ET-2.60b.zip](ftp://ftp.idsoftware.com/idstuff/et/ET-2.60b.zip)
with that version i have sound

however server list doesnt work
for that i used this update:
[http://etmaster.net/files/ET260_linux.zip](http://etmaster.net/files/ET260_linux.zip) 
however with that patch or et.x86 file i get no sound what so ever

more info about what it does here:
[http://etmaster.net/](http://etmaster.net/)

any suggestions about this is greatfull

maybe its possible to mod the 2.60b from idsoftare to 
use master0.etmaster.net as main server?

**UPDATE: **

i tried to edit it with Bless editor however get this errors:


```
d: 4: can't cd to /media/spel/enemy-territory
/usr/games/tce: 14: elsemaster0.etmaster.net: not found
Unsupported architecture or dpkg --print-architecture doesn't work.
Segmentation fault

```erhm think i did something wrong here ;)

still i need help replacing or modding the original [ET-260B.zip]("ftp://ftp.idsoftware.com/idstuff/et/ET-2.60b.zip") from idsoftware so i still have sound.

So any help is apriciated

What is needed to mod in file above from idsoftware is:

change **etmaster.idsoftware.com** to **master0.etmaster.net**

Sincerally
Martin "Ztealmax"

---

### Post by ztealmax on 2012-01-26
Ok this is the deal as i can figure it out correctly
 
et.x86 2.60b standard update sound works with playdeb
et.x86 2.60b modded version to get serverlist working sound stops working.
 
Now this is why:
[sdl script]("https://github.com/nullkey/et-sdl-sound") that comes with playdeb checks crc32 on file et.x86 and if 
it doesnt match the crc32 it doesnt work, so only way around this
is to use standard update et.x86 2.60b and modify host file instead 
so when it asks for idsofware.com it will redirect to the other server.
 
Now you have both working server list and sound.
 
However ive mailed the makers of the [sdl script]("https://github.com/nullkey/et-sdl-sound") that checks crc32
for et.x86 to see if they could do a little update to include the new modded version
 
Lets hold thumbs and see what they reply
 
 
et-sdl-sound currently supports following binaries:
 
CRC32 description
0x6ab49f82 ET 2.60b (et.x86)
0x3b18a889 ET 2.60 (et.x86)
0x3d59a703 ET 2.56 (et.x86)
0x21e60afb ET 2.55 (et.x86)
0xc6aebd79 Wolf 1.41 (wolfsp.x86)
0xd5676d8f Wolf 1.41-MP (wolf.x86)
0xdc49bc09 Q3 1.31 (quake3.x86)
0x10f74d19 Q3 1.32 (quake3.x86)
0xe5782e44 Q3 1.32b (quake3.x86)
0x2f3661cf Q3 1.32c (quake3.x86)
 
 
Sincerally
Martin "Ztealmax"
 
**UPDATE: **
 
hmm check the source code and this is what i found
```

[COLOR=#009999]case[/COLOR]
[COLOR=#009999]0x6ab49f82[/COLOR]**: ->>> THIS IS 2.60b CRC32**
        version **=** [COLOR=#dd1144]"ET 2.60b"[/COLOR];
 
 
        writeJump((**[COLOR=#445588]void[/COLOR]** *****) [COLOR=#009999]0x08188250[/COLOR], (**[COLOR=#445588]void[/COLOR]** *****) SNDDMA_Init);
        writeJump((**[COLOR=#445588]void[/COLOR]** *****) [COLOR=#009999]0x08188840[/COLOR], (**[COLOR=#445588]void[/COLOR]** *****) SNDDMA_GetDMAPos);
        writeJump((**[COLOR=#445588]void[/COLOR]** *****) [COLOR=#009999]0x081888d0[/COLOR], (**[COLOR=#445588]void[/COLOR]** *****) SNDDMA_Shutdown);
        writeJump((**[COLOR=#445588]void[/COLOR]** *****) [COLOR=#009999]0x081888f0[/COLOR], (**[COLOR=#445588]void[/COLOR]** *****) SNDDMA_BeginPainting);
        writeJump((**[COLOR=#445588]void[/COLOR]** *****) [COLOR=#009999]0x081888e0[/COLOR], (**[COLOR=#445588]void[/COLOR]** *****) SNDDMA_Submit);
 
 
        _Cvar_Get **=** (cvar_t***** (*****) (**const** **[COLOR=#445588]char[/COLOR]** *****, **const** **[COLOR=#445588]char[/COLOR]** *****, **[COLOR=#445588]int[/COLOR]**)) [COLOR=#009999]0x08073bb0[/COLOR];
        dma **=** (dma_t *****) [COLOR=#009999]0x0926d3a4[/COLOR];
        **break**;

```
 
And yea im not good with coding but i would expect maybe some update to crc32 check would do the trick, any one know anything about compiling?

---

### Post by TurtleKing on 2012-01-26
Sorry to interrupt without a fix, but wasn't their an announcement about ending support for this game in 2011? I did a Google search and got "PB discontinued support for Wolfenstein Enemy Territory - October 2011".

---

### Post by ztealmax on 2012-01-29
> **TurtleKing said:**
> Sorry to interrupt without a fix, but wasn't their an announcement about ending support for this game in 2011? I did a Google search and got "PB discontinued support for Wolfenstein Enemy Territory - October 2011".

Yes thats why they did a new patch pointing to another server list, therfor this 
sound fix for that patch!

---

