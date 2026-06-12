---
title: "How to &quot;play it all&quot; using mplayer?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by kentl on 2006-07-15
Hi!

I'm quite new to Linux and Kubuntu (which is my Ubuntu flavor of choice), still I know my way around and have configured my system in such a way that I am *pretty* satisfied. One thing is still annoying me though, which leads me to the topic of this thread,

I want to use mplayer to play "all" formats? I know that the XBOX software [XBOX Media Center]("http://www.xboxmediacenter.com/") is based on mplayer. And it can play **almost anything**.

I would like it to work as well as XBMC using my installation of Kubuntu 6.06 and mplayer.

When I discussed this with a guy who uses Gentoo he said that he had "compiled in" support for a lot of formats, which he said was one of the things Gentoo was better at than Kubuntu. As I am a newless cluebie this is hard for me to grasp, and I took what he said with a grain of salt.

All ideas and tips appreciated! If you suggest a method which you have used yourself, please tell if there are any drawbacks (ie formats which can not be played).

---

### Post by infoburner on 2006-07-15
check out this thread : [http://ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://ubuntuforums.org/showthread.php?t=80295&highlight=automatix)

one of the things automatix will install for you is the codecs for many different media formats

---

### Post by T700 on 2006-07-15
I'll second the suggestion for Automatix.  It really makes life with Linux easier.

Paul

---

### Post by Lord Illidan on 2006-07-15
> **kentl said:**
> Hi!

I'm quite new to Linux and Kubuntu (which is my Ubuntu flavor of choice), still I know my way around and have configured my system in such a way that I am *pretty* satisfied. One thing is still annoying me though, which leads me to the topic of this thread,

I want to use mplayer to play "all" formats? I know that the XBOX software [XBOX Media Center]("http://www.xboxmediacenter.com/") is based on mplayer. And it can play **almost anything**.

I would like it to work as well as XBMC using my installation of Kubuntu 6.06 and mplayer.

When I discussed this with a guy who uses Gentoo he said that he had "compiled in" support for a lot of formats, which he said was one of the things Gentoo was better at than Kubuntu. As I am a newless cluebie this is hard for me to grasp, and I took what he said with a grain of salt.

All ideas and tips appreciated! If you suggest a method which you have used yourself, please tell if there are any drawbacks (ie formats which can not be played).

Ideally, when Gentoo users start saying things like that, take everything with a grain of salt.

Just read about restricted formats on the forum and in the wiki and you are set.

---

### Post by Fac51 on 2006-07-15
```
wget ftp://mplayerhq.hu/MPlayer/releases/codecs/all-20060611.tar.bz2

tar xvjf all-20060611.tar.bz2

cd all-20060611

sudo mkdir /usr/lib/win32

sudo cp * /usr/lib/win32
```

see if that works, it works for me

---

### Post by kentl on 2006-07-18
Fac51: It seems to work!

Now I only wish the the mplayer plugin for firefox where a bit friendlier and didn't open a "special tab" where the All-In-One-Gestures extension can't work, which means I can't use mouse gestures to close the tab. (This works much better in Windows where the integration between FireFox and media player seems more flawless and natural.)

---

### Post by Fac51 on 2006-07-19
you can customize All-In-One-Gestures, just dig around a bit, i'm sure you'll find what you need

---

### Post by kentl on 2006-07-19
No I can't customize it so that I can use it at a tab which only contains the mplayer-firefox plugin. It's some kind of special tab which doesn't allow the extension to do its job.

---

