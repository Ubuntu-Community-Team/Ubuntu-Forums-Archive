---
title: "Quake 4 linux installer out now"
date: 2005-10-20
forum: Gaming &amp; Leisure
---

### Post by rejser on 2005-10-20
The linux installer for Quake 4 is out

check out at
[http://www.linuxgames.com/](http://www.linuxgames.com/)

---

### Post by seethru on 2005-10-20
awesome news, just about to go pick this up

---

### Post by GameGod on 2005-10-20
Official link:
[ftp://ftp.idsoftware.com/idstuff/quake4/linux/]("ftp://ftp.idsoftware.com/idstuff/quake4/linux/")

---

### Post by rejser on 2005-10-20
Damn it, normally I don't care that I got a crappy computer, but with this release it really hurts

The official ftp is a bit crowded though, but they have torrent

---

### Post by seethru on 2005-10-20
well, gave this a run before going to work. Seems like ID still has the same problem with Alsa, sound is delayed. I'll try and fix this and post a HOWTO in this thread when I get home.

---

### Post by gil-galad on 2005-10-20
Very nice.  They released this fast.

---

### Post by arcanistherogue on 2005-10-20
dude, im copying the .pk4 files from my DVD as we speak :D

this is awesome.  Now to just mount my windows drive and copy over my saves i got ni the past two days, and im set.  I'm humbly surprised, I didn't expect this for another 2 weeks or so.

Id always cares for its linux fans :D

---

### Post by seethru on 2005-10-20
[QUOTE=arcanistherogue]dude, im copying the .pk4 files from my DVD as we speak :D

this is awesome.  Now to just mount my windows drive and copy over my saves i got ni the past two days, and im set.  I'm humbly surprised, I didn't expect this for another 2 weeks or so.

Id always cares for its linux fans :D[/QUOTE]
if only other companies would clue in on this...

I did some comparing of configs, and made some changes to my config from at work. I'll report whether it fixes the sound issue or not. Before leaving for work I tried changing the resolution and graphics settings to see if it would have an effect on the sound, but no luck, there was still a delay. Hopefully the changes I've made, like setting the correct device, will get sound working properly.

---

### Post by arcanistherogue on 2005-10-20
I use OSS, and it fixes problems with both DIII and QIV.  

just run "+set s_device oss" after quake4 in the command line once, and then it will work every time you use it.

---

### Post by seethru on 2005-10-20
so you were hearing the delay also, and setting it to oss worked? I've changed it inside my config, so hopefully it's good to go when I get home, incase it isn't I've compiled a 2.6.13.2-nitro kernel to try.

---

### Post by arcanistherogue on 2005-10-20
Well, i didnt hear a delay, but i got horrible sound.  It was like scratchy and very loud, every noise.  so I set it to OSS and everything was fixed.  Although my right speaker on my headphones is a lot quieter, but that is just my crappy onboard audio.

---

### Post by seethru on 2005-10-20
well, I'll know in about 20 minutes :)

---

### Post by seethru on 2005-10-20
so, just gave it a try with the +set s_device oss, according to the terminal it's still using Alsa, and it left me some fairly eye opening errors.

```
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 112 out of 1024
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 672 out of 1024
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 592 out of 1024
snd_pcm_writei short write: 432 out of 1024
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 208 out of 1024
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 144 out of 1024
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 192 out of 1024
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 544 out of 1024
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
idAudioHardwareALSA::Write: 1024 frames overflowed and dropped
snd_pcm_writei short write: 912 out of 1024
```

Fun, I'll keep working away at this, and give the nitro kernel a shot and hope that fixes things.

---

### Post by professor_chaos on 2005-10-20
This is awesome news!

I'm going out and buying it tomorrow.

I would appreciate any reviews from those of you who have it running. Any problems besides sound issues?

---

### Post by seethru on 2005-10-20
I've solved my problem with a simple restart...for anyone who runs xcompmgr, it seems to effect Alsa and OpenGL, even when it's not running, so you will need to restart and not allow it to run at start up if you experience any sound delays.

I'll write up a review once I've actually played it, up until now it's just been fixing the sound. Now I'll get into the real fun, play testing the single and multi-player.

---

### Post by Nylith on 2005-10-20
[QUOTE=arcanistherogue]I use OSS, and it fixes problems with both DIII and QIV.  

just run "+set s_device oss" after quake4 in the command line once, and then it will work every time you use it.[/QUOTE]

I believe you mean "+set s_driver oss", not device.  I got this from the Doom III linux client faq:
[http://zerowing.idsoftware.com/linux/doom/FrontPage#head-8a3e830015ce79941f7f69f6d5323d0e52ab126f](http://zerowing.idsoftware.com/linux/doom/FrontPage#head-8a3e830015ce79941f7f69f6d5323d0e52ab126f)

This has solved my sound issues for the time being.

---

### Post by skoal on 2005-10-21
Quake 4??

Wow. I didn't know it was coming so soon.  I wanna t-shirt which says, "I Quake 4 Quake 4".  My fingers are already *trembling* as I whip out the 'ole rattlesnake skin wallet and scadoodle on up to BestBuy.  I'll cya online with my railgun aimbot joo 5uX0rZ! muhahaha...

Hail Flash Gordon Carmack! Long live Id! Death to Ming! err, Death to DirectX!

\\//_

---

### Post by owdeuk on 2005-10-21
Slightly off topic.....But speaking as a keen Ut'er can you now dodge in Q4?

---

### Post by nrgtek on 2005-10-21
wait, so is the quake 4 for linux released on GPL? Do you still need to purchase a copy?

---

### Post by skirkpatrick on 2005-10-21
You still need to purchase a copy.  What you download is the binary client, you still need all the resource files from the CD and the CD-key.

---

### Post by professor_chaos on 2005-10-21
same horrible sound as well.

"quake4 +set s_driver oss" fixed it.

Thanks guys

---

### Post by endy on 2005-10-21
[quote=professor_chaos]same horrible sound as well.

"quake4 +set s_driver oss" fixed it.

Thanks guys[/quote]

For those with an Audigy, or similar 5.1 compatible, card properly set up with ALSA:
```
quake4 +set s_alsa_pcm surround51 +set s_numberOfSpeakers 6
```

Should get 5.1 surround working nicely. This game is fun!

---

### Post by professor_chaos on 2005-10-22
my hands are all cramped from gripping the mouse and gamepad for the last 4 hours of playing. Quake 4 is intense!

---

### Post by Plumsaren on 2005-10-22
Works great here. The performance is acceptable even though I only have a slightly overclocked ati radeon 9600 pro. Does anyone know if there's "config-guide" floating around somewhere to speed up the fps further...?

---

### Post by Drakx on 2005-10-22
[QUOTE=professor_chaos]my hands are all cramped from gripping the mouse and gamepad for the last 4 hours of playing. Quake 4 is intense![/QUOTE]


ditto :)

---

### Post by BLiX on 2005-10-22
Can't play the game, what's the problem? :rolleyes: 

```

qtr@baka:~/quake4$ sh quake4
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

```

---

### Post by seethru on 2005-10-22
is SDL installed?

---

### Post by DJ_Max on 2005-10-22
[QUOTE=BLiX]Can't play the game, what's the problem? :rolleyes: 

```

qtr@baka:~/quake4$ sh quake4
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

```[/QUOTE]
SDL should already installed, but it looks like you need the development files.

---

### Post by dmn_clown on 2005-10-22
[QUOTE=DJ_Max]SDL should already installed, but it looks like you need the development files.[/QUOTE]

Not necessarily, if s/he is running the amd64 port s/he would receive that error even with the dev SDL packages installed.  Quake 4 needs the 32 bit SDL libs to play.  I don't believe these are currently available in ubuntu amd64, which limits Quake 4 to a 32 bit chroot on a 64bit ubuntu system.

---

### Post by mrf on 2005-10-22
I'm seeing the same msg on a 64 bit system. libSDL is installed.

---

### Post by Icaros on 2005-10-22
Still can't get sound to work.  At first it ran with scratchy/choppy sound, now there is no sound at all.  Tried following the "quake4 +set s_driver oss" technique, and can't get sound that way either.  (I have 2 sound devices, an OSS one and an ALSA one even though I only have one onboard sound device.  I have set the device to OSS, and set everything in Multimedia Systems Selector to OSS as well.)

```

-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother.
WARNING: ioctl SNDCTL_DSP_CHANNELS 6 failed: Cannot allocate memory
close sound device
WARNING: sound subsystem disabled
--------------------------------------

```

---

### Post by seethru on 2005-10-22
it's +set s_device oss

---

### Post by Icaros on 2005-10-22
[QUOTE=seethru]it's +set s_device oss[/QUOTE]

Didn't work.

EDIT: After reading the docs on doom3, I found a solution.  I noticed in the error there was something about chanels being set to 6, so I tried this line:

```

quake4 +set s_driver oss +set s_numberOfSpeakers 2

``` 

...and sound works now.

---

### Post by gil-galad on 2005-10-22
You need to turn off surround sound, it doesn't work in oss.

---

### Post by Icaros on 2005-10-22
Has anyone gotten saved games from windows to work?  I have given them all the proper permissions, and the game crashes after its loaded the save 100%.

---

### Post by dmn_clown on 2005-10-23
[QUOTE=mrf]I'm seeing the same msg on a 64 bit system. libSDL is installed.[/QUOTE]

The total re-write to use SDL is a pain... a smart move for portability, but a pain. The game does run in a 32 bit chroot with the libSDL packages installed, however.  Hopefully one of amd64 team will create a libSDL-ia32 package and we'll be able to play it without a chroot *hint-hint wink-wink nudge-nudge*

---

### Post by leech on 2005-10-23
[QUOTE=dmn_clown]The total re-write to use SDL is a pain... a smart move for portability, but a pain. The game does run in a 32 bit chroot with the libSDL packages installed, however.  Hopefully one of amd64 team will create a libSDL-ia32 package and we'll be able to play it without a chroot *hint-hint wink-wink nudge-nudge*[/QUOTE]

Couldn't you just download the ubuntu package for the libSDL i386 and extract it to the quake4 directory?  I know with Nwn, you could specify which sdl library you used, but I think that was within the actual start up script.

Leech

---

### Post by dmn_clown on 2005-10-23
[QUOTE=leech]Couldn't you just download the ubuntu package for the libSDL i386 and extract it to the quake4 directory?  I know with Nwn, you could specify which sdl library you used, but I think that was within the actual start up script.
[/QUOTE]

I think it is possible, yes, 

```
sudo dpkg -X libsdl1.2debian-alsa-*i386.deb /lib32 && sudo ldconfig
```

would accomplish that, but from a security stand point it would be better to add libSDL to the ia32-libs package.  That way if a security exploit is found in libSDL it would be fixed automatically (by the ubuntu security team) without any user intervention at the next apt-get update && apt-get upgrade.  Otherwise you have to remember to pay attention to all security alerts and download and install the security fix on your own, not as easy as it sounds.

---

### Post by arcanistherogue on 2005-10-24
[QUOTE=Icaros]Has anyone gotten saved games from windows to work?  I have given them all the proper permissions, and the game crashes after its loaded the save 100%.[/QUOTE]

My saves didnt work either.  I copied the whole folder over, and in the game they aren't loadable, and none of them have names.

Oh well, I have gotten farther then I was on windows playing through the campaign now.

---

### Post by rejser on 2005-10-26
Thanks for linux, got Quake 4 playable on a amd xp 2000, gf 440mx and 1gb ram.
Never thought it would be playable. But since all of the cpu are free (about 1 % is taken in idle) it runs, not on the best graphics ofcourse, but it runs

---

### Post by slux on 2005-10-26
[QUOTE=rejser]Thanks for linux, got Quake 4 playable on a amd xp 2000, gf 440mx and 1gb ram.
Never thought it would be playable. But since all of the cpu are free (about 1 % is taken in idle) it runs, not on the best graphics ofcourse, but it runs[/QUOTE]

Decent framerates even? Have you tried multiplayer? I have a comparable system with a 1.8GHz Duron & GF4 Ti4200 so I'm interested.

---

### Post by rejser on 2005-10-26
[QUOTE=slux]Decent framerates even? Have you tried multiplayer? I have a comparable system with a 1.8GHz Duron & GF4 Ti4200 so I'm interested.[/QUOTE]

Ok framerates, if there are many monsters on screen at the same time there is trouble. but not much, not so that I suddenly die without notice.

Nope, havn't tried net-play, I am a mean man so I decided that I wanted to try the game on my machine before I bought it, now I see it works so I am going to buy it. So when I get my copy I will get back to you

---

### Post by rejser on 2005-10-26
[QUOTE=slux]Decent framerates even? Have you tried multiplayer? I have a comparable system with a 1.8GHz Duron & GF4 Ti4200 so I'm interested.[/QUOTE]

Ok framerates, if there are many monsters on screen at the same time there is trouble. but not much, not so that I suddenly die without notice.

Nope, havn't tried net-play, I am a mean man so I decided that I wanted to try the game on my machine before I bought it, now I see it works so I am going to buy it. So when I get my copy I will get back to you

---

### Post by Khannie on 2005-10-26
Anyone compared the windows FPS with Linux FPS?

I have a 3700+ with a 6800GT, so I'd expect it to run nicely anyway, but I remember AA placing a terrible strain on my 6600GT under linux.

---

### Post by pmj on 2005-10-26
[QUOTE=slux]Decent framerates even? Have you tried multiplayer? I have a comparable system with a 1.8GHz Duron & GF4 Ti4200 so I'm interested.[/QUOTE]
I have an Athlon XP 2000+, 512MB RAM and a ti4200 128MB and the framerate I get ranges between good and, in complex areas with a bunch of enemies, nearly unplayable. It's mostly fine though since the game usually doesn't throw more than 2-3 enemies at you at the same time.

It's a great game, I'm really enjoying it.

---

### Post by h4ck on 2005-10-27
Anyone knows the cd key of Quake4 please help

tnx

---

### Post by Drakx on 2005-10-27
Yea, you should have it if you bought it! (just a thought :))

---

### Post by h4ck on 2005-10-27
nep, but i am wondering if did anyone buy it:D

---

### Post by seethru on 2005-10-27
I don't think anyone who legitmately bought it is gonna give their cd key out, the reason that person bought it is probably because they want to be able to play multiplayer, and not have their cdkey locked out because a bunch of other people found it on public forums.

ps, I bought it

---

### Post by Drakx on 2005-10-27
>  ps, I bought it 

As did i :)

---

### Post by koroumel on 2005-11-02
[QUOTE=endy]For those with an Audigy, or similar 5.1 compatible, card properly set up with ALSA:
```
quake4 +set s_alsa_pcm surround51 +set s_numberOfSpeakers 6
```

Should get 5.1 surround working nicely. This game is fun![/QUOTE]

Although I'm a gentoo user I'm in search of help in these forums too. I have surround working in my system (in DVD reproduction) but in Quake I can only get the sound of the front speakers mirrored in my rear. I already have the settings you mention above but no result. I'll be glad if you can help me :)

---

### Post by WitchCraft on 2009-01-11
> **h4ck said:**
> Anyone knows the cd key of Quake4 please help

tnx

[http://ubuntuforums.org/showthread.php?t=843922](http://ubuntuforums.org/showthread.php?t=843922)

---

