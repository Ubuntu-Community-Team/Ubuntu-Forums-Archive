---
title: "nVidia GeForce 8300 GS Restricted Driver Instability - Replacement Recommendations?"
date: 2008-02-17
forum: Dell  Ubuntu Support
---

### Post by Simon G Best on 2008-02-17
I just want to rant about the instability of the restricted driver for the nVidia GeForce 8300 GS that came in my Inspiron 530n.

Recently, it's started occasionally crashing when I change desktop workspace using the pager in Xubuntu.  It now seems to be crashing quite frequently.  It's really annoying, as I've usually got several windows open at the time, with stuff going on.

I've also noticed that Flash sometimes hangs Firefox.  The connection?  Both Flash and the restricted nVidia driver are closed-source.  It usually seems to be closed-source software that has the worst stability problems.

Back to the restricted nVidia driver, I've also noticed that it has a potential security problem.  It often allocates display memory that's still got old contents in it.  Momentarily, you can see something of what was in that chunk of memory prior to it being reallocated.  It's not unusual for the visual contents to be recognisable.  This, I believe, is a potential security risk, as it's quite conceivable that the old contents could contain sensitive information.

(Imagine, for example, that you're examining the plans for a new battlestation.  Once you've finished, you close the window displaying those plans, and move onto something else.  Then someone, who is not authorised to see those battlestation plans, or even know of the existence of that project, comes by.  While they're standing behind you, watching your screen, you open a new window.  For a brief moment, but long enough to get a glimpse, the secret plans for the Death Star are revealed.  That's a breach of security.)

What I'd really like is a good replacement for this nVidia GeForce 8300 GS, *with a full-featured, fully Open Source driver.*  Does anyone have any recommendations?

I'm just fed up (again) with shoddy closed-source software.

Oh, and here's the tail end of the X server log:-

```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]
2: /usr/bin/X [0x817e389]
3: /usr/bin/X [0x817ad15]
4: /usr/bin/X(CompositePicture+0x153) [0x8161223]
5: /usr/bin/X [0x81674ff]
6: /usr/bin/X [0x8164425]
7: /usr/bin/X [0x815765e]
8: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
9: /usr/bin/X(main+0x495) [0x8076f05]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7daf050]
11: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting


```

---

### Post by SandmanCL on 2008-02-18
I don't have anything really useful to contribute to this post, but I wanted to chime in and share your frustration.

I also have an Inspiron 530 (not the 'n') with the 8300GS graphics card. If I have any visual effects turned on (System -> Preferences -> Appearance -> Visual Effects), Firefox will sometimes crash and there will be consistent problems with the text not updating properly when I scroll up and down. This at least occurs in Firefox, Thunderbird, xterm, and Anjuta, so I'm assuming it's consistent for all apps.

If I have Visual Effects set to 'None', the problem seems to be non-existent. 'Normal' and 'Extra' are equally bad.

Are there known issues with the 8300 that are not present with higher end cards ? I had contemplating going to the highest Nvidia card I could use without upgrading the PSU and if this problem would disappear by upgrading the decision might be easier...

---

### Post by Simon G Best on 2008-02-18
> **SandmanCL said:**
> Are there known issues with the 8300 that are not present with higher end cards ? I had contemplating going to the highest Nvidia card I could use without upgrading the PSU and if this problem would disappear by upgrading the decision might be easier...

I suspect it's more a matter of the restricted driver being closed-source.  The problem is with the driver anyway, rather than the card itself.

Also, I'm not going to be buying another nVidia card to "solve" this problem, as that would seem silly to me.  Firstly, it seems perverse, to me, to buy a more expensive card when the problem's with the driver.  Secondly, I'm not going to reward nVidia for providing a buggy, closed-source driver.

If the driver was open-source, we wouldn't be dependent on, and limited by, nVidia.  But it isn't, so we are.  The result is that the driver's only as good as nVidia believe is most profitable for them.  And, as usual with closed-source software, that means it's not as stable as it could be.

I think 530s come with an Intel GPU on the motherboard, anyway.  I haven't checked to see if mine is usable, but I might do that.  I'm hoping it's one which is fully supported by a fully open-source driver.  Then, perhaps, I'll just remove the nVidia card.

---

### Post by wild_oscar on 2008-04-22
I have the exact same random crashes.

Info:

Video card: Nvidia Geforce 8600 GTS
Ubuntu 7.10
X Protocol Version 11, Revision 0, Release 1.3


> Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]
2: /usr/bin/X [0x817e389]
3: /usr/bin/X [0x817ad15]
4: /usr/bin/X(CompositePicture+0x153) [0x8161223]
5: /usr/bin/X [0x81674ff]
6: /usr/bin/X [0x8164425]
7: /usr/bin/X [0x815765e]
8: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
9: /usr/bin/X(main+0x495) [0x8076f05]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d41050]
11: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting


---

### Post by Simon G Best on 2008-04-22
I just thought I'd finally get round to mentioning that since I deactivated "display compositing" in "Window Manager Tweaks" in Xubuntu, the instability problems have disappeared.

I'm not saying it's a fault in Xubuntu, though, as it was the X server that was crashing.  I still believe the problem's with the closed source nVidia driver.

---

