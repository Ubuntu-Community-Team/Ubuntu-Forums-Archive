---
title: "streaming mp3s w/ icecast - libshout?"
date: 2005-11-20
forum: Desktop Environments
---

### Post by djlosch on 2005-11-20
so im lookin around to find out how to stream mp3s...

after f'ing around with ices2 and icecast and wondering why the hell it's not working, i finally found out that ices2 is not for mp3s... only for ogg.  so i go to get ice0 which supposedly handles mp3s.  so i check apt for it... nada.

then i go fetch the tarball... but i dont have a c compiler...

so i: sudo apt-get install build-essential gcc gcc-3.4 libncurses5 libncurses5-dev

so then i go back to compile.. yay starting... WRONG

cant locate libshout.

any ideas, or anyone have a .deb for ice0?

---

### Post by JimmyJazz on 2005-11-20
[http://www.ubuntuforums.org/showthread.php?t=73098](http://www.ubuntuforums.org/showthread.php?t=73098)
check out my guide to setting up an online radio station (using mp3s) at the above link.
and hey why not check out my station while you are at it...
[http://jimmyjazz.homeip.net:808/listenwavy/](http://jimmyjazz.homeip.net:808/listenwavy/)

---

### Post by JimmyJazz on 2005-11-20
libshout should be in the repos you may need to enable universal repos though...
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)
(just use "breezy" instead of "hoary")

---

### Post by djlosch on 2005-11-20
hehe... using your guide, i was gettin nowhere fast...

tons of crap strangely not in the repos, no xml nor gtk support, screwing around with muse, darkice, ice2, ice0, and then finally ezstream, 6 hrs later i got it up using icecast2 + ezstream.

---

### Post by djlosch on 2005-11-20
im gonna slap together a new machine and see if i can make a ubuntuguide style easy install process for it.

i already started making some at my site ([http://www.djlosch.com/post_retrieve.php?pid=59](http://www.djlosch.com/post_retrieve.php?pid=59)), but im not really advertising it yet as complete as it's got some stuff i need to still test out and fix (that's why it's not in the sig yet hehe).

---

### Post by djlosch on 2005-11-20
these are my repos and they did not have libshout, libvorbis, libogg, ezstream, and darksnow (did have darkice though, but not compiled with lame support).
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

#deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
#deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

deb http://soulmachine.net/breezy unstable/

```

---

### Post by JimmyJazz on 2005-11-21
did you search synaptic for libshout it will be called libshout3 so if you are using apt-get it would be: sudo apt-get install libshout3
so on libvorbis is also not simply libvorbis but libvorbis0a
then libogg0
so what you need is 
libshout3
libvorbis0a
libogg0

if you wanna compile ices from my guide with lame support you will need
liblame0

hope that helps, sorry my guide wasn't easy for you I'll admidt I should have been much more clear about the whole compile process and dependencies.
I really recommend ices0 though its worked great for me with zero trouble.

---

### Post by garyng on 2005-11-21
[QUOTE=djlosch]so im lookin around to find out how to stream mp3s...

after f'ing around with ices2 and icecast and wondering why the hell it's not working, i finally found out that ices2 is not for mp3s... only for ogg.  so i go to get ice0 which supposedly handles mp3s.  so i check apt for it... nada.

then i go fetch the tarball... but i dont have a c compiler...

so i: sudo apt-get install build-essential gcc gcc-3.4 libncurses5 libncurses5-dev

so then i go back to compile.. yay starting... WRONG

cant locate libshout.

any ideas, or anyone have a .deb for ice0?[/QUOTE]

You can use the older icecast-server and icecast-client that is in debian(at least), which supports mp3. nothing to compile.

If you want mixing, liveice is there too, which can also itself serve mp3 streams to icecast server(not icecast2).

---

