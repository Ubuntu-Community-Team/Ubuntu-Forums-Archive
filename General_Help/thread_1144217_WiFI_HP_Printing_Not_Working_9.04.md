---
title: "WiFI HP Printing Not Working 9.04"
date: 2009-04-30
forum: General Help
---

### Post by bailunrui on 2009-04-30
I upgraded to 9.04 and among other issues I've been having, my wireless printing (HP Photosmart C4580) no longer works.

I can "discover" my printer in both the gnome and HP printer device managers.
I can ping my printer.
I have drivers for my printer.
I have upgraded to the latest HPLIP (even outside of the repo).

Yet my laptop insists that my printer is not connected and I cannot print documents that I send to it. They process seemingly forever.

Here is the latest error I've received trying to print:
Apr 30 15:23:32 QueenBitch Photosmart_C4500_series?ip=192.168.10.156: io/hpmud/jd.c 330: unable to connect to print port 9100: Connection timed out hp:/net/Photosmart_C4500_series?ip=192.168.10.156 

Any ideas? :confused:

**SOLVED**

I don't know what ultimately fixed my problem, since I tried a lot of things. But printing now works.

---

### Post by Polygon on 2009-04-30
seems like a support question aimed towards HP support....but i know that MY hp printer takes a super long time to print as well (like 2-3 minutes for it to finally print something, when intrepid it was basically instant)

is that line you posted from messages.log or something similar?

---

### Post by bailunrui on 2009-04-30
Well, under 8.10, my printing started almost instantaneously. I don't think this is an HP problem so much as a Linux problem.

What I posted was from messages.log.

---

### Post by Polygon on 2009-04-30
yeah i dunno, my hp printer is having problems too, i wonder if there is an option to increase the timeout time, cause maybe your printer is having the same issue as mine, and its just taking super long to connect...but it DOES work...

---

### Post by bailunrui on 2009-04-30
Perhaps. I looked around and didn't see a timeout option. I'll keep an eye out.

The weird thing is that my ping to the printer is very, very fast. :-/

---

### Post by bailunrui on 2009-04-30
I think it could be a JetDirect problem, but I'm not sure. I've tried foomatic and hpoj to no avail.:icon_frown:

---

