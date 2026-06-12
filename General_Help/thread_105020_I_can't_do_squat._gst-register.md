---
title: "I can't do squat. gst-register"
date: 2005-12-17
forum: General Help
---

### Post by SZF2001 on 2005-12-17
OK... So I've successfully installed Ubuntu in my other computer - this computer is not really meant for games or internet browsing (but I'll be doing that someday). It's more for music and when I'm writing papers and such.

But the thing is... I can't open most of my programs for crap. It keeps asking me if I've run "gst-register"... Does this mean I'll have to connect to the internet? Or is my whole system corrupt? Hopefully someone will know and it's probably a n00b question and all...

**(This has been answered, the new question is my next post)**

---

### Post by amohanty on 2005-12-17
If you have installed all the codecs and stuff at the command line just to :
```
gst-register-0.8
```

and you should be good to go.
HTH
AM

---

### Post by BathroomNinja on 2005-12-17
if it doesnt run, then use:

sudo gst-register-0.8


You need to run this from the terminal.

---

### Post by SZF2001 on 2005-12-17
Oh yess! Thanks you guys, I got things runnin'.

But now I have a new question...

So, I'm trying to install [Xine](http://xinehq.de/) onto Unbutu.

But... I have no idea where to start. And their FAQs don't really even help. I went into the download section and downloaded xine-lib-1.1.1.tar.gz, but when I run it on Unbutu, I have no idea what in the hell I'm doing.

---

### Post by Kevinator on 2005-12-17
Xine is in the Ubuntu software repositories. All you need to do is run Synaptic (in the System -> Administration menu) and select it for installation. You may have to enable some extra repositories first.

---

### Post by SZF2001 on 2005-12-17
Holy cow... You guys are my heros.

If I could hug you, I probably would, considering if you smell alright...

---

### Post by SZF2001 on 2005-12-17
Uhm... Synaptic couldn't find it.

*I* couldn't find it either.

---

### Post by aysiu on 2005-12-17
[QUOTE=SZF2001]Uhm... Synaptic couldn't find it.

*I* couldn't find it either.[/QUOTE] See the first link of my sig.

---

### Post by SZF2001 on 2005-12-17
Eh... Even after following your tutorial, it still doesn't have it.

---

### Post by amohanty on 2005-12-17
If you follow aysiu's tutorial and setup universe repos and then search for **totem-xine** you should find it. Look at the screenshot attached in aysiu's post. 

If you still cant find it, post the contents of the following file: /etc/apt/source.list

AM

---

