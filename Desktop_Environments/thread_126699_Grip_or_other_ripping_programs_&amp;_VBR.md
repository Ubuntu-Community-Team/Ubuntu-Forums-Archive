---
title: "Grip or other ripping programs &amp; VBR"
date: 2006-02-07
forum: Desktop Environments
---

### Post by MJSOnline on 2006-02-07
Hi all.

How do I create VBR mp3s' from a cd?  I have installed Grip, but cannot find the option to select to make VBR mp3s'.

What other packages have this option?  They must be GUI ran, not command line i.e. terminal.

Thanks in advance.  Matthew

---

### Post by MJSOnline on 2006-02-07
Anyone got any ideas?  Thanks.  Matthew

---

### Post by halfvolle melk on 2006-02-07
Hi,
Maybe ABCDE (A Better CD Encoder) works for you. I'm not sure if it supports VBR but I would guess it does.

Edit: The pacage says to be a front end to your favorite encoder. 
"A frontend program to cdparanoia, wget, cd-discid, id3, and your favorite
Ogg/Vorbis, MP3, FLAC, Ogg/Speex and/or MPP/MP+(Musepack) encoder (defaults
to oggenc)."

[http://lly.org/~rcw/abcde/page/](http://lly.org/~rcw/abcde/page/)
[http://www.xiph.org/paranoia/](http://www.xiph.org/paranoia/)

---

### Post by MJSOnline on 2006-02-07
Ok.  I have installed it, but where is it on my system?  Do I uninstall Grip? Matthew

---

### Post by halfvolle melk on 2006-02-07
They're both in /usr/bin/

In a terminal try
```
abcde
```
or
```
cdparanoia
```

You could uninstall Grip if you're not gonna use it anymore.

---

### Post by psusi on 2006-02-07
Have you tried sound juicer?  I'm not sure if it does mp3, but I use it to encode to vbr ogg and it works great.  Besides, ogg is legal and free, mp3 is not.

---

### Post by MJSOnline on 2006-02-07
[QUOTE=psusi]Have you tried sound juicer?  I'm not sure if it does mp3, but I use it to encode to vbr ogg and it works great.  Besides, ogg is legal and free, mp3 is not.[/QUOTE]

Ok.  How do I make Sound Juicer do VBR in ogg?  Can I convert the ogg files to mp3 but keep the vbr?  Aso is "abcde" package a GUI app or a command line?  If I take Grip off will "abcde" be shown in GUI mode?
Thanks again. Matthew

---

### Post by halfvolle melk on 2006-02-07
[QUOTE=MJSOnline]Ok.  How do I make Sound Juicer do VBR in ogg?[/QUOTE]
Hmm, in prefs you can't seem to either let it do that or not. Probably does VBR by default.

> Can I convert the ogg files to mp3 but keep the vbr?
You probably could but then you'd have wav -> loss.ogg -> moreloss.mp3 so if you really want mp3 it's best to convert to mp3 directly.

> Aso is "abcde" package a GUI app or a command line?  If I take Grip off will "abcde" be shown in GUI mode?
I just installed it myself and it apears to be command line only. And I saw that cdparanoia comes with Ubuntu.

Pop in a CD and type "abcde" in a terminal and away he goes, making ogg VBR by default. mp3 is also supported so I guess with VBR as well. Haven't figured out yet how to do that though.

edit: I did some searching and Grip seems to use Lame and Lame seems to use VBR by default. Could be wrong though.

---

