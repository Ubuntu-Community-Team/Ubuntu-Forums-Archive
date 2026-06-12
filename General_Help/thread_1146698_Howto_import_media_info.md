---
title: "Howto import media info"
date: 2009-05-02
forum: General Help
---

### Post by Bearded-flower on 2009-05-02
This is a stupid question and the answers probably right in front of my eyes but anyway.
I just started using banshee media player and i cant figure out how to import media information

---

### Post by Bearded-flower on 2009-05-02
Bump?

---

### Post by Bearded-flower on 2009-05-03
Anything at all???

---

### Post by wsscott on 2009-05-03
To import music .......

1) Edit
     Preferences
       General
          Music Library (assign a directory)

2) Media
     Import Media
       Local Folder
         Import Media Source (select directory assigned above)

---

### Post by Bearded-flower on 2009-05-05
Uuum i want to find out how to import MEDIA INFORMATION.
NOT the songs

---

### Post by Bearded-flower on 2009-05-09
Bump?

---

### Post by Bearded-flower on 2009-05-10
Bump?!?

---

### Post by Ericyzfr1 on 2009-05-10
What do you mean by Media Information? Could you give an example? Thanks.

---

### Post by Bearded-flower on 2009-05-11
metadata, EG songe title, artist, album, ect

---

### Post by SedaliaSteve on 2009-06-14
I'll add a hearty bump. I just got a system up & running last night. I've tried Rhythymbox, Audacious and Banshee. Banshee plays the CD but none of them have access to artist info like Windows apps do.

Steve

---

### Post by Bearded-flower on 2009-06-14
God damnit sweet mother f****ing bump!!!!!!

---

### Post by SedaliaSteve on 2009-06-18
I've had my desktop running for a few days and I'm very slowly getting the hang of it.

I'm not sure why Banshee or Rhythymbox couldn't pull info. Neither could Audacious and it worked like crap. amarok set me off installing and configuring databases. Songbird is still not convinced I have a CD drive. syslog is your friend.

I then tried XBMC. Here's some installation instructions for 9.04. [http://ubuntumanual.org/posts/176/install-or-upgrade-to-all-new-xbmc-9-04-in-ubuntu-jaunty]("http://ubuntumanual.org/posts/176/install-or-upgrade-to-all-new-xbmc-9-04-in-ubuntu-jaunty")

It gradually started working. I don't especially like it. It tries to be all things so it does them all in a so-so way. I like music and something like winamp was great.

XBMC tends to screw up and not say why. I found I had to open a terminal and:
cd /home/[insert your user name here]/.xbmc/temp
tail -f xbmc.log

The errors were useful. It plays music fine, knows the artist and once I installed lame I imported MP3's. I'm not thrilled with mp3's and it can't create directories but it is getting there.

If you want to get info via command line abcde is great. Here's a link to show how to use it to import CD's as FLAC files: [http://ubuntuforums.org/showthread.php?t=1183333&highlight=abcde]("http://ubuntuforums.org/showthread.php?t=1183333&highlight=abcde")

I want my desktop to do several music functions. These don't have to be one app.

1. Easily import music CD's in FLAC format. I collect some taper friendly bands so I'm fond of FLAC. These would be imported with all the info.
2. Have a very friendly interface that I could run locally or through remote desktop. This would let me play these FLAC's through my home stereo. Friendly is important since non-geeks would be using it. It would have all the playlist and genre features of itunes and winamp.
3. A web type interface to let other computers in the house steam music. They'd be Ubuntu, Windows or Mac. (Could be same as 2.)
4. Easily import CD's or tracks from CD's into MP3 for portable MP3 players.

I'm probably asking way too much. Ubuntu is great but there are so many projects going on energy is dissipated. There's lots and lots of works in progress and not many masterpieces.

Steve

---

