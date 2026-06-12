---
title: "New to Ubuntu, need help installing mplayer..."
date: 2005-10-13
forum: Desktop Environments
---

### Post by SeanCallan on 2005-10-13
Hey guys, I've been learning about as fast as I can, I got my new HD to show up and reformatted and everything but theres 2 last things I need to do before I'm settled.

1) Fix my screen resolution (working on it)
2) Install MPlayer (or any other video player)

I've looked in Synaptic and Mplayer isn't there. Is there any chance you guys could point me in the general direction on how to install a player in 5.10? :)

Thanks!

---

### Post by KingBahamut on 2005-10-13
youll need to add the addition repositories in Synaptic, but once you do that, you should be able to search for and find mplayer, vlc(a better choice in my opinion), and xine.

---

### Post by SeanCallan on 2005-10-13
Hey fellow Georgian!

Where do I find these additional repos?

---

### Post by pitr on 2005-10-13
Uncomment the lines with universe/multiverse in /etc/apt/sources.list

To do that start gnome-terminal, Applications->Accessories->Terminal and type
"sudo nano /etc/apt/sources.list"

---

### Post by SeanCallan on 2005-10-13
edit:  NM it's still downloading, I got ahead of myself.

---

### Post by torf on 2005-12-11
I'm running into a problem as well.  After finding out Mplayer does't want to compile with gcc 4.0, I tried using apt-get. I uncommented everything in my sources.list, yet the mplayer package still could not even be found.   Could someone please let me know if this source.list does not look right? Thank you.
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by taurus on 2005-12-11
How about adding these three lines at the end of your /etc/apt/sources.list

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

Save it and run "sudo apt-get update" at the prompt.  Then, fireup synaptic and search for mplayer...

---

### Post by torf on 2005-12-11
Wow, quick response. :) Thanks, that did the trick.  The only thing that seems to be wrong is that wmv's are rediculously laggy.  I copied the the essential-codecs to /usr/lib/win32, perhaps the wrong place?

---

### Post by anil_robo on 2005-12-11
I've tried VLC media player, and I've found it to be the best media player for Ubuntu in terms of playback quality! Try installing VLC through the "add applications" menu. Search for VLC and install it!

By the way I could never get wmv playback right with any media player in Linux, except VLC! So go ahead! :)

---

### Post by torf on 2005-12-11
I had some great dvd and wmv playback back on 5.04 when I just compiled mplayer instead of using any package manager. At any rate, I really would like to try VLC, since all I see is praise.  Upon installing it, I still had issues with the wmv format.  I have sound but no video, or absolutely nothing.  I assume I need to install some codecs or do some further configuring... After checking google and some more of this forum, it seemed like all one should have to do is install VLC.  (At first I just used apt-get, so I figured I didn't install correctly.  After removing it, I tried using the add applications item, which ended up giving me the same results :???: ) Thanks for the help everyone, very much apprecitated.

---

### Post by torf on 2005-12-18
Since I wanted to compile an orinoco driver for kismet, I ended up getting gcc-3.4 anyway.  After that I was able to follow a guide I used here: [http://oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://oldskoolphreak.com/tfiles/hack/ubuntu.txt)
(It's dated, so you have to just get the newest versions and such). Mplayer works fine aside from some sound complaints that don't affect the quality, but some further configuration should fix that.  So if anyone *really* wants mplayer, I'd basically follow the above guide.

---

