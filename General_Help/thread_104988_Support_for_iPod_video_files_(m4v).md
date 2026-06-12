---
title: "Support for iPod video files (m4v) ???"
date: 2005-12-17
forum: General Help
---

### Post by kerinin on 2005-12-17
i've been playing with the [DTV]("http://participatoryculture.org") as the linux port is developed, and i've noticed that some of the people are publishing video files with the 'm4v' extension, and i have no idea how to view them.

after a little research, it turns out that m4v is the file format used by the new video iPods to display video.  Are there any plans to support this in Ubuntu?  it seems like an important filetype, especially considering that many people probably plan to use Rhythmbox as their iPod link (otherwise they'd have to dual-boot just to use their iPod).

Personally, i'd like file support, or at least the ability to transcode the filetype so that i can watch videos being distributed on DTV.  

Just curious...

---

### Post by hensonkid on 2006-01-11
Give MPlayer a try.

---

### Post by kaamos on 2006-01-11
MPlayer (at least from cvs) plays them very well.

---

### Post by CompShrink on 2006-02-07
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=85190](http://ubuntuforums.org/showthread.php?t=85190)

On the first page is links to deb files compiled for breezy, I'd suggest the P3 SSE MMX one, as that's a pretty decent baseline for most people.

---

### Post by stevea1210 on 2006-03-08
I followed the link in the above post, and built mplayer from cvs.  It didn't play the m4v from itunes though.  I got the below error

```

Playing /netshares/movies/itunes/Downloads/The Carpet.m4v.tmp/download.m4v.
ISO: Unknown File Type Major Brand: M4V 
Quicktime/MOV file format detected.
VIDEO:  [drmi]  320x192  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Cannot find codec for audio format 0x736D7264.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Cannot find codec matching selected -vo and video format 0x696D7264.
Read DOCS/HTML/en/codecs.html!

```

Is there something else I need to do in order to play movie files from itunes?

---

### Post by akiro.yamamoto on 2006-03-08
I know this may sound silly, but did you install the w32codecs?

---

### Post by stevea1210 on 2006-03-09
Doesn't sound slly, often times it is the simple steps that are overlooked.  However, in this case, win32 codecs are installed.

I used mplayer to play other media files, and it worked fine.  It is just the m4v ipod videos that won't play.

---

### Post by stevea1210 on 2006-03-24
Bump...

---

### Post by Dr.Smurf on 2006-04-27
bump.. i buyed some videos from itunes shop in windows and how i play on linux.. seems same situantion... bump bump...

---

### Post by Jerrac on 2006-08-21
So, has anyone been able to play videos downloaded from itunes music store on linux?

---

### Post by linkunderscore on 2008-06-18
having the same problem

i guess thats what i get for actually BUYING a movie... :mad:

---

