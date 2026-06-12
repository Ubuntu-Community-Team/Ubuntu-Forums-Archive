---
title: "can't open .zip files"
date: 2006-02-12
forum: Desktop Environments
---

### Post by Bou on 2006-02-12
When I download a .zip file and open it, only empty (0b) files with weird names appear on it, and I get an error mesage: "caution: filename not matched:  6f2c2501".

[http://www.elrellano.net/audio/audiofiles/Broma-por-un-mp3.zip](http://www.elrellano.net/audio/audiofiles/Broma-por-un-mp3.zip) <- I can't extract it, for example; is anyone able? Should I install any other package beside unzip? Could it be because of running on Dapper?

---

### Post by joft on 2006-02-12
Hi,

did you install the package "unzip" and/or the package "zip"? I think GNOME's Archive Manager (file-roller) uses one of them ...

---

### Post by Bou on 2006-02-12
yep, both of them are installed.

---

### Post by alfotis on 2006-02-12
Try to install other zip packages (maybe you need to add the multiverse and restricted repository in /etc/apt/sources.list or synaptic options - whatever you use...)

---

### Post by Spano on 2006-02-12
from the terminal I used -

$ unzip /home/daniel/Broma-por-un-mp3.zip

Opened fine.  
If you know how to install from source you might try this program
  [http://xarchiver.sourceforge.net/](http://xarchiver.sourceforge.net/)
it's opened everything I've come across.

---

### Post by Bou on 2006-02-12
[QUOTE=Spano]from the terminal I used -

$ unzip /home/daniel/Broma-por-un-mp3.zip

Opened fine.[/QUOTE]

It opened alright. So, why doesn't fileroller open it then, if the codecs are there?

---

### Post by Spano on 2006-02-12
> It opened alright. So, why doesn't fileroller open it then, if the codecs are there?
That I don't know.  I have had problems with fileroller in the past as well.  I get the best results using terminal to open .tar .zip .rar files.  If you type in terminal "man unzip" you will get instructions on how to issue the commands (type "q" to exit).
Or you can google for commands.  When you type my examples don't use quotes.
Next time can you give me a porn.zip to try opening?

---

### Post by Bou on 2006-02-12
[QUOTE=Spano]Next time can you give me a porn.zip to try opening?[/QUOTE]

LOL I'll try man :-D

I like the graphical way, but I'll do an exception with fileroller.

---

