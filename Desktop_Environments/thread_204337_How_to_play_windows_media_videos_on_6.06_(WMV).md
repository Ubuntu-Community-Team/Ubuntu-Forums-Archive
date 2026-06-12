---
title: "How to play windows media videos on 6.06 (WMV)"
date: 2006-06-26
forum: Desktop Environments
---

### Post by anony on 2006-06-26
Hey, I am looking to play windows media videos (WMV) and I do not know where to get the codects for ubuntu 6.06, if any one can help out thanks.

---

### Post by taurus on 2006-06-26
You can use Automatix to install the codecs and you can play everything after that...

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by evilghost on 2006-06-26
Add PLF to /etc/apt/sources.list, apt-get update, and apt-get install w32codecs.

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

They work with Dapper too, or you can just grab the deb and dpkg -i it from [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/)

---

### Post by anony on 2006-06-26
I allready have automatix and wmv still don't play.

---

### Post by taurus on 2006-06-26
Did you use Automatix to install w32codecs?  Installing Automatix will not do anything so you need to use it to install other apps...

---

### Post by anony on 2006-06-26
I did, im reistalling the (non-free) codecs well see if this works.

---

### Post by anony on 2006-06-26
I get this error:
Could not open *****.wmv
Archive type not supported.

---

### Post by Anduu on 2006-06-26
[QUOTE=anony]I get this error:
Could not open *****.wmv
[COLOR="Red"]Archive type not supported[/COLOR].[/QUOTE]


Seems to me the wrong app is trying to open the file

Right click and select a media player.

---

### Post by anony on 2006-06-26
Found the error, thanks guys.

---

### Post by vidak on 2006-06-27
[QUOTE=anony]Found the error, thanks guys.[/QUOTE]

I use mplayer downloaded as source with all the codecs from [www.mplayerhq.hu](www.mplayerhq.hu). It knows all the video formats I've ever met...

---

### Post by joselin on 2006-06-27
Follow the intructions of the oficial ubuntu wiki.
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Cheers

---

### Post by lylrq on 2006-07-23
VLC solve ur all problems

---

