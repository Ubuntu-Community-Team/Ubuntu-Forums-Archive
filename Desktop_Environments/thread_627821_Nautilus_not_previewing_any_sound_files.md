---
title: "Nautilus not previewing any sound files"
date: 2007-11-30
forum: Desktop Environments
---

### Post by Islington on 2007-11-30
When I used to hold my mouse over a sound file it used to play a preview. Now it doesn't. in nautilus preferences I have the option for sound files set for "always". 

Please help.:)

possible help stuff:
[http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/](http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/)             ::did not work for me::

To summarize from [http://ubuntuforums.org/showthread.php?p=3668053:](http://ubuntuforums.org/showthread.php?p=3668053:)

You need "esound" for generell preview capability in Nautilus.

"mpg123-esd" or "mpg321" for mp3 support (although the first has less cpu-usage)

"vorbis-tools" for ogg vorbis support

"sox" for wav support (aiff, voc, snd, au, gsm should also work, but i didn't test them)

---

### Post by markp1989 on 2007-11-30
i never knew that feature existed, i enabled it on my computer and it doesnt work.

---

### Post by rainwalker on 2007-11-30
I have the same problem, worked on Feisty, Edgy, and Dapper, but not Gutsy.

---

### Post by Fingers &amp; Thumbs on 2007-11-30
Yeah! what a neat feature, although since meticulously going through my files to make sure they're all correctly labelled I haven't spent much time in my media folder, I just access through my media player. 
   I went to the folder to try to find out what the program is that incrporates itself into nautilus to acheive this, in order to answer this thread, but lo and behold, I'm having the same problem, the icon appears over the file as if it should be playing, but no sound.
   Hmmmmm!

---

### Post by Islington on 2007-12-01
bump this thread for possible solutions!

---

### Post by infra_red_dude on 2007-12-01
Haf the exact problem here! So, any solutions?

---

### Post by Islington on 2007-12-01
noone seems to know. :( keep bumping the thread, so some person who knows can enlighten us

---

### Post by Islington on 2007-12-01
so possible addition to problem :[http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/](http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/)

mpg321 and vobis tools installed and still doesnt help.

---

### Post by cosmofed on 2007-12-01
Another data point for this problem:
    No effect on installing mp321. I think I have all the necessary mp3 codecs installed. I can rip from a CD and save them. Music players such as Rhythmbox can play the mp3 files. However, when using Nautilus to view the mp3 file, the browser will freeze up and a "forced quite" is required to close the browser. I'm running the 64-bit version of Gutsy and I am about 95% converted to kissing Windows goodby. Since I can see mp3 files in other installed applications, it appears to be specific to Nautilus2.20.0. 
    Any help is will be greatly appreciated.

---

### Post by Islington on 2007-12-01
After reading though bug-report comments. this is how I got it to work.

install packages 
mpg321
vorbis-tools
pulseaudio
pulse audio esound

now previews are working for me.

Reference threads:

[https://bugs.launchpad.net/ubuntu/+source/mpg321/+bug/125739](https://bugs.launchpad.net/ubuntu/+source/mpg321/+bug/125739)
[http://ubuntuforums.org/showthread.php?p=3668053](http://ubuntuforums.org/showthread.php?p=3668053)

---

### Post by infra_red_dude on 2007-12-02
Hey thanks :) It works for me too now!

---

### Post by cosmofed on 2007-12-02
**This solution did not work for me.** Matter of fact if crashed my system. (After log-on, the screen just became a single color.It wasn't crashed because I could "ctrl-alt-backspace"and logon again; but only to the same result.

Fortunately I was able to uninstall mpg321,vorbis-tools,pulseaudio and pulse audio escound and restored my system. 

Any other ideas from the community?

I'd really hate to have to maintain a Microsoft license just to get files onto my Sansa e260 player.

---

### Post by cosmofed on 2007-12-05
Apparently this is definitely related to Nautilus. Use the Thunar file manager instead if you want to be able to view and move .MP3 files.

---

