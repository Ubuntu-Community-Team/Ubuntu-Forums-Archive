---
title: "Eat the Whistle"
date: 2006-04-22
forum: Gaming &amp; Leisure
---

### Post by katu on 2006-04-22
Has anyone got it running under breezy? 

I tried the binary and the debian packages I found. both exit with:

```
Initializing audio channels...
Unable to open audio: There are 0 joysticks available
Entering loop...
Freeing a GfxObj.
FreeGfxObj - width: 320
Program exited cleanly!

```

I also tried compiling from source, but I just get lots of errors.

I can't find the documentationfor sound. Any suggestions?

---

### Post by GameGod on 2006-04-22
Hmmm, I had it running under Breezy, and I'm not sure what I did...

Try killing esd first maybe?
("killall esd" from a terminal)

---

### Post by katu on 2006-04-22
I don't have esd running. I'm on kubuntu. I basically have all my sound on alsa. 
Did you use the binaries or compile?

---

### Post by katu on 2006-04-26
bump. This forum is like quicksand ;->. 
Really nobody got this thing to work? I found it on the list of games that work...

---

### Post by GameGod on 2006-04-26
It turns out I have the game still laying around on my drive, so I tried running it and it still works fine in Dapper.
I'm using the binaries.

When I run the game, my relevant sound output looks likeP

> Sound system initialization...
Initializing audio channels...
AUDIO: Asking for 22050/8/512/1, obtained 22050/8/512/1


I'm pretty sure that won't help very much though...

(So Kubuntu doesn't use ARTS?)

---

### Post by katu on 2006-04-27
I don't use arts, cause my soundcard on the laptop is only capable of one audio stream at a time, and so far alsa seems to work best wtih mixing. I'll try with arts on, when I get home in the evening. thanks.

---

### Post by katu on 2006-04-27
started working. didn't take into account my sound card. it seems that I can't have anything else running which might even try to touch the sound. Stupid me. Thanks for the suggestions. they did lead me to the right track. ;-)

---

