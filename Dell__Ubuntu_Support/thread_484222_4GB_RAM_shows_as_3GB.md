---
title: "4GB RAM shows as 3GB"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by udaykdk on 2007-06-25
Hi all,

 I have recently installed Ubuntu Edgy on a Dell Optiplex 745 which basically has a Core2 Duo 2.4 GHz processor and a 4GB RAM. However, when I open up the system monitor, I can see only 3GB of system RAM. Is this a known issue? Any solutions that people might know of?

Thanks in advance,
 Uday

---

### Post by apel_2804 on 2007-06-25
what a graphics card?

---

### Post by Trebaruna on 2007-06-25
Yes, you need to run either 64 bit Ubuntu, or recompile the 32 bit kernel with a patch to enable extended memory support (or whatever it's called).

The thing is, yesterday I'd found a very promising thread on these very forums which dealt with this issue, but I can't quite find it anymore. I am also trying to find out how to make it work ;)

I do not recommend running 64 bit, because hardware support and development are not quite as far along as 32 bit, and you need to put some more effort into it. On the other hand, compiling your own kernel takes some time and work. There's also a HowTo on that somewhere on the forums, though.

Afraid all I can say is search the forums and try and get some answers. At least you know now that it is a known issue and that there isnt specifically anything wrong with your computer. Hopefully someone else can help you along further.

EDIT: Just to explain a bit: 32 bit means you cannot have more than 4GB of RAM (2 to the power of 32 is 4GB), and because your BIOS, graphics card and other devices also claim memory, the amount of usable RAM is less than that. The patch I mentioned actually extends the address range to 36 or 40 or so bits (at least, that's what I gather), which will allow for a lot more memory.

---

### Post by apel_2804 on 2007-06-25
Trebaruna is right, it's nothing wrong with your system!

---

### Post by clikc on 2007-06-25
Just agreeing with everyone else, its a restriction of a 32 bit os, reguardless of windows or linux os's you will have this issue, it will still utilize all 4 gigs of memory but will only show as 3 or 3.2 there are work arounds that i have heard of that will show 4 gigsbut this is a known issue. :popcorn:

---

