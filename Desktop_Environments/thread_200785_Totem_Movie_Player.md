---
title: "Totem Movie Player"
date: 2006-06-20
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-06-20
I use Totem in Debian and like how it's included by default in Ubuntu however out the box, Totem can't even play a simple .MPG file. I don't understand why. I get an error that says it does not have a codec installed to handle the file type. How can Totem not read a simple .MPEG.

Anyone know how to resolve this and if there is a "all in one" codec pack?

---

### Post by Akita on 2006-06-20
MP3 is a "restricted" format (it's proprietary) - Instructions here:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by GoogleNinja on 2006-06-20
[QUOTE=Carlwill]I use Totem in Debian and like how it's included by default in Ubuntu however out the box, Totem can't even play a simple .MPG file. I don't understand why. I get an error that says it does not have a codec installed to handle the file type. How can Totem not read a simple .MPEG.

Anyone know how to resolve this and if there is a "all in one" codec pack?[/QUOTE]

as cool as gstreamer looks like it will be one day, it really doesn't cut it nowadays, at least for movies. totem uses gstreamer as a backend by default, you can get it to use xine instead by apt-getting totem-xine

---

### Post by Bloch on 2006-06-20
> Anyone know how to resolve this and if there is a "all in one" codec pack?
Yes, there are two (at least). Not codec packs as such, but scripts that will download and install these.

They are Automatix and Easy Ubuntu. There is information on how to get them on these forums - they have their own section each.

I am sure pople have their favourite, and I don't know why there are two. Automatix worked for me. 

Yeah, proprietary codecs etc are the big pain in Ubuntu. I can understand your surprise. Given that the introductory page below is aimed at average users, I think the ubuntu team should mention this. They mention that OpenOffice is compatible with MS Office - they should give the bad news along with the good. What they say about Totem is misleadiing. 

Correction, it mislead me and a few other people who had huge ignorance about proprietary formats and licencing issues
[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

---

### Post by loserboy on 2006-06-20
so is it like evil for us to use mp3 or any license format?
are we supporting The Man when we do?

---

### Post by GoogleNinja on 2006-06-20
the best explination of good and evil (in a free software sense) is the fsf site. [www.fsf.org](www.fsf.org)

---

### Post by loserboy on 2006-06-20
mmhmmm i see, thanks for clarifying the help doc was pretty vague

---

