---
title: "Please help w/Wolf ET install."
date: 2007-05-30
forum: Gaming &amp; Leisure
---

### Post by Sweet Spot on 2007-05-30
Hey guys. I'm definitely not one to pose a question without having searched the forums in order to help myself first, but for some reason I'm having a hell of a time just trying to do a basic install of Enemy Territory. 

Perhaps I missed it, (and yes, the first thing I saw was the "read me, installing ET" thread) but is there a REALLY EASY yet comprehensive post which deals with all of the possible up to date issues of installing this game ?  Reading through all of the different posts in that install thread, got me quickly confused, and trying way too many things which were probably irrelevant to me. 

I'm running Dapper, 6.06 32 bit. Downloaded the files :

et-linux-2.60.x86.run
and The 2.60b patch I guess which is:
et.x86

The run file is sitting on my desktop, as is the ET 2.60b folder with the et.x86 file.   I've tried several variations of code to execute the install, but none of them have done squat. And yes, the files are all executable. I'm also getting kind of scared off in regards to having more issues once its installed, like the sound, and punkbuster stuff. 

Isn't there just one thread/post which is dedicated to serving the purpose of all the issues at once ? It's a bit nerve wrecking to have to go through tons of posts only to turn up negative results.  I'd really like to install as a regular user too, and not root. Read about the issues w/that. 

I'd really appreciate it if someone could see it in their heart to spell all of this out for me and my total lack of knowledge/noobness. Perhaps step by step. I have installed other games successfully, and have learned a thing or two, but for some reason, this has me stumped. A little learning might go a long way here... Seriously, I feel like I'm a child whom needs to be taught the alphabet for the first time.

TIA for anyone with a bit of patience. 

Doug

---

### Post by Rafty on 2007-05-30
this works in most cases:

**1)** download ET Full 2.60 with this command in a terminal (if it's not already downloaded):
```
wget http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run
```

**2)**open a terminal, change to the folder with the downloaded file and install ET with this commands:
```
sudo apt-get install libgtk1.2
```
```
chmod +x et-linux-2.60.x86.run
```
```
sudo ./et-linux-2.60.x86.run
```
exit the installer.

**3)** start ET in a terminal or via execute
```
et
```
the first mask needs to be completed at first. important: enable punkbuster! save this new profile and restart ET.

good luck ;)

---

### Post by Sweet Spot on 2007-05-30
Unless I'm doing something totally wrong, it says: > bash: cd: home/*******/desktop/et-linux-2.60.x86.run: No such file or directory
What am I missing ? It seems I do this quite often. (make mistakes that is)  Does the file its self have to be in a folder, or is it ok just sitting on the desktop ?  I really appreciate those explicit instructions, and only wish I wasn't such a dolt when it came to this stuff. I didn't download the file again, since it was already sitting on my desktop btw.

---

### Post by Sweet Spot on 2007-05-30
Wait, wait... got it ! I think it's just that I always put "Desktop" in lower caps. so I never actually get to the directory. Ok, it's installing into  /usr/local/games and the link is /usr/local/bin. Yeah, just finished. Still getting some errors as with other games though:

Edit

---

### Post by meborc on 2007-05-30
do you get to the game and there is no sound? or do you just see this message and don't get to the game?

for the first option there is an easy fix... to the second... well, i never had that problem

---

### Post by Sweet Spot on 2007-05-30
Nevermind, I just got my *** plastered in the game, full sound and all. Looks great ! Thanks a lot !  Now I just have to download map packs, and other stuff. 

Doug

---

### Post by Sweet Spot on 2007-05-30
Wait, hold on a sec... What about the PATCH ?   The "et.x86" file ?  What do I do with that one, and what does it do exactly ?I cd'd to my desktop and tried to open it but didn't do anything.

---

### Post by Rafty on 2007-05-31
no, the 2.60b patch is a only security patch. this patch can cause serious probs in some cases.
but it's possible to close this security leak without the patch. just go "options - game" and set "use ftp/http downloads" to "no".

