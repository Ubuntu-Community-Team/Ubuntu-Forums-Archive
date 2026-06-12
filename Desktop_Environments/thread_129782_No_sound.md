---
title: "No sound?"
date: 2006-02-14
forum: Desktop Environments
---

### Post by Nasty Dollars on 2006-02-14
I've installed Ubuntu (Breezy Badger) on my Acer Laptop. Everything works perfectly, but when i play music there's no sound coming from the speakers.
I opened the Sound-configuration menu and put all the leavers on max.
Still no sound. Can anyone help me?

Yours sincerely
Jeroen

---

### Post by Robgould on 2006-02-14
You need to go to turn the external amp on.  You do this from the same control panel where you found the leavers.  Look in options and add all the controls...then turn on external amp.  Should work for you then.

---

### Post by Nasty Dollars on 2006-02-15
Thanks. I tried turning on the Ext. Amplifyer but still no succes.

---

### Post by Robgould on 2006-02-15
Do you get sounds at logon?  Do you get any sound at all ever?
 
If not, try this.
 
From a terminal type:
 
```

sudo alsamixer

```
 
alsamixer will rin in the terminal window.  It is a program that looks a lot like your panel you were already using with the leavers.  This command will work without the sudo part but make sure you use it.
 
Look at everything there and make sure that nothing is muted, and the external amp is on.
 
try to play music while your doing all this.  Play with all the settings while you have music playing.  When you get it like you like close alsamixer.
 
now run the command
 
```

alsamixer

```
 
without the sudo. Make your settings here the same as they were the other way if they are not like that now.
 
Here is a post from another porum along the same lines.
 
[http://forums.fedoraforum.org/showthread.php?t=78239]("http://forums.fedoraforum.org/showthread.php?t=78239")
 
I hope this helps you.

---

### Post by Nasty Dollars on 2006-02-15
I'll try that one thanks. In the meanwhile i discovered my external sound card does work. Could this mean Ubuntu doesn't recognize my standard sound card?

---

### Post by jezjones on 2006-02-15
Although i really like Ubuntu, sound support is terrible.
There are loads of posts on these forums about it and very very few that are resolved.

To be fair, it is more likely the Alsa side of things that is the issue especially if you have a recent intel sound card in your laptop.

Despite all the posts to these forums, Dapper does not appear to be moving the alsa drivers forward to the latest versions. It is moving them to the next version but still a long way off the versions that are claimed to work.
If Dapper does not fix my sound problem then i'm ditching ubuntu as no sound is bullsh*t. 
Sound has been on computers for years and years and linux cant seem to get a decent grip on it. I am still using an old SB16 card in my desktop as i know there are drivers for it.

---

### Post by Nasty Dollars on 2006-02-15
So it's very likely that i'm not going to be able of fixing the sound problems.
I have indeed a very recent Intel Mobile sound card. :neutral:

---

### Post by jezjones on 2006-02-16
yes and no.

If you can get and install the latest ALSA drivers then you might get it to work.
I managed to get them from source forge but the install of them was complicated even for someone used to linux, so mine are still not working.

If you do have success then please post to say how.

Sadly this is likely to be the problem with any distro of linux you put on there. I tried a few to see if they worked, but without a working ALSA driver there is nothing the OS can do.

---

