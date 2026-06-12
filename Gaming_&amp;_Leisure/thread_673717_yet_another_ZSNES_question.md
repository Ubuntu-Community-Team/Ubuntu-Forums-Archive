---
title: "yet another ZSNES question"
date: 2008-01-20
forum: Gaming &amp; Leisure
---

### Post by Aysah on 2008-01-20
so yeah I had issues regarding ZSNES showing me the black screen and flickering out and I resolved it by adjusting the resolution in the config file.  After poking around the net I realized it runs fine if I run it from the terminal and adding some sound options to it (i think thats what it is)

```
sudo zsnes -ad oss
```

the problem is that I have been doing that soo much to get the program started to play my games throughout the day that now the sound doesnt work... :(  ...I'm not sure how to fix it

---

### Post by kooldino on 2008-01-21
Does it work if you reboot?

---

### Post by erginemr on 2008-01-21
And do you mean that the sound of the game or the overall sound of the system doesn't work?

---

### Post by Aysah on 2008-01-21
well I did a reboot and the sound worked again but then after I exited the game and tested ONE more time it flickered black and wouldn't boot again unless I added the "-ad oss" suffix on it in the terminal..  The sound just doesnt work at all... it's weird

---

### Post by erginemr on 2008-01-21
Could you please tell us your computer specs?
- CPU
- Graphics Card
- Sound Card
- etc.

And there should be a file "zsnesl.cfg" in your "home -> .zsnes" folder.
```
gedit ~/your_name~/.zsnes/zsnesl.cfg
```

Could you please attach it here?

One more thing: Your ZSnes version, and from where you got it....

---

### Post by Aysah on 2008-01-21
Pentium D 3.4GHz
NVidia 8600GTS XFX Card
Onboard Audio
3GB Ram
SUS Striker Extreme LGA 775 NVIDIA nForce 680i SLI ATX

---

### Post by erginemr on 2008-01-21
Please check out my other questions. (I am also a ZSnes user, but am currently away from my home computer. Maybe I can help.)

---

### Post by erginemr on 2008-01-21
Anyhow, here are some hints that I can think of, for you to find the solution:

1) Make sure you are using the final version of ZSnes, namely ver.1.51. If you downloaded it from their 

web site, try the ubuntu repositories:

```
sudo aptitude install zsnes
```
There is also a ZSnes debian package at GetDeb:

[www.getdeb.net](www.getdeb.net)

2) There is a hidden directory under your home folder ".zsnes" that contains the config files for 

ZSnes. You may have messed up your config files, and a fresh start may do good. So, try replacing your 

"zsnesl.cfg" file with a newly created one by renaming it to something else:

```
sudo aptitude install zsnes
```

For a comparison, please find attached my config file.

3) You are using 
```
sudo zsnes -ad oss
```
to overcome the sound problem. But you are running it with root rights, which is not recommendable and may cause something with the sound system to go wrong afterwards.

4) Make sure that the 3D capabilities of your graphics card has been enabled by issuing:
```
glxinfo | grep rendering
```

If you are using Compiz, does disabling Compiz-Fusion (desktop effects) help?

---

### Post by erginemr on 2008-01-21
Carrying on from above...

5) For video flickering issue, I don't know if it has anything to do with ZSnes, but in the past, I had 

video flickering with movies in full screen, which I could eliminate by adding the following line to 

the general config file for the graphical desktop: /etc/X11/xorg.conf 
```
 Option   "XvmcUsesTextures" "True"
```
to the Section "Screen" in your xorg.conf file.

For more info on the symptoms of this behavior please refer to:
[http://ubuntuforums.org/showthread.php?t=624498](http://ubuntuforums.org/showthread.php?t=624498)

6) Some games running SDL sound system are problematic in this or that way. When I first installed ZSnes to my Ubuntu system, I was having intermittent crackles in the sound with a low overall performance in the emulation. The game was apparently using ALSA sound system with conspicuous problems. An exhaustive search on this issue brought me to adding a custom ALSA config file to my home folder. I lived happily ever after.

Please find attached the custom config file I have been using for ALSA. Try putting this to your home folder by first renaming it to ".asoundrc" thus rendering it invisible. Kindly check if this helps at all.

For more info on .asoundrc, please refer to:
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

---

### Post by Aysah on 2008-01-21
> **erginemr said:**
> Carrying on from above...

5) For video flickering issue, I don't know if it has anything to do with ZSnes, but in the past, I had 

video flickering with movies in full screen, which I could eliminate by adding the following line to 

the general config file for the graphical desktop: /etc/X11/xorg.conf 
```
 Option   "XvmcUsesTextures" "True"
```
to the Section "Screen" in your xorg.conf file.

For more info on the symptoms of this behavior please refer to:
[http://ubuntuforums.org/showthread.php?t=624498](http://ubuntuforums.org/showthread.php?t=624498)

(I will add it when I get back home.)

6) Some games running SDL sound system are problematic in this or that way. When I first installed ZSnes to my Ubuntu system, I was having intermittent crackles in the sound with a low overall performance in the emulation. The game was apparently using ALSA sound system with conspicuous problems. An exhaustive search on this issue brought me to adding a custom ALSA config file to my home folder. I lived happily ever after.

Please find attached the custom config file I have been using for ALSA. Try putting this to your home folder by first renaming it to ".asoundrc" thus rendering it invisible. Kindly check if this helps at all.

For more info on .asoundrc, please refer to:
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

wow the sound did it for me... and i must say it actually sounds better too compared to when I kind-of sort-of had it "working" before.  Thanks again for all your help man!!!   :)

---

### Post by erginemr on 2008-01-21
:guitar:

Take Care & Have Fun!

---

