---
title: "[SOLVED] ZSNES Crashing.. Sadness Ensues"
date: 2007-11-30
forum: Gaming &amp; Leisure
---

### Post by k1dicarus on 2007-11-30
Okay, my ZSNES was working like a charm just after I upgraded to Gutsy and for a while afterwards.. but lately, the program is crashing before I can even use it. The window pops up.. it's all black.. and about one second later it's gone. So, I tried running it from the terminal, and here's what I get:

kidicarus@pit:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/kidicarus/.kde/socket-pit.
can't create mcop directory

That last part looks bad.. I dono..
Any help would be amazing.
Thanks, folks.

---

### Post by subs on 2007-11-30
this is pretty common problem with zsnes.... 

try making the folder in question urself...

---

### Post by BigSilly on 2007-11-30
Yeah it's a common problem on Gutsy for some crazy reason. It's easily fixed though. Have a search around on this forum and you'll find an easy solution. I got this one from here and it worked for me -

```
mkdir ~/.kde/socket-`hostname`
chown -hR `id -n -g` ~/.kde
chmod 755 -R ~/.kde
```

It's just missing a directory it needs, and you can just create it yourself, which is all that does above. Let us know if this works.

---