if you really want to have 2.60b do this in a terminal:
```
wget "http://ftp.freenet.de/pub/4players/hosted/et/official/ET-2.60b-linux.zip"
```
```
unzip ET-2.60b-linux.zip -d ~/Desktop/260b
```
```
cd ~/Desktop
```
```
sudo cp "/usr/local/games/enemy-territory/et.x86" "/usr/local/games/enemy-territory/et.x86.bak"
```
```
sudo cp "/usr/local/games/enemy-territory/etded.x86" "/usr/local/games/enemy-territory/etded.x86.bak"
```
```
sudo cp "260b/Enemy Territory 2.60b/linux/et.x86" "/usr/local/games/enemy-territory/et.x86"
```
```
sudo cp "260b/Enemy Territory 2.60b/linux/etded.x86" "/usr/local/games/enemy-territory/etded.x86"
```

---

### Post by asipi on 2007-06-01
it's highly recommended to upgrade 2.60b, the most of the servers requires it

---

### Post by Rafty on 2007-06-01
> **asipi said:**
>  the most of the servers requires it
the server version (2.60 or 2.60b) doesn't matter.

---

### Post by asipi on 2007-06-01
it does, dude...
etpro 3.2.6, jaymod 2.14, noquarter 1.1 all requires both client and server side 2.60b
beleive me I am running gameservers, and I'm also a fanatic ET player :)

and:
if server running 2.60b but u have only 2.60, Punkbuster often kicks you with game integrity error

---

### Post by Rafty on 2007-06-01
oh ok! i never noticed that ;)

but it's not a miss to have the two old 2.60 files as backup :D

---

### Post by Shadowmeph on 2007-06-02
ok I only have about 3 days experience with linux but I am learning.
Anyway, I was having the same problem but now that I have the game installed I have run into a new problem which is that when I try to run the game it starts for a second then goes back to desk top this is what show up on the terminal;

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/meph/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect

not sure whats up with that or what it all means my system =3.4 ghz, 1.5gigram /ati x800 video card soundblaster live5.1 sound card and the os is feisty fawn I hope that this is enough information to help

---

### Post by asipi on 2007-06-02
you need to install 3D driver for your videocard. It won't work with a software renderer like mesa.

I never had an ati card but as I know fglrx is in the repository you should simply install it (or anyhow it called... :) )

next step will be the sound I guess after the video driver will be fine ;) I recommend to disable gnome's sound system

---

### Post by asipi on 2007-06-02
> **Rafty said:**
> oh ok! i never noticed that ;)

but it's not a miss to have the two old 2.60 files as backup :D
Could come handy if the downloaded files are corrupted ;) but anyway 2.60b is backward compatible with 2.60, so you can connect to normal 2.60 servers

---

### Post by Sweet Spot on 2007-06-02
Thanks a lot asipi, I'll apply the patch when I've got some time to actually play. I tried setting up a server, but couldn't figure out how to do a free for all match rather than a campaign ? 

By the way, and totally off topic... Where in Hungary do you live ? My wife is from Nyiregyhaza, and her family still lives there. We both visited this past September for our wedding, (and lots of pogacsa on my part !) My moms parents were from Buda-Pest as well, and went there too, of course. 

Doug

---

### Post by asipi on 2007-06-03
OFFTOPIC: very nice :D I am living in Dunaujvaros near the center of Hungary at the bank of the river Duna, nothing special only an industrial city though
/OFFTOPIC

to make a server read this link: [http://www.rtcw.jolt.co.uk/content/enemy_territory/server_guide/index.html]("http://www.rtcw.jolt.co.uk/content/enemy_territory/server_guide/index.html") 
not so difficult, some computer experinece need, but there are thousands of servers out there so I rather recommend to visit them, and get experience about how they are running before u decide to make one. We have a FunClan if you interested in, our homepage is [http://vwvclan.extra.hu/]("http://vwvclan.extra.hu/") it's dual language you can switch to english in the upper-right, and visit our gameserver, IP: 85.25.130.154:27960

Welcome on board! :)

---

