---
title: "Guitar Pro 5"
date: 2009-04-11
forum: General Help
---

### Post by drummerchrissk on 2009-04-11
Hi,

    I have installed Guitar Pro 5 on my Compaq Armada E500 laptop running Ubuntu. Nothing in this laptop has been changed save for the 12 GB hard drive (now 20 GB) and the CD-ROM drive (now a DVD-ROM). Guitar Pro opens fine. I can tune my guitar, look through tabs, edit tabs, etc. However, when I go to play a tab, the results are extremely choppy. It almost sounds as if a heavy reverb and tremolo has been placed on the tab. I have Timidity installed as well and all my tabs are being run through Timidity port 0.

    My question is if there's a way to get rid of the choppy tab. I'm wondering if it's due to the fact that I'm using software MIDI instead of hardware MIDI.

    Please help!

    (P.S. I have tried TuxGuitar and found that it plays the tabs without too much trouble, but it tends to lose tempo if that makes sense. It will change speed between notes or measures.):guitar:

---

### Post by geraldm on 2009-04-11
There are two factors in being choppy;
1. The buffers fill up, and are emptied too soon, before they are filled up again.
2. Low latency.  This is a special kernel, in which an application is serviced, and  then control goes to other programs, before returning to this application.
Music enthusiasts have developed a special low latency settings in the kernel so that there is a short interval between servicing an application rather than a longer "normal" kernel.

You might look into extending the buffers in length or number if the programs allow such settings.  If that does not work, then look into using a low-latency kernel.

regards,
Gerald

---

### Post by drummerchrissk on 2009-04-12
I have tried increasing the buffer before. I had increased it quite a bit if I remember correctly. And it worked. But only for a very short time. After about a measure and a half or so, the sound stopped completely while the tab kept scrolling as if it were still playing. The only way to get it to play sound again was to stop the tab, and then start it again. However, the same problem would happen again and again.

As I said, I'm pretty sure I had increased the buffer to the max, just to see what it did. I wasn't quite so sure what it was (and am still not %100), and was just tweaking what I could to see if I could get lucky. I really am quite a newbie at most of this stuff. :)

Hopefully, tommorow I will get the chance to mess with this buffer setting again and get my Guitar Pro running as it should be.

Also, you mentioned a low-latency kernel. What exactly does this mean? How will it help me with Guitar Pro? And if possible, where might I be able to get a low-latency kernel?

Thanks for the quick response.

Happy Easter!

---

### Post by geraldm on 2009-04-12
You may have to search a bit for more information on the low latency kernel.
Here is some information on the Intrepid Real Time kernel package
[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-3-rt](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-3-rt)

Basically, using this type of kernel services its applications more quickly than a normal kernel, so the buffers would not get drained to depletion.
Look for the package in the repositories.

regards,
Gerald

---

