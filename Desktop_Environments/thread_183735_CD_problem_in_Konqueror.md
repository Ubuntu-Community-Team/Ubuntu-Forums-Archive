---
title: "CD problem in Konqueror"
date: 2006-05-28
forum: Desktop Environments
---

### Post by isaacf on 2006-05-28
Everytime I try to view the contents of a CD in Konqueror it gives me a "malformed URL" error and won't let me do anything with it. Any help is greatly appreciated.

---

### Post by isaacf on 2006-05-29
I tried viewing the contents of other CDs I had. No blank CDs go through without the "Malformed URL error." Other linux install CDs I have lying around show up fine and playstation disc which I'm trying to read to play them with epsxe don't even register with kubuntu.

---

### Post by emretemp on 2006-07-10
I also get this msg whenever I insert a new DVD into my dvd driver. 

simply confused here. 

anyone knows what todo?

---

### Post by oliwally on 2006-07-19
> Everytime I try to view the contents of a CD in Konqueror it gives me a "malformed URL" error
I have the same problem with a data DVD that I've burned although it didn't consistently fail - one time it opened.

I found that that if I "create a new link to a device" and make that device a DVD Rom device on the Desktop, then I can access the data on the DVD though that link. 

I've noticed that if I try to open the DVD with the automatic function that comes up when the DVD is inserted, then Konqueror uses the following path:
system:/media/hdd    and often the "malformed URL" error message.
But if I open the DVD through my newly created link to the DVD device (wich works consistently), then the path is this:
/media/cdrom0

Not sure what the problem is or how to fix it, but at least there is a workaround. I wonder if Konqueror needs to be pointed to the DVD device in a different way. Some setting that can be adjusted for auto-opening the data DVD?

---

### Post by NiksaVel on 2006-09-12
was this problem ever fixed... I just started having it a few days ago and noticed that there are quite a few posts on this topic... just search for "malformed url" in these forums...

---

