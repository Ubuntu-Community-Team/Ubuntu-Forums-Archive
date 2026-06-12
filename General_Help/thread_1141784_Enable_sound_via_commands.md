---
title: "Enable sound via commands"
date: 2009-04-28
forum: General Help
---

### Post by Monotoko on 2009-04-28
Hiya fellow ubuntu users :)

I was just on MSN, and the other night i slept through when my girlfriend came online, so last night i left the sound on, only problem was, others tried to talk to me and it woke me up, had to shutoff the sound in the end.

Now i have found aMSN has a feature to activate a script when someone signs in, i was wondering if it would be possible, to create a bash script to do the following: keep my volume off, but when my girlfriend logs in, unmute the sound and play a song?

Thanks in advance :)

---

### Post by Monotoko on 2009-04-28
Anyone?

---

### Post by zeex on 2009-04-28
> **Monotoko said:**
> Anyone?

Interesting situation :). I'll look into it. Are you using Pidgin for MSN ??

---

### Post by soskito on 2009-04-28
why dont you look up to make a pidgin script? maybe you can disable sound from pidgin for anyone who isnt your girlfriend instead

---

### Post by Monotoko on 2009-04-29
I'm using aMSN, it will allow me to run a bash script when someone signs in, so i was thinking about making it run a bash script to enable my sound when my girlfriend signs in?

---

### Post by kpkeerthi on 2009-04-29
**To mute:**
    amixer set Master mute 

**To unmute and set volume to 100%:**
    amixer set Master unmute 
    amixer set Master 100% 

For more info, refer to [man page]("http://linux.die.net/man/1/amixer")


**To play a file:**
    aplay /path/to/file.mp3

[aplay man page]("http://linux.die.net/man/1/aplay")

---

### Post by Monotoko on 2009-04-29
Ahhh thank you very much :)

I have created myself a script :D

---

