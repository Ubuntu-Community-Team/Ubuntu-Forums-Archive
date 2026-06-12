---
title: "Can ubuntu play DVD's?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by snoochems on 2005-08-09
Hi all.

I threw in a DVD movie into the dvd drive, and totum starts playing some random peice of video (one of the special feature on the dvd)

I tried to get it to just play the DVD from the start, but either i don't know how, or it can't be done.

Oh, and 'pulp fiction' came up as a desktop short cut too. (yes, i was trying to watch pulp fiction)

So, i look around, do some searching, and found a that 'Mplayer' was suppose to be the 'ultimate media player'.

So i jump into the Synaptic Package manager, and find Mplayer 586.  I install it.

i then go and find a guide to installing DVD playback ([http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback))

So, i thought i was all set... but i was wrong.  Mplayer just freezes up when trying to open the dvd.

I tried reseting, and also installed all the other codecs found in that ubuntuguide.org place.

What do i do now?  Oh, and i can' even eject the DVD now.  WTF?  Is it gone for good?  Even if i can't get ubuntu to play DVD movies, i at least want my DVD back!

---

### Post by manobes on 2005-08-09
[QUOTE=snoochems]Hi all.
What do i do now? [/QUOTE]

Mplay is pretty good for playing all other sorts of video.  But for DVDs I'd recommend ogle.  You'll need the dvdcss library as well, which you can get from the hoary-extras or marrilat repositories.  

[http://ubuntuforums.org/showthread.php?t=9810&highlight=ogle](http://ubuntuforums.org/showthread.php?t=9810&highlight=ogle) should help.  You might also check out the user guide [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by kosmic on 2005-08-09
add the backports repostitories to apt...and then install libdvdcss and vlc :)

---

### Post by snoochems on 2005-08-09
vlc? 

Okay, the reason why i installed mplayer was because i understood it was the 'ultimate media player'

It's not exactly 'ultimate' if it doesn't play DVD's now!

So, is vlc capable of DVD's?

Should i unistall mPlayer?

BTW, what is the difference between mPlayer 386, 586, and 686?  (etc)

---

### Post by snoochems on 2005-08-09
Okay, I just installed ogle.

It played my dvd, but it's slow, chunky, and actually, i think it's frozen.

The first second or two were fine though

---

### Post by Hairy_Palms on 2005-08-09
it sounds like you need to enable dma on your dvd drive, but i cant remember how of f the top of my head, ill post how when i remember unless someone gets to it first

---

### Post by snoochems on 2005-08-10
well...?

---

### Post by bored2k on 2005-08-10
[QUOTE=snoochems]well...?[/QUOTE]
```
 sudo hdparm -d1 /dev/dvd 
```(or your correct disc drive -- cat /etc/fstab to see what's yours; could be /dev/cdrom0 or any other).

---

### Post by Knome_fan on 2005-08-10
Installing totem-xine (it's an other backend for totem) and libdvdcss2 should help you out.

About enabling DMA:
[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

---

### Post by mcmuffy on 2005-08-10
Personally I prefer to use xine for DVD playback, if you have used powerDVD on windows you will be right at home.
But then I vote Labour so what do I know  \:D/

---

### Post by shakin on 2005-08-10
Xine will work and so will VLC. Pick one of those two and you'll be ok. IMO, VLC will be better since Xine will change the way totem works (although that might be for the better). I watch lots of DVDs using VLC.

---

### Post by justinflavin on 2005-08-11
i have the same problem. Xine only plays the intro bit to Michael Palin's "Sahara" (the bbc logo)  and then doesnt play the DVD menu.
I can only eject the DVD by right clicking on it and selecting "eject" - hardware eject button doesnt work for some reason.

Not tried VLC yet though, but the lack of an ability to play a DVD menu says to me that a library is needed somewhere. Any hints?

I'm using Ubuntu 5.04 (Hoary Hedgehog) , fresh install on an IBM T34 thinkpad.

---

### Post by Knome_fan on 2005-08-11
[QUOTE=justinflavin]but the lack of an ability to play a DVD menu says to me that a library is needed somewhere. Any hints?
[/QUOTE]
Did you install libdvdcss2?
If not:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Add the needed repositories and then install it:
[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

Hope this helps.  :grin:

---

### Post by ssck on 2005-08-11
i face the same problems :-

[http://www.ubuntuforums.org/showthread.php?t=54015](http://www.ubuntuforums.org/showthread.php?t=54015)

does anybody have the same problems ? i have been trying to fix this for weeks.

any help will be appreciated.

thanks  ](*,)

---

### Post by justinflavin on 2005-08-11
yes. extra repositories added, and libdvdcss2 installed.

libdvd version is 1.2.8-1~5.04ubp1

---

### Post by justinflavin on 2005-08-11
on my DVD playing Mandrake laptop,  i've got a package installed called 
libdvdplay0-1.0.1-5.mdk

its a "portable abstraction layer for DVD menus support"
curiously , the one on Ubuntu is a later version - 1.0.1-6


i grabbed vlc and tried that - all that does is just shut itself down when i tell it to play the DVD.

this isnt good - has anyone ever got Ubuntu 5.04 to play a DVD?  this stuff is a piece of cake in Mandrake.

---

### Post by justinflavin on 2005-08-11
i followed the unofficial ubuntu guide and added extra repos - but there are repos on mirrormax.net that are not officially supported yet.   i got an email from someone saying that these could well be the cause of breakage for dvd playing.

oh well - back to square one. reinstall.

---

### Post by Lord Illidan on 2005-08-11
Yep, I managed to play dvds by following the Ubuntu Guide, but i use kaffeine and xine...

---

### Post by justinflavin on 2005-08-11
my sources now all point to the official ubuntu sources, including the official ubuntu backport repo.

 trouble is , libdvdcss2 isnt in these repos, so i cant play encrypted DVDs.

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=justinflavin]my sources now all point to the official ubuntu sources, including the official ubuntu backport repo.

 trouble is , libdvdcss2 isnt in these repos, so i cant play encrypted DVDs.[/QUOTE]

Did you try universe, multiverse, and hoary-extras?

---

### Post by justinflavin on 2005-08-11
># sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate


here's my  /etc/apt/sources

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=justinflavin]here's my  /etc/apt/sources[/QUOTE]

Try this:

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

instead of this:

```
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-backports main restricted
```

And [read this HOWTO.](http://ubuntuguide.org/#extrarepositories)

---

### Post by justinflavin on 2005-08-11
[QUOTE=Stormy Eyes]Try this:

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

instead of this:

```
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-backports main restricted
```

And [read this HOWTO.](http://ubuntuguide.org/#extrarepositories)[/QUOTE]


i used the mirrormax repos originally, and that didnt work either - had libdvdcss2 installed and totem-xine as well.  i then  reinstalled and just used only the official ubuntu respositories.


but , i'm getting confused here -  you're saying that in order to get a DVD playing you have to use non-official repositories?  wont that screw up future upgrades?

---

### Post by Hairy_Palms on 2005-10-01
[http://developers.videolan.org/libdvdcss/](http://developers.videolan.org/libdvdcss/)

just install the .deb from here, it works fine, all it does is install two files to /usr/lib so you could do it manually too

---

