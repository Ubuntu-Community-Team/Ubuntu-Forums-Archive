---
title: "Ease of installing windows drivers?"
date: 2008-12-14
forum: General Help
---

### Post by Sup3rkirby on 2008-12-14
I suppose this isn't an ubuntu specific question, but this is the only linux forum I am a part of.

My father has an old PC at his house that would probably need to run Xubuntu if I wanted linux on it(and I do). The thing is, this PC is so old that it does not have ethernet ports, therefore, the only way it can connect to the internet is by using the modem's USB connection, which requires drivers.  Since this method is far less used, it is very unlikely any linux development has been done for modem USB drivers.

I was wondering what would be the best and easist way to get something like this working?  It is a westell modem, which drivers can be found on the AT&T website(win32 drivers are only available).

I was curious as to what all Wine was capable of, for instance, can it open up Windows binary files(kind of like a default app for opening files), and then run the driver installation?  Would it actually install the drivers to a working condition for Xubuntu?


I know this is rather general linux help and probably a very rare question as most people have ethernet ports(and you can buy USB to ethernet and vice versa).  But he is just going to use that PC until next year, when he gets a new one. XP runs terribly slow on it and it isn't very secure.


Thank you in advance for any help.

---

### Post by blazemore on 2008-12-14
Sorry dude, can't be done.
Windows drivers are Windows drivers.

You know how you can't play a PS2 game on an Xbox? Well it's like that.

---

### Post by karlr42 on 2008-12-14
Er, [Ndiswrapper?](http://en.wikipedia.org/wiki/NdisWrapper)

---

### Post by Sup3rkirby on 2008-12-14
Well, I know about ndiswrapper, but would this be easy.  Honestly, I don't know.  I've only used ndiswrapper once, a few years ago when I first tried ubuntu and I was trying to get a wireless adapter to work.  I had a full set of instructions so it was more read and react rather than actually knowing what i was doing.

And of course one of the thoughts now is, the driver from the site, is this an .exe or the actual driver? I know ndiswrapper requires the driver file itself, so it can't be bundled inside of an executable.

I suppose I can give ndiswrapper a try, but I doubt it will be easy.

---

### Post by karlr42 on 2008-12-14
I found this:
[http://www.ubuntuhcl.org/browse/product+westell-versalink-327w?id=126](http://www.ubuntuhcl.org/browse/product+westell-versalink-327w?id=126)
So it's possible drivers are included for your modem already. Nowadays most of them are, every single piece of equipment I've ever plugged in has been detected and worked.
Try run a LiveCd on the PC and test the modem.

---

### Post by hikaricore on 2008-12-15
lol

---

### Post by TeXtonyx on 2008-12-16
Some of the old modems were called WinModems becaused they used
part of the Windows OS to function. They of course made modems
that worked with Linux. I suggest you install a compatible (USR)
Linux internal modem. They should be cheap and work well for email.
You should also be able to add an ethernet port card for $12-15.

---

