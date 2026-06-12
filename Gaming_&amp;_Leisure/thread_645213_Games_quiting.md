---
title: "Games quiting"
date: 2007-12-19
forum: Gaming &amp; Leisure
---

### Post by LostMagix on 2007-12-19
When i start a game such as alien arena i can get into the game, get into the battle but after about 30 seconds of playing it will quit on me

any idea what would be causing this?

---

### Post by cogadh on 2007-12-19
Not without a lot more information, like some hardware specs to start.

---

### Post by LostMagix on 2007-12-19
503.7 MB RAM 

AMD sempron 3000+

ATI radeon 9550XL 256MB

---

### Post by LostMagix on 2007-12-19
ubuntu 7.10 gutsy

---

### Post by cogadh on 2007-12-19
Which drivers are you using for your ATI card? I just read something about one of the newest drivers having a moderate to severe memory leak that might present itself like this:
[http://ubuntuforums.org/showthread.php?t=644471](http://ubuntuforums.org/showthread.php?t=644471)

---

### Post by acoustibop on 2007-12-20
That's very strange.  Someone's claiming that games are bound to crash after 20 minutes to an hour - but I can play for hours with no problems on the current 7.11 driver.  I'm sure that such a major problem would have garnered much more recognition by now; the 7.11 driver has been out for nearly a month now.

It's possible there may be a memory leak (I've had no experiences with this driver that would suggest this, though) but it can't be very major.

Usually, a game crashing as quickly as LostMagix's would indicate either he's hitting some procedure in the game that his drivers (likely video, but may be something else) can't handle, or severe overheating problems - most likely the videocard, but possibly the CPU.

---

### Post by aoanla on 2007-12-20
> **acoustibop said:**
> That's very strange.  Someone's claiming that games are bound to crash after 20 minutes to an hour - but I can play for hours with no problems on the current 7.11 driver.  I'm sure that such a major problem would have garnered much more recognition by now; the 7.11 driver has been out for nearly a month now.

It's possible there may be a memory leak (I've had no experiences with this driver that would suggest this, though) but it can't be very major..

The memory leak, which is well documented in a thread on the Phoronix forums, and is confirmed to be in the Catalyst 7.11 driver, only occurs in render paths used for later ATI cards (this gen and last gen, as far as anyone can tell). 
If you have an older ATI card, there is no memory leak.

---

### Post by cogadh on 2007-12-20
I'm not too familiar with the current generations of ATI cards, is LostMagic's 9550XL one of them? I know it's not listed as a legacy product on ATIs website, but that doesn't mean much.

---

### Post by acoustibop on 2007-12-20
The 9550 is one of the earliest cards that will run the current fglrx driver.  So, no, from what aoanla says, this would not affect the OP's card or my 9800 XT - and this bears out my experience with the driver.

---

### Post by cogadh on 2007-12-20
Okay, so we can forget the memory leak as a cause of the problem. The overheating issues you brought up are an interesting possibility. I know you can get processor temp info from the system, but what about the video card? Nvidia has a temp monitor built into the driver settings application, does ATI have anything similar? Or is ATI's hardware compatibile with the system temp monitors (I know Nvidia isn't)?

There is also the possibility of a conflict with some other running application, such as Compiz. It would help to know if that is running when the games are launched.

---

### Post by LostMagix on 2008-02-03
Its not over heating i know that, i have a fan pointed right at it.

---

