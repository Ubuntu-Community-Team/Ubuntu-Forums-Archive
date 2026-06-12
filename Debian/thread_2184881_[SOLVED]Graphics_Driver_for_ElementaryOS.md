---
title: "[SOLVED]Graphics Driver for ElementaryOS"
date: 2013-10-31
forum: Debian
---

### Post by digitalmetis on 2013-10-31
Hi! I'm not having much luck getting a reply to my question in the eOS community, so I've come here for some tech support.

I want to try and install the proprietary graphics driver in the Pantheon desktop. My video card is called an ATI Mobility Radeon HD 4250. The driver tool show's results for installing a ATI/AMD proprietary FGLRX graphics driver. If I install this and can't boot the kernel, what should I do?

Thanks in advanced.

---

### Post by Stinger on 2013-10-31
I would recommend you use the open source ATI radeon driver as I do, it's really working well for my radeon hd 4670.
I don't know about the power consumption though, might be a problem, yours is a Mobility Radeon HD 4250 ( laptop ).

Have a look at your possibilities on [this thread]("http://ubuntuforums.org/showthread.php?t=2184725") :)

---

### Post by neu5eeCh on 2013-10-31
> **digitalmetis said:**
> Hi! I'm not having much luck getting a reply to my question in the eOS community, so I've come here for some tech support.

I want to try and install the proprietary graphics driver in the Pantheon desktop. My video card is called an ATI Mobility Radeon HD 4250. The driver tool show's results for installing a ATI/AMD proprietary FGLRX graphics driver. If I install this and can't boot the kernel, what should I do?

Thanks in advanced.

First, [go to this page]("http://askubuntu.com/questions/78675/how-do-i-remove-the-fglrx-drivers-after-ive-installed-them-by-hand"), and print it out.

Then...

Install the drivers. If you end up at a blank screen, then reboot. The next time you see the Elementary Splash Screen, try getting into a TTY session. CTRL+ALT+F1 or F2 through F6. F7 is your X session.

Once there, follow the instructions on the print out to restore your OpenGL drivers.

---

### Post by Bashing-om on 2013-10-31
et all;

Seems "digitalmetis" is in this boat and has no current recourse but to run the open source driver.
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

If the OP is running version 12.04.1 - has the older kernel - then yeah, can use the proprietary drivers.

A shame but;
[INDENT][INDENT]that's the way it is
[/INDENT][/INDENT]

---

### Post by digitalmetis on 2013-10-31
Thanks guys. It's no big deal if I can't use the driver. Everything is working so far with the opensource driver. I'm more of a console gamer, so if I can't play games, that's okay. I was just hoping for a performance boost. Speaking of which, I can't wait to try the next release of Pinguy.  They seem to have put a lot of effort into making it run fast.

---

### Post by Stinger on 2013-10-31
You are welcome. :)
For the record, I'm having better performance with the open source driver on Elemetary now than I had earlier when I used the fglrx driver from AMD.
I think the open source ati driver is the right one for you, the fglrx driver from AMD is having trouble with tearing in video playback.

---

