---
title: "esd startup help?"
date: 2005-04-04
forum: Desktop Environments
---

### Post by novamon on 2005-04-04
Ok, first of all, sorry if someone made this thread already... I did a quick quick search, and I'm really tired so I didn't find it... 

Ok basically, I have kubuntu up and running nice... but I want to use esound for my sound stuff (mixing etc..) just because it seems to work, and I can play more than one sound at once...anyway yea I just want to use esd..

Anyway, I've tried making up really really simple startup scripts for esd and putting stuff like
/usr/bin/esd -d /dev/dsp
in some scripts.. but nothing wants to load it up....maybe gdm turns it off or something when i go into KDE.. I donno, but if I want to use sound, when I first load up I need to start the daemon manually... by doing the command above.. and everything nice and works..

so.. where can I put a script/what script to load esd automagically?

I tried so far:
rc2.d .. with a really simple script that basically just runs the above command
startkde I think in /usr/bin/startkde or something
and actually one more, but I don't remember exactly, where it might a xorg thing....

thanks

EDIT: ok nevermind... esd doesn't work too well... if I start esd, I can play in xmms using the esound plugin for a bit.. but if I close xmms and play again, it doesn't work...I think actually it stops playing when esd returns to command prompt..

i.e. I run esd.. it says using device /dev/dsp.. then it's on a newline for a while... then it goes back to the bash thingy.. and after it goes back there I can't start new stuff... the esd stays on newline if stream is playing... =(

---

### Post by cwaldbieser on 2005-04-05
You are teh R0x0r!!!

Seriously, I have been pulling my hair out getting all my sound to work with esd.  I had been setting everything back to OSS where I could, because I didn't understand what the problem was.  But as soon as I saw you post:

> Anyway, I've tried making up really really simple startup scripts for esd and putting stuff like
/usr/bin/esd -d /dev/dsp

the lightbulb turned on!  I though esd just kinda went out and worked with *all* your sound cards, and then the application was responsible for picking the correct one somehow.  But when I saw your post, I realized I had to:

```
$ /usr/bin/esd -d /dev/dsp1
```

because I have 2 sound cards (1 built-in and another that actually works with Linux).

Everything just suddenly started working right after that, though I did have to Google around to find out how to get SDL to choose the second card as well:

```
export AUDIODEV=/dev/dsp1
```

Anyway, thanks for your help!

---

