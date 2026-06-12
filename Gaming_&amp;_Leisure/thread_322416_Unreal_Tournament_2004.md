---
title: "Unreal Tournament 2004"
date: 2006-12-20
forum: Gaming &amp; Leisure
---

### Post by gwayne on 2006-12-20
Anybody ever been able to play UT 2004 and listen to mp3s at the same time?  I have been doing some research on this and it looks like my sound card does not support hardware mixing, so I took some steps to enable hardware mixing by following this Howto:

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

I then created a .openalrc file with this in it:

```
(define devices '(alsa))
(define alsa-out-device "plug:dmix")

```

Which should theoretically point UT2004s openal sound to use alsa.  Unfortunately it does not seem to.

I can listen to 2 different mp3s using xine and amarok at the same time but not play UT2004 and listen to an mp3 using either program.  If I start amarok or xine and then launch UT2004 all I can hear is the mp3.

Both mp3 players are configured to use alsa, and I have tried ESD as well

Has anyone gotten both UT2004 and an mp3 going at the same time on Edgy?  If I buy a sound card that supports hardware mixing will this be a non-issue?

Thanks,
Greg

---

### Post by _simon_ on 2006-12-20
Just tried it and yes, I can play mp3's whilst also playing UT2004. I am however using Totem, but it shouldn't make any difference what player is used.

I can hear both the mp3 clearly and UT2004 sounds.

I use a Creative Labs Audigy 2 ZS Value.

---

### Post by gwayne on 2006-12-20
Hmm.. that sounds like a card that would do hardware mixing.  Maybe thats my best option.  Thanks for your reply.

Did you have to do any config to get this working or did it just work out of box?

---

### Post by Tuna-Fish on 2006-12-20
> **gwayne said:**
> Hmm.. that sounds like a card that would do hardware mixing.  Maybe thats my best option.  Thanks for your reply.

Did you have to do any config to get this working or did it just work out of box?

Note that UT2004 has an mp3 player integrated into itself, so if you just want to listen to music you can use it. I got no idea how it works though, I use exaile.

---

### Post by gwayne on 2006-12-20
haha awesome, I did not know that, if I can get that working that would definately do the trick, thanks. :-)

---

### Post by _simon_ on 2006-12-20
> **gwayne said:**
> Hmm.. that sounds like a card that would do hardware mixing.  Maybe thats my best option.  Thanks for your reply.

Did you have to do any config to get this working or did it just work out of box?

Just had to play with the levels in alsamixer.

I didn't realise UT2004 had a player either lol

---

### Post by handy on 2006-12-20
Also, if you want a soundcard that does hardware mixing that is well suported by Ubuntu & is cheaper than the Audig(ies) try the SBLive, you can get oem version with 5:1 sound in australia for under $20-.

From what I have read on the forums some people prefer the SBLive to the Audigy?

---

### Post by ekuliak on 2006-12-21
I have the Soundblaster Live! 24-bit soudcard, and it does not have hardware mixing.  I believe the older SB Live! card does though.

If you press f11 while playing UT2004 it brings up the music player window.

---

### Post by handy on 2006-12-21
> **ekuliak said:**
> I have the Soundblaster Live! 24-bit soudcard, and it does not have hardware mixing.  I believe the older SB Live! card does though.

If you press f11 while playing UT2004 it brings up the music player window.

Does it have the emu10k1 chip?

---

### Post by ekuliak on 2006-12-21
Nope, you can see details about it [here]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix")

scroll down to 
> Sound Blaster Live 24bit
Sound Blaster Live 7.1

---

### Post by handy on 2006-12-21
> **ekuliak said:**
> Nope, you can see details about it [here]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix")

scroll down to

Bummer!

Thanks for the informative link.

---

### Post by _simon_ on 2006-12-21
You can usually pick the Audigy 2 ZS value up cheap on ebay. It's how I got mine.

The only difference between the normal ZS and the ZS Value is a few extra ports on the back of the card.

---

### Post by gwayne on 2006-12-21
Ill look into those cards, thanks for all the info guys.

I cant get the UT2004 Music player to browse my system properly to create a playlist.  Buttons in the playlist editor just dont seem to work right.  Maybe I have a borked install.

---

