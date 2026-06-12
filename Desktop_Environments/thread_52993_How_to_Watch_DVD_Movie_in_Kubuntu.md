---
title: "How to Watch DVD Movie in Kubuntu"
date: 2005-07-29
forum: Desktop Environments
---

### Post by retsel on 2005-07-29
How does one watch DVD movies from Ubuntu? None of the software that came with the distro seems to do it.

---

### Post by super on 2005-07-29
quick! look! over here!

[http://ubuntuguide.org/?#dvdplayback](http://ubuntuguide.org/?#dvdplayback)

and for some additional dvd players try mplayer, gxine, vlc, etc...

---

### Post by retsel on 2005-07-30
Thanks for the suggestion. I looked at the link, and it was no help to me. Surely something as common as playing a DVD can't be all that hard to do in a distro that's supposed to built for human beings. Plus, the stuff in that link is for Ubuntu, not Kubuntu, and I've had trouble every time I've tried using stuff that isn't Kubuntu specific.

---

### Post by bored2k on 2005-07-30
[QUOTE=retsel]Thanks for the suggestion. I looked at the link, and it was no help to me. Surely something as common as playing a DVD can't be all that hard to do in a distro that's supposed to built for human beings. Plus, the stuff in that link is for Ubuntu, not Kubuntu, and I've had trouble every time I've tried using stuff that isn't Kubuntu specific.[/QUOTE]
 Kubuntu uses the same repositories as Ubuntu. The tips and tricks are mostly the same. The fact that is Ubuntu is for human beings doesn't mean it has to break its 100%free and legal motto.

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
* DVD playback *et al**
3. sudo apt-get install libdvdcss2 w32codecs gstreamer0.8-plugins --force-yes -y
* Possible media players *
4. sudo apt-get install totem-xine mplayer-386 vlc-esd --force-yes -y

---

### Post by mojorising on 2005-07-30
Getting DVD video playback is a little tricky. 

The libdvdcss2 package bored2k referred to is vital. 

Once you have the codecs installed, you can insert a DVD, double-click on the DVD icon on your desktop to make sure it is mounted, then type sudo ln -sv /media/cdrom1 /dev/dvd at a command line, open kaffeine, click open DVD in the Kaffeine File menu. 

The DVD should then play. 

If that works OK, then refer to one of my threads at [http://www.ubuntuforums.org/showthread.php?p=267706#post267706](http://www.ubuntuforums.org/showthread.php?p=267706#post267706) (I had the same and other related problems), specifically, the post from timetunnel. There you will see how to have the DVD drive set correctly in fstab.

Hope that helps you get it going.


Mike

---

### Post by retsel on 2005-07-30
Thanks Bored2k and Mojorising! I'll try it out and see what happens.

---

### Post by retsel on 2005-07-30
Well... I have some progress to report.

I updated sources.list, and downloaded and installed libdvdcss2 and w32codecs.
I then made sure the dvd was mounted, and typed sudo ln -sv /media/cdrom1 /dev/dvd.
I then opened kaffeine, and clicked open dvd in the file menu.

It almost worked! I got the first few seconds of audio that I know are on the dvd, and the vidio tried to put something up, but it was just hash, and then it just sat there.

I'd appreciate any more guidance you may have - looks like we might be getting close.

---

### Post by Tolomir on 2005-07-30
[QUOTE=retsel]Well... I have some progress to report.

I updated sources.list, and downloaded and installed libdvdcss2 and w32codecs.
I then made sure the dvd was mounted, and typed sudo ln -sv /media/cdrom1 /dev/dvd.
I then opened kaffeine, and clicked open dvd in the file menu.

It almost worked! I got the first few seconds of audio that I know are on the dvd, and the vidio tried to put something up, but it was just hash, and then it just sat there.

I'd appreciate any more guidance you may have - looks like we might be getting close.[/QUOTE]

Ok, I have checked that part.

My kaffeine version is using xine to play DVDs. There are some suggestion, if playback is jumpy and rather unusable.

Please check this website: [http://xinehq.de/index.php/faq#SPEEDUP](http://xinehq.de/index.php/faq#SPEEDUP)

Tolomir

---

### Post by retsel on 2005-07-31
I've tried all of the suggestions given so far, and the best I can get from a DVD movie is about 15 seconds of audio and essentially no video - just multicollored horizontal lines - video noise maybe. Any more thoughts on what might make it better?

---

### Post by coolclassic on 2005-07-31
Try installing xine using kynaptic and use this to watch dvd's.

---

