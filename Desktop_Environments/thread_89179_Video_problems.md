---
title: "Video problems"
date: 2005-11-12
forum: Desktop Environments
---

### Post by corvax on 2005-11-12
Hello i have totem-xine installed have ALL the Codecs installed but every time i goto play a video especially one that embeddd in a webpage it starts to play for a few seconds and then just stops any idea what the problem could be?

---

### Post by frodon on 2005-11-12
Install the media connectivity extension of firefox, you can find it in the extension tab of firefox.
If you don't use firefox there're another plugins which do the job : vlc, mplayer, ...

---

### Post by corvax on 2005-11-13
I installed the extension its a nifty tool but it didnt fix my problem videos still freeze after a couple seconds of play i tried kaffeine nogo on it it kept saying i needed some codec or something forget the proper term it used and i tried vlc which played the audio tracks of the video clips just fine but couldnt play the video.realplayer wont play .wmv videos i tried it too. I cant find mplayer deb files that dont lead me to dependency nightmares. Try playing some of the video clips here [http://www.ebaumsworld.com/index2.shtml](http://www.ebaumsworld.com/index2.shtml)

---

### Post by frodon on 2005-11-13
You can find mplayer in the repositories using synaptic. You need to install realplayer and w32codecs to read .rm and .wma files, i think your problem come from codecs only.
Realplayer is in synaptic i think, and for w32codecs there is severals howto's : [http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs)

If you have some problems finding realplayer and mplayer with synaptic, maybe you have repository problem. If it's the case post your source.list file in the next post, to open it :```
 sudo gedit /etc/apt/sources.list
```

---

### Post by corvax on 2005-11-13
Ive had the w32codecs all along .......I got realplayer from marillat  i prefer to use nano from the cli when editing ;) real player wont  play wmv videos the ONLY thing ive gotten to ever work on ubuntu is totem-xine but for some reson afer i upgraded to 5.10 now video clips on THAT SITE mostly embedded wmv's freeze after a few seconds of play :( I dont ewant my wife to have to boot into windows to play a lousy video clip.
heres my sources.list yeah i know it needs to be cleaned up lol

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


##Updated software from the network
 deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

##Major bug fix updates 

 deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Universe
 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

##Backports Old

#deb http://us.archive.ubuntu.com/ubuntu hoary-backports main
restricted universe
#deb-src http://us.archive.ubuntu.com/ubuntu hoary-backports main
restricted universe

##Security updates
 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Extras
 deb ftp://ftp.nerim.net/debian-marillat/ etch main

## Wine
 deb http://wine.sourceforge.net/apt/ binary/
 deb-src http://wine.sourceforge.net/apt/ source/





```

---

### Post by frodon on 2005-11-13
strange, my firefox completely crash on this site !!!
I also use totem-xine, it works for 90% of the videos and i use mplayer for the others.

---

### Post by corvax on 2005-11-13
i cant install mplayer because 
```
The following packages have unmet dependencies:
  mplayer-386: Depends: libdirectfb-0.9-20 but it is not installable
```
And ubuntu uses a different version 
```
apt-cache search libdirectfb-0.9-2*
libdirectfb-0.9-22 - frame buffer graphics library

```
 MAybe if i put some debian repos in my sources.list and made a preferences file and pinned the debian repos higher than ubuntu i could snag the  0.9-20 version?

---

### Post by frodon on 2005-11-13
Just to be sure that you didn't forget an ubuntu repo, could you post your source.list file ?

---

### Post by corvax on 2005-11-13
Here it is again..............

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


##Updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

##Major bug fix updates 

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 

## Universe
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

##Backports Old

#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-backports main
restricted universe
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-backports main
restricted universe

##Security updates
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Extras
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

## Wine
 deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
 deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by frodon on 2005-11-13
You should add the multiverse repository of breezy :  ```
deb http://us.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy multiverse
```

---

### Post by corvax on 2005-11-13
Well that worked for mplayer now lets see if it will play those videos  (dunno how i missed multiverse must have erased it while messing around)

edit: Well it seems mplayer is doing the same thing the video starts but freezes after a few seconds of play :(
 is there anyone out there that can get these to play?

---

### Post by frodon on 2005-11-14
If i remember well, there is a field where you must specify the w32codecs path in the preference tab of mplayer. The path would be /usr/lib/w32codecs or something like that, if the path is wrong set here the good path and your problem will be solved.

---

### Post by beerorkid on 2005-11-15
so i synaptic'ed w32codecs and it worked.

I had used automatix to get my PC going pretty good, this was one thing that bugged me.

Thanks

---

