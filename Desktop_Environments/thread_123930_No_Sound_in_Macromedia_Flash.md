---
title: "No Sound in Macromedia Flash"
date: 2006-01-31
forum: Desktop Environments
---

### Post by danish_demon on 2006-01-31
i am reposting [this]("http://www.ubuntuforums.org/showthread.php?t=24509") thread from warty discussion in here.  basically, i (and some other people) have no sound when we play flash files (for example, from video.google.com), but have sound when playing mp3s or other files.  i am running firefox 1.5 and can see the videos fine, but no sound.  i installed flash via automatix.  anyone know what else can be done (besides the symbolic link mentioned in the other thread) to solve this problem? 

thanks.

---

### Post by ringding on 2006-01-31
It appears that there is some bug in FF1.5  check this thread for the fix....this is how I fixed mine......

[http://www.ubuntuforums.org/showthread.php?t=122495&highlight=flash+sound]("http://www.ubuntuforums.org/showthread.php?t=122495&highlight=flash+sound")

---

### Post by danish_demon on 2006-01-31
thanks, i found a solution in one of those threads.  i also was able to inadvertently get some of the other media players to work.  nice.

---

### Post by Micro$oftWinblows on 2006-04-29
I'm running Firefox 1.0.8  on Breezy Badger and I'm having the same problem. I went to [www.jdimenna.com](www.jdimenna.com) and tried to listen to the music, but there's no sound. Sound works with everything else though.

When I sudo firefox, the sound works. (I know I shouldn't do this but I thought it'd be valuable to problem solving).

Anyone know what's going on?

---

### Post by Sef on 2006-05-01
Try this to get the sound to work.  Did the trick for me for YouTube.

sudo apt-get update

sudo apt-get install alsa-oss

Hmmmm...that reminds me since I reinstalled my os, I need to download that.

---

### Post by louis_nichols on 2006-05-01
I had this problem also and solved it by simply starting firefox with

```
aoss firefox
```

I also updated all launchers to have the same command.

---

### Post by Jose Catre-Vandis on 2006-05-01
I am using alsa
Firefox 1.5.0.2
Dapper (up to date)
Just fixed the flash sound problem:

```
 sudo gedit /etc/firefox/firefoxrc
```

# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).

Changed "none" to "auto"

# which /dev/dsp wrapper to use
FIREFOX_DSP="auto"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).

restarted firefox and had sound working fine

---

