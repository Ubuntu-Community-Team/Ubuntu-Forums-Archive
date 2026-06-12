---
title: "No DVD Sound"
date: 2009-05-09
forum: General Help
---

### Post by tractor on 2009-05-09
Hi,

I have Ubuntu 9.04 on two machines here at the office. One was a fresh install. One was an upgrade from 8.10. The media players in both machines will all play video clips and u-tube videos with sound. But, if I put a video DVD into either the DVD Rom or the DVD burner in either machine, the video will play, but I have no sound. Otherwise the sound works fine.

Thank you for any help you can give.

---

### Post by albinootje on 2009-05-09
> **tractor said:**
> But, if I put a video DVD into either the DVD Rom or the DVD burner in either machine, the video will play, but I have no sound.

Is it possible that the drives are not connected to the sound card inside the machine ? 
And did you check the mixer settings ?

---

### Post by fooman on 2009-05-09
*right*-click on the speaker/volume icon in the top panel....choose "open volume control"

check that all the sliders are turned up and not muted.

---

### Post by tractor on 2009-05-09
Yes, I had checked all of that before posting. I even uninstalled and reinstalled all of the players. The sound is only missing on playbeack of DVD videos. Otherwise I have sound for everything else.

---

### Post by fooman on 2009-05-09
try installing the gnome-alsamixer....it has quite a few more sliders & options then the default alsamixer.

open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install gnome-alsamixer
```after it installs,  open it in applications > sound & video

see if anything there is muted (CD ?).

---

### Post by tractor on 2009-05-09
Hi,

I just installed the gnome-alsamixer here at home on my home computer with Jaunty on. I had done that on one at the office today. My home computer also will not play audio in DVD's, but the sound on everything else works, including DivX video clips. I made sure nothing was muted in gnome-alsamixer. I also downloaded some additional codecs from Medibuntu and installed them, as well as trying the RealPlayer (Helix) from Medibuntu. Real player says it cannot open this format. Since I have three computers all doing the same thing, this must be a bug.

---

### Post by crazypeppo on 2009-05-09
I had a similar problem and this was suggested to me:

"On a side note you might be better to use a newer copy of MPlayer and I would suggest using the one generously provided by rvm from his PPA:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

and also install SMPlayer from the repository to get a decent gui."

I was not getting sound in Totem and not getting video in Mplayer...
Just a shot but you can see if that works.

---

### Post by tractor on 2009-05-12
Hi,

Thank you for your post. I am a Realtor and a farmer, so sometimes it takes me a little while to test things out more. I did try your suggestion. It didn't make any difference on my problem. But here is additional information:

1. I have tried the things suggested here.
2. I am a realtor and make DVD video tours of the properties I sell. These include narration and background music.
3. I have installed Ubuntu on 8 computers since I started with linux and Ubuntu about 2 months ago.
4. I have discovered that the more recent DVD's I've made will play back fine in Ubuntu and have the voice and background music. I've tried this on 4 different Ubuntuboxes with the same results in all 4 of them. Older DVD's have no sound in Ubuntu, even though the play fine on Windows Vista and XP boxes and also a range of older and newer DVD players connected to TV's.
5. I'm presently using Corel's (formerly ULead) Video Studio 11 Plus. Prior to that I had version 10, and prior to that version 9. Prior to that Pinnacle Studio 9, 8, and 7.
6. It appears that there is something in the way the DVD's are formatted with respect to sound which causes some of them to be read in Ubuntu or possibly Linux as a whole, but not all of them. 
7. It would be nice if they all would work!

I very much appreciate the time you've taken to assist me.

---

