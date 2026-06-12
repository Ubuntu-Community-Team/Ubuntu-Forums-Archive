---
title: "mp4 will not play after 10.04 install"
date: 2010-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gringexican on 2010-05-10
I have this same problem in both computers (one as an upgrade from 9.10 and the other is fresh install from burned .iso)

Neither box will play .mp4 video formats, but will play flv (standard music formats such as .mp3 and .wav seem unaffected).

I have already installed medibuntu repository (specifically got ffmpeg libavcodec-extra-52 libavcodec-unstripped-52) and the ubuntu-restricted-extras.  I also tried to make sure that totem had the proper gstreamer packages.

I have followed just about every path I can think of to fix this issue to no avail based on posts already in the forum and the advice listed on mediubuntu.

Anyone else experience this issue and found a viable workaround or fix?

---

### Post by eltonw on 2010-05-10
> **Gringexican said:**
> I have this same problem in both computers (one as an upgrade from 9.10 and the other is fresh install from burned .iso)

Neither box will play .mp4 video formats, but will play flv (standard music formats such as .mp3 and .wav seem unaffected).

I have already installed medibuntu repository (specifically got ffmpeg libavcodec-extra-52 libavcodec-unstripped-52) and the ubuntu-restricted-extras.  I also tried to make sure that totem had the proper gstreamer packages.

I have followed just about every path I can think of to fix this issue to no avail based on posts already in the forum and the advice listed on mediubuntu.

Anyone else experience this issue and found a viable workaround or fix?
**Movie Player** is the media player installed by default. It **does** play mp4 files. If you let Lucid install default apps it would be in your Sound and Video section. There are alternate players too. For alternate applications (such as Mplayer), do a search in either Synaptic or Ubuntu Software Center for "mp4".


HTH....

---

### Post by pabc on 2010-06-05
it does not play **all** mp4 files by default. any files taken on my SE C902 phone will not play back on 10.04s default player. I have to convert via pitivi or use VLC to see them

---

### Post by dentaro16 on 2010-06-18
install VLC?

---

### Post by SRTS on 2010-06-18
I have exactly the same problem.
In 9.10, all my mp4 files worked in gnome media player.
In 10.04, some of them don't anymore.
And "install vlc" isn't a solution, sorry. Does anyone know how to fix the broken gnome media player so it becomes as good as it was in old 9.10?

---

### Post by udude on 2010-07-13
Is there some way to provide information about the mp4 files which do not play? 
If there's a good way dump the header of the unsupported mp4 files, we can narrow down the options for the unsupported fmt and thus try to find out more about the missing codec. Ideas?

---

### Post by bobcollard on 2010-07-13
Try this Thread:
[http://ubuntuforums.org/showthread.php?t=230123](http://ubuntuforums.org/showthread.php?t=230123)

---

### Post by udude on 2010-07-15
> **bobcollard said:**
> Try this Thread:
[http://ubuntuforums.org/showthread.php?t=230123](http://ubuntuforums.org/showthread.php?t=230123)

Looks like this is a 2006 thread. Have you seen anything specific there which allows dumping the mp4 file's fmt/codec info?

---

### Post by bobcollard on 2010-07-15
> **udude said:**
> Looks like this is a 2006 thread. Have you seen anything specific there which allows dumping the mp4 file's fmt/codec info?
No, sorry.  Perhaps someone else could help with that?

---

### Post by LFS-Nr-3305 on 2010-11-08
apt-get install gecko-mediaplayer

Mediaplayer played my donwloaded .mp4 file, 
Totem Video-Player 2.30.2 did'nt. And Firefox automatically was able to play the same downloaded file since, which was not the case before.

---

### Post by no2498 on 2010-11-30
if you would like totem to play mp4's
install smplayer it loads a few more codes for mp4's
type smplayer in a terminal it tells you how to install it

---

### Post by Lektorvis on 2010-12-13
> **no2498 said:**
> if you would like totem to play mp4's
install smplayer it loads a few more codes for mp4's
type smplayer in a terminal it tells you how to install it

Almost solved my problem. 
Until restart this gave me picture and sound in both Totem- and VLC-player, but only sound in SM-player 
- Strange,- I have updated all codecs of relevance I can find, but VLC and Totem crashes without showing anything but a black scene in flash and then closes down. 
- I wounder if the problem is the screen driver, as Lucid don't give full support to the i855 chipset.

---

