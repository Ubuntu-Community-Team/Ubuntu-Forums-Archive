---
title: "Return To Castle Wolfenstein - no sound"
date: 2007-06-11
forum: Gaming &amp; Leisure
---

### Post by Merritt.kr on 2007-06-11
I get this error in console:

/dev/dsp: Input/output error
Could not mmap /dev/dsp

and I can get no sound at all. I have tried all the sound fixes on this page:

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

as well as a few more from google searches. No luck, no sound.
Any ideas?
Running Kubuntu Feisty Fawn.

---

### Post by Merritt.kr on 2007-06-12
bump

---

### Post by viciouslime on 2007-06-12
There's also this: [http://www.nixcoders.org/forum/index.php?showtopic=609]("http://www.nixcoders.org/forum/index.php?showtopic=609")

---

### Post by Merritt.kr on 2007-06-13
That link is for enemy territory, and seems to link to files specifically for ET. I'm trying to run the original Return to Castle Wolfenstein, not the multiplayer expansion...

---

### Post by Merritt.kr on 2007-06-14
No one else have an idea for getting Return to Castle Wolfenstein working with sound? The opening cinematic looks really nice, I wish I could hear it! :)

---

### Post by reset3x on 2007-06-15
I found this.... Maybe it will help you....

[https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfenstein](https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfenstein)

---

### Post by Merritt.kr on 2007-06-15
Thanks, I tried that but still no sound unfortunately. I'm actually starting to think of trying to run the game's Windows version under Wine... sad, since it is supposed to actually work under Linux. :(

---

### Post by reset3x on 2007-06-15
It's strange... Works fine on my laptop which has a cheesy ac97 codec....  and works fine on my machines that have sound blasters.... My main rig has nVidia and it doesn't work there.... I had an X-fi in it but thats another story..... 

I believe your Dell has an Audigy right?

---

### Post by Merritt.kr on 2007-06-15
I believe so, yes. I think it's this:

Sound Blaster® Audigy™ HD Software Edition

I checked off the Dell website. I put my order receipt in storage with the box, and my memory sucks, so yeah.. :)
I was actually wondering if perhapse they were the reason it wasn't working, but on the same page EVERYTHING else works... linux, video, other games, amarok, etc... so I don't know.

---

### Post by Merritt.kr on 2007-06-16
Alright, I tried installing the game through WINE. Install went fine, it opens fine, graphics are fine.... no sound whatsoever. It has to be a problem with the program. I don't get it.

---

### Post by reset3x on 2007-06-16
Wine version 0.9.39 was released yesterday... The WineHQ Website [http://www.winehq.org/](http://www.winehq.org/) says that there are improvements for sound support..... I'm gonna give this a whack and see what happens.... Keeping in mind that it's not from the Ubuntu repositories and thus may not be stable.... I'll let you know if I have any luck with it.....

---

### Post by reset3x on 2007-06-16
Well, I added the winehq rep to my sources list and ended up with 0.9.38.... I didn't read the webpage thoroughly (duh!!) and found later that 0.9.39 just comes as source at this time and will be added to the repositiories later.... I did manage to get sound in RTCW by configuring wine to use ALSA... But there is an annoying lag.... I tried OSS too but then had no sound at all..... Maybe check your wineconfig and see that you're using ALSA???

---

### Post by Merritt.kr on 2007-06-16
Alright... made sure ALSA was working, and set hardware acceleration to Full. I added this as the command:

wine WolfSP.exe +set s_driver ALSA

And omg, I have sound. Unfortunately it has quite a bit of static coming through, kind of painful.. but at least this is a step in the right direction.

I'm still disappointed I had to use a windows install of an id game!

---

### Post by Fuzzypiggy on 2007-06-17
I had exact;y the same problem on 7.04 running on my HP Pavillion w5261 ( whatever stuff is in the box, I think it's a RealTek High Def Audio!)  but I found a workround!

The lead offs to the Ubuntu guide to get this installed state that you need to redirect two binaries to OSS :

        echo 'wolf.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
        echo 'wolfsp.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss

It seems though that when you start the game with wolf.x86, this only loads the main menu, it then chains off to wolfsp.x86 ( SIngle player) or wolfmp.x86 ( Multiplayer) , whichever you select. 

Now if you run the line: 
        echo 'wolfsp.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
The start the game with :
        /usr/local/games/wolfenstein/wolfsp.x86

The sound comes through fine on the video and in the game! I can only assume that when you fire up wolf.x86 it doesn't "handover " the OSS to the chained wolfsp.x86 or wolfmp.x86.

Hope this helps someone! :)

---

### Post by LordBanter on 2009-05-14
Hi,

I was going nuts with this Wolfenstein Enemy Territory sound issue. I have installed the game, but the sound was not working at all. I have tried almost all available solutions from the Internet. None worked. However I have managed to make one solution work properly for me and voila! I HAVE SOUND & MUSIC NOW! )) Read on how I made it:

