---
title: "Another Sound Issue Thread"
date: 2006-01-02
forum: General Help
---

### Post by TheIdiotThatIsMe on 2006-01-02
I have read through many threads dealing with users having sounds issues in games, and have yet to be able receive sound in some games.

I currently have a SoundBlaster Live! 24-Bit soundcard. Under Multimedia System Selector I have OSS for both input and output, if I choose anything else I lose all my sound. I've read that my card should support ALSA, but when I try to choose ALSA and click test (on either input or output) I receive the error: Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'. 

I get sound from my music programs and some games, such as Quake IV's demo. However, I do not currently get sound from Enemy Territory and LinCity-NG.

For LinCity-NG I get the following terminal output: 

```
Starting lincity-ng (version 1.0.1)...
[/home/anthony/.lincity] is in the search path.
[/home/anthony/.local/share/lincity-ng] is in the search path.
LINCITY_HOME: /home/anthony/.local/share/lincity-ng
open /dev/sequencer: No such file or directory
OpenGL Mode 1024x768
ERROR of degree -1:Error. Can't find LINCITY_HOME
anthony@ubuntu:~$
```

If I do a sudo modprobe snd-seq I get sound. Is there anyone to get around this or load the module on startup?

For Enemy Territory, I get the following error on sound in the terminal output:

```

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
```

I dont really know what that means :confused: But I know I've seen it and still cant figure out how to fix it.

---

### Post by yaztromo on 2006-01-02
I don't really understand what the heart of the problem is, but I do notice you have no /dev/dsp. I didn't have one either and this worked for me.

Open a console and type:
cd /dev
sudo ./MAKEDEV audio

For me this got sound working in firefox flash and various games.

---

### Post by TheIdiotThatIsMe on 2006-01-12
[QUOTE=yaztromo]I don't really understand what the heart of the problem is, but I do notice you have no /dev/dsp. I didn't have one either and this worked for me.

Open a console and type:
cd /dev
sudo ./MAKEDEV audio

For me this got sound working in firefox flash and various games.[/QUOTE]

Unfortunately no success :???:

---

### Post by TheIdiotThatIsMe on 2006-01-19
Sorry to bump, I've been trying to get my sound working correctly for a long time so I can do more gaming in Ubuntu :-k

---

### Post by eMuNiX on 2006-01-28
Thanks MAKEDEV worked a treat here too, can't figure out why sound was working and then suddenly didn't though.  Anyway EnemyTerritory and UT2004 have sound :)

---

### Post by eMuNiX on 2006-02-12
Further to my last post I now notice that when I restart the machine it always loses /dev/dsp.  It creates it again easily with sudo ./MAKEDEV audio but how do I get it to keep /dev/dsp?

---

### Post by Cathbard on 2006-02-12
This is starting to sound like a udev problem to me (not that I'm an expert). Should we write a udev rule for it? Shouldn't that already be there?
This fault happened after an update launched off the little red button (that's dist-upgrade isn't it?) I have been using breezy since an rc release of it and this is new. I've installed breezy on this pc about 4 times because I like to experiment and this problem with no /dev/dsp is new.

*waiting patiently for the guru's to do their thing*

---

### Post by nanotube on 2006-02-13
hmm, dont know if this will help, but try giving this a read:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Sound_problems](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Sound_problems)

---

### Post by Cathbard on 2006-02-13
It might help if my etc/modprobe.d/sound file was actually there I guess.
Where it went is a bit of a mystery but once I inserted another my /dev/dsp came back..........oops, how embarrasment.:oops:

Edit: /etc/modprobe.d/sound is usually created by alsaconf during the install process on other distros. Ubuntu's alsa doesn't have alsaconf at all so you can't even run it afterwards. Is there a good reason that Ubuntu has an apparently stripped down alsa-utils? I'm sure if alsaconf was there we wouldn't be seeing so many posts about disfunctional alsa imho.

---

### Post by TheIdiotThatIsMe on 2006-02-16
[QUOTE=Cathbard]It might help if my etc/modprobe.d/sound file was actually there I guess.
Where it went is a bit of a mystery but once I inserted another my /dev/dsp came back..........oops, how embarrasment.:oops:[/QUOTE]

How do you insert another one?

---

### Post by TheIdiotThatIsMe on 2006-02-17
Would someone be kind enough to show me all of what's in their modprobe.d folder? I think I'm missing a few things maybe? I created a blank sound file but that didn't work, and I am unsure of what to do.

---

### Post by TheIdiotThatIsMe on 2006-02-17
*ignore post*

---

### Post by Cathbard on 2006-02-21
Sorry about the lateness of my reply.
The simplest thing you can do is:```
sudo gedit /etc/modprobe.d/sound
``` and insert something like:```
alias snd-card-0 snd-emu10k1
options snd-emu10k1 index=0
```
just replace emu10k1 (that's for sounblasters) with whatever driver you are using with your card. This is the type of file alsaconf would create. It's very basic but should get you out of trouble.
You may also want to take a look at this thread. It has a fair bit of info on setting up sound.
[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds)

PS The IdiotThatisMe: I know you said to ignore your post but other ppl may need to know this also it seems.

---

### Post by TheIdiotThatIsMe on 2006-02-22
[QUOTE=Cathbard]Sorry about the lateness of my reply.
The simplest thing you can do is:```
sudo gedit /etc/modprobe.d/sound
``` and insert something like:```
alias snd-card-0 snd-emu10k1
options snd-emu10k1 index=0
```
just replace emu10k1 (that's for sounblasters) with whatever driver you are using with your card. This is the type of file alsaconf would create. It's very basic but should get you out of trouble.
You may also want to take a look at this thread. It has a fair bit of info on setting up sound.
[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds)

PS The IdiotThatisMe: I know you said to ignore your post but other ppl may need to know this also it seems.[/QUOTE]

That ignore post was because I accidentally double posted and couldn't figure out how to delete it :confused:

---

