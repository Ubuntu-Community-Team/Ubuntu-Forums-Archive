---
title: "Sound Card"
date: 2005-11-10
forum: Desktop Environments
---

### Post by seismicmike on 2005-11-10
I have no sound card apparently.


I don't think esd is configured right...

help...

---

### Post by RAOF on 2005-11-10
Some more details would be useful.  Such as:
[list]
[*]Is sound working for anything?  
[*]What error messages (if any) are you getting?
[*]What **is** your soundcard?
[*]Are the modules for the soundcard loaded/what modules are loaded? (you can get the list by running "lsmod" from a console)
[*]Have you checked that your soundcard volume is not muted? (You can run "alsamixer" from a console)
[/list]

---

### Post by seismicmike on 2005-11-17
Ok... it randomly decided to work today...

though it won't play mp3 :(

---

### Post by az on 2005-11-17
MP3 is a proprietary format that you cannot distribute freely.  Look up on the wiki how to enable restricted formats

wiki.ubuntu.com/RestrictedFormats

---

### Post by seismicmike on 2005-11-17
Yeah, working on that... i'm behind a proxy right now, so I can't apt-get anything

i'll have to do it at home

---

### Post by az on 2005-11-17
[QUOTE=seismicmike]i'm behind a proxy right now, so I can't apt-get anything

[/QUOTE]
?

apt-get uses http.  Is this a bandwidth thing?

---

### Post by seismicmike on 2005-11-18
it must be... all i know is that when I'm at work or at school (each have a proxy), I cannot apt-get... At home (where we have no proxy) we can.

It could be post hoc ergo proptor hoc, but who knows?

---

