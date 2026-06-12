---
title: "Xmms support for m4a and wma"
date: 2006-01-15
forum: Desktop Environments
---

### Post by jyer on 2006-01-15
Hi,
I've just installed the last version of the Kde desktop which provides a player called noatun. Though I don't like the player much, I'm most impressed by the quantities of formats it joyfully reads, especialy m4a and wma. 
Since I started running Linux (quite recently in fact), I've been using Xmms which I most appreciated and don't perticularly want to have to renonce to. Since the start, I've been trying unsuccesfully to install wma and m4a (especially the latter) support, in an understanble beginner-friendly way. 
Now, my question is: can I and how simply use noatun libraries to read all the formats I could possibly dream of (especially to two mentionned in this thread) with Xmms? If not, does any of you know a simple way to ensure m4a and wma support for xmms?
_Or du you know of any other programm, similar to Xmms, that supports these audioo formats?_
Thanks a lot,
jr

Come on, does none of you use xmms to read m4a of wma?

---

### Post by jyer on 2006-02-04
No answers within two weeks?
I can't believe none of you ever listen to m4a format...

---

### Post by duffydack on 2006-02-04
not tried but i know wmv play in linux with the w32codecs.
dont wma?

---

### Post by jyer on 2006-02-04
Well that is the whole point: why are the codecs I installed work with most of my media players (Xine, Mplayer, etc support m4a and wma) except Xmms?
Is there anything I should do to inform Xmms about my codecs?

---

### Post by duffydack on 2006-02-04
only thing i can suggest then is to convert em to mp3.....thats what ive done...as i just dont like any other players output as far as equaliser settings go (imported from winamps, as they seem to sound fine for my plain 2.1 speaker setup).  xmms is the only app that sounds the same as winamp with the same EQ settings.. the rest are way too quiet or just plain crazy..  
and no i wont buy new speaker just to please linux! :)
i dont believe in bending to suit linux, it should work around me.
if windows is so crap and works the way i want, why doesnt a superior Os do as good..

---

### Post by jyer on 2006-02-04
There is bound to be a way to get xmms to read other sound formats. Why should they be supported by other media player then?
The solution of converting everything to Mp3 doesn't really sute me. As you pointed out, if a poor quality OS allows you to read all formats within one program, then Linux should too.
Thanks for you replies anyway...

---

### Post by nykobing on 2006-02-06
Xmms plays m4a here fine. You need to install xmms-mp4 in order to get it to work.

These are stock m4a I made in Nero or Itunes, they have no DRM. If your files aren't playing because of DRM I don't know what you should do.

---

### Post by jyer on 2006-02-09
Hi, 
Thanks a lot for you answer.
Turns out the mp4 plugin works fine for m4a. I've read through the list of xmms plugins in apt-cache and didn't find anything for wma. Any idea?
Especially, _is there a way of getting XMMS to use the other plugins I've installed on my system?_They seem to be working fine with Xine and Mplayer...

---

### Post by jyer on 2006-02-09
Hem. The plugin seems to suck a lot of memory while loading a song. Monitored up to 72% of my Memory wax being used by xmms, no need to say that my other programs went a little hirewire. Ever occured to any of you?

---

### Post by Teroedni on 2006-02-09
xmms-mad

try it

also do you got ffmpeg installed?

---

### Post by jyer on 2006-02-10
Hi, 
Thanks for your answer.
ffmpeg was already installed.
Installed xmms-mad, though still can't read wma.

PS. The memory issu has been solved (reboot).

---

### Post by jyer on 2006-02-10
I've finally found a solution for wma.
Thanks for you support.

I downloaded xmms-wma-1.0.4-1.i386.rpm here [http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

```

sudo alien xmms-wma-1.0.4-1.i386.rpm

sudo dpkg -i *.deb

```

---

### Post by Raavea on 2006-05-03
So, now I have downloaded that file, I type 

sudo alien xmms-wma-1.0.4-1.i386.rpm

sudo dpkg -i *.deb

 into the terminal? Will that work, or do I need to change anything?
 EDIT: I am on Ubuntu.

---

### Post by Mr Green on 2006-05-13
Jyer's tip worked like a charm, but you need to install alien first:
sudo apt-get install alien

---

### Post by Boatswain on 2006-07-05
Just tried this, but with the (presumably more recent?) xmms-wma-1.0.5-1.i386.rpm and it doesn't seem  to be working.  Xmms can at least now recognize the track  names of WMAs, but can't play.  Any advice?

---

### Post by kris kincaid on 2006-08-01
Nice find jyer. Works perfectly for me.

I ripped my entire cd collection to (don't laugh) .wma format, now I can play them with XMMS. :)

---

### Post by Jose Catre-Vandis on 2006-12-22
Thanks, this method worked for me too:

Download xmms-wma-1.0.4.1-1.i386.rpm from [http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

then open terminal in your download directory
and type following commands
```
sudo alien xmms-wma-1.0.4-1.i386.rpm

sudo dpkg -i xmms-wma*.deb
```

And wma playback in xmms is yours

Update Manager will offer you an update too, but you need the repo activated for this

---

