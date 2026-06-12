---
title: "how to make movies from pictures"
date: 2006-06-05
forum: Desktop Environments
---

### Post by murataht on 2006-06-05
hi there,
i have been looking for a tool that creates video from pictures. i want to make small movies from my pictures. but kino and other movie editor tools do not have this feature. so, is there any tool to do this? by the way Picasa does have timeline feature, but it does not work on my dapper and it does not have music integration feature, besides i am using f-spot to manage my photos. 
thanks

---

### Post by JonnyRo on 2006-06-05
there is [http://www.pic2vid.com](http://www.pic2vid.com), and the microsoft photo story tool.  The bummer about both is that they require M$ in some form or another.  The pic2vid setup only works on IE, and you of course know that MS wouldnt make a picture tool for Linux.

Let me know if you find a good solution for linux.  In the meantime you might just be better off taking the pics over to another PC on a pendrive and using pic2vid to make them into a movie.

---

### Post by ed_agamemnon on 2006-06-05
do you mean stopmotion? - are you animating?

try searching for 'stopmotion', there are a few cool tools around.

---

### Post by murataht on 2006-06-05
it seems the pic2vid is the right tool. too bad it does not work under linux.
but stopmotion is not the tool i am looking for i think. i am looking for a tool that i could make videos from the pictures i take in vacations. 

i cheked imagemagick, but it only creates gifs from images. still not the one i need.

---

### Post by murataht on 2006-06-06
no more suggestions?

---

### Post by az on 2006-06-06
dvd-slideshow and slideshow creator?

[http://slcreator.sourceforge.net/](http://slcreator.sourceforge.net/)

It is pretty alpha, but it seems to work.

---

### Post by eeclark on 2006-06-06
maybe create the .avi using picasa and then add an audio track with kino?
maybe?
:-)

You might need to install:

The following extra packages will be installed:
  liba52-0.7.4-dev libimlib2 libmjpegtools0c2a liboggflac3 libquicktime0
Suggested packages:
  html2ps
The following NEW packages will be installed:
  ffmpeg imagemagick kino kinoplus lame liba52-0.7.4-dev libimlib2
  libmjpegtools0c2a liboggflac3 libquicktime0 mjpegtools mpeg2dec sox toolame
  vorbis-tools
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.

---

### Post by toLa` on 2006-06-06
I did something like this a few years ago with Counter-Strike, made a .avi movie out of .bmps using a program called VideoMach (under Windows of course :(), I haven't visited their site for a year or so, maybe they've ported a Linux version :D

---

### Post by eeclark on 2006-06-06
[QUOTE=eeclark]maybe create the .avi using picasa and then add an audio track with kino?
maybe?
:-)

You might need to install:

The following extra packages will be installed:
  liba52-0.7.4-dev libimlib2 libmjpegtools0c2a liboggflac3 libquicktime0
Suggested packages:
  html2ps
The following NEW packages will be installed:
  ffmpeg imagemagick kino kinoplus lame liba52-0.7.4-dev libimlib2
  libmjpegtools0c2a liboggflac3 libquicktime0 mjpegtools mpeg2dec sox toolame
  vorbis-tools
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.[/QUOTE]


I just did this and it worked really well.
[http://www.messinet.com/~eeclark/test.mpeg]("http://www.messinet.com/~eeclark/test.mpeg")
File is about 5 Megs and is in mpeg format. Keep in mind it was quick and dirty.

---

### Post by murataht on 2006-06-06
thanks everybody,
now i am trying slideshow-creator.
and also i can edit it with kino i think. 
i will let you know with the result. 
and i will try picasa+kino suggestion too. :)
thanks again.

---

### Post by revertex on 2007-02-01
Is this a linux forum?
it seems there is no linux users out there.

mencoder is what you are looking for.

It's a CLI tool, but don't be scared, it's powerfull and flexible enough to produce amazing results.

maybe this tutorial could help

[http://www.linuxfocus.org/English/September2004/article347.shtml](http://www.linuxfocus.org/English/September2004/article347.shtml)

man mencoder is your friend

you can try stopmotion, a pretty fontend to do all mencoder dirty job.

cheers

---