1. I have downloaded this script: [http://nullkey.ath.cx/~stuff/et-sd]("http://nullkey.ath.cx/%7Estuff/et-sd") [...] -sound.gz. (Alternative mirror: [http://members.lycos.co.uk/lordban](http://members.lycos.co.uk/lordban) [...] l-sound.gz )
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
Brand new advanced Amiga compatible! Visit [www.natami.net]("http://www.natami.net")
---------------------------------------------------------------------------------

---

### Post by Dave_Jackson on 2009-07-28
Fuzzy was kind of on the right track, but his solution as stated did not work for me on 64 bit Ubuntu Jaunty (It's 2009 now :D). What I had to do to get sound working in RTCW was (in exact, command by command sequence):

> 
In the terminal, change to the directory containing the installation. In my case, cd /usr/local/games/wolfenstein.

sudo -i
echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "wolfsp.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit

If you're trying to get sound in Enemy Territory working, just substitute et.x86 within the quotes in the above lines, leaving the rest unchanged.
The same goes for the wolfmp multiplayer binary. 

If you leave out sudo -i, you will get a permissions error. 

I got those steps from the "Method 2" of the "Sound Issues" section of a
guide for Enemy Territory, a similar game. That was all I had to do. I didn't need to set up any scripts or anything like that. 

Of course, if this alone doesn't work for you, feel free to try the other suggestions in that guide. Here is the link: 

[https://help.ubuntu.com/community/EnemyTerritory#Sound%20Issues](https://help.ubuntu.com/community/EnemyTerritory#Sound%20Issues)

Hopefully I was able to help someone enjoy this great game on Linux.

---

### Post by mullens101 on 2009-11-13
I know this is an old thread but this could help others running newer (Karmic x86_64) versions of Ubuntu.

Fixing RTCW sound in Ubuntu Karmic x86_64, without et-sdl-sound.so

I had been trying to use et-sdl-sound.so with RTCW on Karmic.  I could get some really crackly sound using the et-sdl-sound.so hack and SDL_AUDIODRIVER set to "alsa" in the initialization script, but A: the sound was horrible and B: the game completely hung on exit (in et-sdl-sound.so, the calls to __SDL_CloseAudio would lock the game).

After a bunch of research, trying to hack and re-compile and failing, I finally have sound working well.  Here are the steps I used.

1.  Create a larncher script that has the following (The big difference here from the et-sdl-sound.so hack is the LD_PRELOAD line ... don't use et-sdl-sound.so, instead use "/usr/lib32r/libpulsedsp.so"):

export ETSDL_SDL_LIB="/usr/lib32/libSDL-1.2.so"
export SDL_AUDIODRIVER="alsa"
export LD_PRELOAD="${LD_PRELOAD}:/usr/lib32r/libpulsedsp.so"
cd /usr/local/games/wolfenstein
wolfsp.x86 $*

2.  Save this file to whatever name you want (runwolf? startwolf? whatever...) and make it executable.

3.  su to root (for some reason the following command doesn't work with sudo, you get permission denied)

4.  As root, execute 'echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'

5.  Exit root and as your normal user, execute the script created above, the game should start, have smooth sound, and not hang on exit.

---

### Post by RawShark on 2009-11-24
My solution on Ubuntu 8.04 LTS is to modify the wolfsp launcher script like so:

```
#!/bin/sh

cd "/usr/local/games/wolfenstein/"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
echo "wolfsp.x86 0 0 direct" | sudo tee /proc/asound/card0/pcm0p/oss
exec ./wolfsp.x86 $*
exit 0
```

This assumes sudo is set up to run [without needing a password]("http://ubuntuforums.org/showthread.php?t=19236").

I can now just launch RTCW will "wolfsp" by command line, desktop launcher, whatever.....

---

