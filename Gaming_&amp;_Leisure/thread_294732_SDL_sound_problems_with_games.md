---
title: "SDL sound problems with games"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by billyfoxtrot on 2006-11-07
I'm having trouble with games that use SDL sound.  The two games in particular that I'm trying to get working are Quake 2 and Tenebrae (a Quake engine with updated graphics).  Both appear to use SDL for sound, and in both games the sound is what might be described as fuzzy or crackling.  I've played around with the configuration files in both games, but I haven't had any luck fixing either.

Does anyone know what might be the problem?  I know very little about SDL.

---

### Post by me1on on 2006-11-08
I have the same problem. One thing that fixes it is turning the in-game volume up to 100%, but some games don't have that option (it fixes the sound for Wesnoth :)). See if that helps. Note that I didn't have this problem for Dapper, just for Edgy, so if you're using Dapper my advice was probably useless.

---

### Post by play0r on 2006-11-19
i had the same problem with quake2, with a bit of thinking i figured out the issue.
edit .asoundrc in your home directory & add the following code.

```
pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}
```

---

### Post by xfile087 on 2006-11-28
> **play0r said:**
> i had the same problem with quake2, with a bit of thinking i figured out the issue.
edit .asoundrc in your home directory & add the following code.

```
pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}
```

You are amazing!!! I've tried other solutions and nothing worked. I've just tried yours and it worked perfectly!!!

---

### Post by billyfoxtrot on 2006-11-29
> **play0r said:**
> i had the same problem with quake2, with a bit of thinking i figured out the issue.
edit .asoundrc in your home directory & add the following code.

```
pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}
```

Thanks a lot, the fix works for me too!  It's odd that Edgy doesn't come with ALSA automatically configured like this -- it would've saved me a lot of time searching and tinkering with configuration files.

---

### Post by me1on on 2006-11-29
> **play0r said:**
> i had the same problem with quake2, with a bit of thinking i figured out the issue.
edit .asoundrc in your home directory & add the following code.

```
pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}
```

For some reason I don't have a .asoundrc file in my home directory. :( I'm using Kubuntu if that makes a difference.

---

### Post by Rinnan on 2006-12-13
If you don't have an .asoundrc, go ahead and create one (for example, in a shell, type "touch ~/.asoundrc", and hit return.  No quotes in the real thing!

Then go ahead and edit this empty file adding the lines mentioned.  It worked for me (Feisty Fawn Herd 1, but had this problem since Edgy).

---

### Post by Rounin on 2007-03-30
Wow! It worked! Thanks a lot!

I can only echo what was said earlier... It would be nice to see SDL and alsa working together out of the box. Though honestly, I can't really see why there should have to be a secret configuration option to disable unwanted crackling.

On a side note, it seems like what this code does is disable the software mixing that enables several programs to share the same audio channel? So the choice is between crackling or single-channel audio...

---

### Post by Pitel on 2007-04-06
I've the same problem, crackling sound in games. But your method doesn't work. Installing libsdl-esd or something like that helped, but the sound was lagged. And would just like to use alsa.

---

### Post by kc0eks on 2007-04-07
upon trying this sound in my games didnt work at all, and sound in general was worse. I have tried nearly everything I can find to fix this crackle sound and its not going well :(

---

### Post by Bokonon on 2008-02-10
I had to edit this to card 1 for my usb audio, but it works great now!  

Thanks mucho!!!

---

