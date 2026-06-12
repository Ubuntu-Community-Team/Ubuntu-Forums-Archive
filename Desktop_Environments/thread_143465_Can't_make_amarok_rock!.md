---
title: "Can't make amarok rock!"
date: 2006-03-12
forum: Desktop Environments
---

### Post by chugru on 2006-03-12
Hi, All...

I'm totally new with amarok.

When I try to play an mp3 file, I get: > Some media could not be loaded (not playable).
How can I find out what is causing this?
What must I do to get this to play?

Thanks...

---

### Post by IGNIZ on 2006-03-12
```
sudo apt-get install amarok-xine
```

you need a good engine

---

### Post by gingermark on 2006-03-12
The correct codecs probably aren't installed. (see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats))

---

### Post by chugru on 2006-03-12
[QUOTE=IGNIZ]```
sudo apt-get install amarok-xine
```

you need a good engine[/QUOTE]

OK, did that. Now I'm a bit confused as to which codecs to install... Also when I configure the xine Engine, is there a preferred **output plugin** to select for mp3's??

---

### Post by kittycatsexycat on 2006-03-12
can some one please give this person the gstreamer 0.8 or something command line...

something like....
apt-get install gstreamer 0.8

and thats the mp3 codecs or something...

---

### Post by kittycatsexycat on 2006-03-12
you need automatix.. i recommend it to every linux user.. its basically a starter pack....

Do not run ANYTHING while running this.... this is illegal in america....

type these lines in one after the other in the terminal.... hitting enter after each line...

only works with breezy... there is more you need to know but you need to search the forums for it.... but this'll work... it installs everything you need...

wget [http://beerorkid.com/automatix/automatix_5.6-2_i386.deb](http://beerorkid.com/automatix/automatix_5.6-2_i386.deb) 
sudo dpkg -i automatix_5.6-2_i386.deb

---

### Post by chugru on 2006-03-12
[QUOTE=kittycatsexycat]you need automatix.. i recommend it to every linux user.. its basically a starter pack....

Do not run ANYTHING while running this.... this is illegal in america....

type these lines in one after the other in the terminal.... hitting enter after each line...

only works with breezy... there is more you need to know but you need to search the forums for it.... but this'll work... it installs everything you need...

wget [http://beerorkid.com/automatix/automatix_5.6-2_i386.deb](http://beerorkid.com/automatix/automatix_5.6-2_i386.deb) 
sudo dpkg -i automatix_5.6-2_i386.deb[/QUOTE]

Unfortunately, I get: ```
dpkg: dependency problems prevent configuration of automatix:
 automatix depends on zenity; however:
  Package zenity is not installed.
dpkg: error processing automatix (--install):
 dependency problems - leaving unconfigured

```

I looked at zenity (which has dependency requirements)... Am I going in the right direction??:???:

---

### Post by kittycatsexycat on 2006-03-12
did you get my email... if so thats all i know about it my self... it helped me out and i wanted to help someone else out....

Sorry if it doesn't work but you should ask people about it because if you can get it to work.... it rules..... well you'll know if you've read it.. lol

:KS

---

### Post by kittycatsexycat on 2006-03-12
what os are you using....

---

### Post by chugru on 2006-03-12
[QUOTE=kittycatsexycat]what os are you using....[/QUOTE]
 I'm using Kubuntu Breezy...

---

### Post by chugru on 2006-03-12
Got the email and running the install...
Works perfectly!!

Thanks!

---

### Post by claydoh on 2006-03-12
You will need the akode-mpeg package, which is in Universe. You will need to enable that before you can use Adept, synaptic or the command-line apt command, and then you possibly may wanrt to install other amarok-engines, the above-mentioned amarok-xine is also in Universe, but the gstreamer and the arts engines are already available. I would sugggest trying the arts-engine, and the xine-engine as they may work better for you in KDE than the gstreamer engine.

---

### Post by chugru on 2006-03-12
[QUOTE=claydoh]You will need the akode-mpeg package, which is in Universe. You will need to enable that before you can use Adept, synaptic or the command-line apt command, and then you possibly may wanrt to install other amarok-engines, the above-mentioned amarok-xine is also in Universe, but the gstreamer and the arts engines are already available. I would sugggest trying the arts-engine, and the xine-engine as they may work better for you in KDE than the gstreamer engine.[/QUOTE]

Thank you for those comments. I downloaded akode-mpeg and I have managed to get the xine-engine to work!

---

