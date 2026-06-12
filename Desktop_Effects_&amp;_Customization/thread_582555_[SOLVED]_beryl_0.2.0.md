---
title: "[SOLVED] beryl 0.2.0"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by RuB3N on 2007-10-20
Where do i get beryl 0.2.0?
Is there a command for it?
The old beryl doesn't work on gusty....

---

### Post by FredB on 2007-10-20
> **RuB3N said:**
> Where do i get beryl 0.2.0?
Is there a command for it?
The old beryl doesn't work on gusty....

You don't need beryl. It is a dead project. Compiz Fusion is the next generation of Beryl, and it works great, even for me, a beryl "die-hard" user ;)

---

### Post by ravenus on 2007-10-20
Yes, CF does ALL the beryl stuff and more. make sure you get the compiz-fusion settings manager from Synaptic, so you can play around with all the effects :)

---

### Post by C64MAN on 2007-10-20
Hy All!

Thats ok that the Beryl is merged. I use the a compiz-fusion now. It works well, but what about the Beryl Manager, which always had a tray icon (and i used it many times). I found the program as CompizConfig Settings manager, but it can't run in the background.

Any idea?

THX

---

### Post by NoSmokingBandit on 2007-10-20
I was wondering the same thing, where is the beryl manager? Does it have to be installed separately like ccsm?

---

### Post by FredB on 2007-10-21
There is no need of the beryl manager. Compiz Config could be find in system / preferences / advanced desktop effects settings.

---

### Post by NoSmokingBandit on 2007-10-21
but that doesnt support themes like beryl does.

---

### Post by FredB on 2007-10-21
> **NoSmokingBandit said:**
> but that doesnt support themes like beryl does.

What about emerald and its theme ? Beryl was the core, and emerald managed themes...

---

### Post by klikko on 2007-10-21
You mentioned the old beryl tray icon?

Install *fusion-icon*
It acts just like the beryl icon, with window manager options and the Settings Manager available at a click. Very very useful.

---

### Post by C64MAN on 2007-10-21
Yes i mentioned the beryl icon which always run on the tray.

I searched for fusion-icon, but i didn't found in synaptic. Where can i found it?

---

### Post by NoSmokingBandit on 2007-10-21
> **FredB said:**
> What about emerald and its theme ? Beryl was the core, and emerald managed themes...

Aha! Thats what i was thinking of. Thanks a ton. I'll go install Emerald now.

---

### Post by C64MAN on 2007-10-21
Yes, you can install the emerald from synaptic.

And what about the fusion-icon???

---

### Post by NoSmokingBandit on 2007-10-21
If i remember right, the Compiz-Fusion icon in the notification area is nothing more than a launcher for ccsm, but i may be wrong.

---

### Post by C64MAN on 2007-10-21
With Beryl-manager you could make some instant option with right click, which was very useful.

---

### Post by bengoza on 2007-10-21
I couldn't find fusion-icon in synaptic either, nor do I have "advanced desktop effects settings" under system / preferences. And, yes, Synaptic says I have compix-fusion installed.

---

### Post by NoSmokingBandit on 2007-10-22
if you want the "advanced settings" option you must install compizconfig-settings-manager from synaptic. For some reason the developers didnt think most users would want that standard in gusty...

---

### Post by _simon_ on 2007-10-22
This deb was made for Feisty but may also work with Gutsy.

[http://ubuntuforums.org/showpost.php?p=3163821&postcount=8](http://ubuntuforums.org/showpost.php?p=3163821&postcount=8)

I compiled my own icon but can't remember where I found the source.

---

### Post by C64MAN on 2007-10-22
That package works for me. Thanks a lot! (A small problem with it: it hasn't got an icon. It just a plain area on the notification area, but it works well. :))

---

### Post by bengoza on 2007-10-23
> **NoSmokingBandit said:**
> if you want the "advanced settings" option you must install compizconfig-settings-manager from synaptic. For some reason the developers didnt think most users would want that standard in gusty...

Ah, yes. Got it all figured out now, thanks very much.

---

### Post by Kiyo86 on 2007-10-23
> **FredB said:**
> What about emerald and its theme ? Beryl was the core, and emerald managed themes...

Compiz-Fusion does support Emerald. All you have to do is install it. "sudo apt-get install Emerald"

Then go into the terminal and use the replace command to start up Emerald as the windowmanager.

---

### Post by NoSmokingBandit on 2007-10-23
to clarify for someone who doesnt know how to replace metacity with emerald: just hit alt-f2 and type 
```

emerald --replace

```
theres also a command to install quite a few emerald themes, but i forget what it is right now, ill post it if i remember.

---

### Post by rundee_f on 2007-10-23
guys help...

im still using feisty, and i already install compiz-fusion, but it didnt work at all.. and eventually when i typed "compiz --replace" on Alt-Tab,, my window title bar disappeared!! oh no... help... dunno what to do... :(

---

### Post by rundee_f on 2007-10-23
in addition,, my desktop also cant rotate, cant perform desktop cube, and everything else that i can easily done in beryl...

---

### Post by C64MAN on 2007-10-24
Install compizconfig-settings-manager and emerald from synaptic. Than install the package what was linked here few days ago. After that you will have a window manager, and you can change the compiz's settings.

---

### Post by rundee_f on 2007-10-24
yups!! i got it!

my case is solved at [http://forlong.blogage.de/#blogentry_451](http://forlong.blogage.de/#blogentry_451)..

thank you for your answer guys! :D

---

