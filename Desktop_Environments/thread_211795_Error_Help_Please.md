---
title: "Error Help Please"
date: 2006-07-08
forum: Desktop Environments
---

### Post by majkmil on 2006-07-08
Hi, I installed ReaalPlayer to watch video in firefox. But when I run it in terminal I get this error.

miller@ubuntumac:~/Desktop/RealPlayer$ realplay
/home/miller/Desktop/RealPlayer/realplay.bin: symbol lookup error: /home/miller/Desktop/RealPlayer/plugins/swfrender.so: undefined symbol: _Z27FlashRendererCreateInstancePP8IUnknow

What does undefined sybol mean?
Thanks
 I am on a PPC running dapper

---

### Post by Fac51 on 2006-07-09
ignore the error and uninstall your realplayer

download codecs from mplayerhq.hu
```
user@localhost:~$ wget ftp://mplayerhq.hu/MPlayer/releases/codecs/all-20060611.tar.bz2
```

extract contents
```
user@localhost:~$ tar xvjf all-20060611.tar.bz2
```

create folder /usr/lib/win32
```
user@localhost:~$ sudo mkdir /usr/lib/win32
```

Copy contents of ~/all-20060611/ to /usr/lib/win32
```
user@localhost:~$ cp ~/all-20060611/* /usr/lib/win32
```

install mplayer and mozilla-mplayer
```
user@localhost:~$ sudo apt-get install mplayer mozilla-mplayer
```

that will get you going for a multitude of video formats, as for the swf thinger... pfft 

first, make sure you have "restricted" "multiverse" and "universe" in your /etc/apt/sources.list
example(my /etc/apt/sources.list)
```
#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

#Repositorio plf
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

deb http://theli.free.fr/packages/dapper/ ./

```

then...
```
user@localhost:~$ sudo apt-get install x-ttcidfont-conf msttcorefonts freefont ttf-bitstream-vera ttf-xfree86-nonfree
```

after that, firefox should be able to detect the flash plugin just fine

this should work perfectly, at least it does for me, but i'm not on ppc.... good luck

---

### Post by majkmil on 2006-07-12
Sorry to drag this thread up again. fac51 has me closer than I have been with streaming video in firefox. (THANK YOU). I now get to 99% buffering at Apple trailers and I get audio but no video. I must be missing some codec but I have installed every thing I culd find. I have given up hope on nfl.com, I only get 15% buffer and then nothing. I also tried multimedia conectivity extension and this works sometimes but I still get errors. OH, my error on nfl.com is (could not resolve name or something). Please help, I feel I am so close. I would really like to see the video IN firefox, instead of having to copy a URL and paseting in mplayer or totem.  Thanks in advance

---

### Post by catlett on 2006-07-12
I just watched a video on NFL.com without any problems. I use the Dapper Guide for my setups. It has always given me full support for just about everything.
The only other thing I do is go to thew Ubuntu wiki "Restricted Formats" and get the instructions for downloading win32codecs and the package name for mp3 and vorbis.
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

P.S. The vide played through RealPlayer

---

### Post by Fac51 on 2006-07-13
> **majkmil said:**
> Sorry to drag this thread up again. fac51 has me closer than I have been with streaming video in firefox. (THANK YOU). I now get to 99% buffering at Apple trailers and I get audio but no video. I must be missing some codec but I have installed every thing I culd find. I have given up hope on nfl.com, I only get 15% buffer and then nothing. I also tried multimedia conectivity extension and this works sometimes but I still get errors. OH, my error on nfl.com is (could not resolve name or something). Please help, I feel I am so close. I would really like to see the video IN firefox, instead of having to copy a URL and paseting in mplayer or totem.  Thanks in advance

try this....
```
user@localhost:~$ sudo apt-get install w32codecs
```

> **catlett said:**
> I just watched a video on NFL.com without any problems. I use the Dapper Guide for my setups. It has always given me full support for just about everything.
The only other thing I do is go to thew Ubuntu wiki "Restricted Formats" and get the instructions for downloading win32codecs and the package name for mp3 and vorbis.
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

P.S. The vide played through RealPlayer

P.S. screw realplayer

---

### Post by catlett on 2006-07-13
> **Fac51 said:**
> try this....
```
user@localhost:~$ sudo apt-get install w32codecs
```



P.S. screw realplayer

Most of my video comes through my totem xine plugin but that file came through realp[layer. It is the first time a video defaulted to Realplayer instead of my totem plugin. That is why I mentioned "it played through realplayer". Since it was the first video file that defaulted to realplayer instead of totem, it may be an issue when trying to play the video.

Like I said earlier, I use the Dapper Guide. That is how I ended up with the totem plugin instead of mplayer. I use to use mplayer until the guide referred to totem. I switched and found out totem was better (at least for me)

About 
> P.S. screw realplayerThat is easy for you to say, you are not trying to enjoy a site who's conntent may require it. Just because your  "hard-core" OSS doesn't mean majkmil's choices should be limited or that he shouldn't enjoy a site that requires it.
Plus if that is your attitude you shouldn't be running Ubuntu. Ubuntu now has a commercial repository that holds RealPlayer, Opera and more. You should probably instal Debian Sid and gnome instead of using a distro that supports and furthers proprietory software, consdering your purist spirit.

---

### Post by Fac51 on 2006-07-13
> **catlett said:**
> Most of my video comes through my totem xine plugin but that file came through realp[layer. It is the first time a video defaulted to Realplayer instead of my totem plugin. That is why I mentioned "it played through realplayer". Since it was the first video file that defaulted to realplayer instead of totem, it may be an issue when trying to play the video.

Like I said earlier, I use the Dapper Guide. That is how I ended up with the totem plugin instead of mplayer. I use to use mplayer until the guide referred to totem. I switched and found out totem was better (at least for me)

About 
That is easy for you to say, you are not trying to enjoy a site who's conntent may require it. Just because your  "hard-core" OSS doesn't mean majkmil's choices should be limited or that he shouldn't enjoy a site that requires it.
Plus if that is your attitude you shouldn't be running Ubuntu. Ubuntu now has a commercial repository that holds RealPlayer, Opera and more. You should probably instal Debian Sid and gnome instead of using a distro that supports and furthers proprietory software, consdering your purist spirit.

i can view anyformat, except flash 8(of course)
if you do not know how to make shit run without out realplayer, that is not my fault, a person asked for help, and i assisted. and here you are accosting me like a femme-nazi outside of an abortion clinic, and for what? realplayer... wow, your ePenis is obviously way larger than mine, i bow to you good sir.  as for limiting choice.... hmm, OSS or the same old shit that causes problems... why make the switch?
i have no time for your petty activism, so please, "flame" somewhere else....  i'm sure you will find lots of people with similar interests to your own here... [http://thevistaforums.com/](http://thevistaforums.com/)  :wink:

---

