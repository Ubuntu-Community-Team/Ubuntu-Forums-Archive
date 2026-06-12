---
title: "Shift to 64 bit."
date: 2010-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vinu Raj V on 2010-09-10
Hi,

      I recently upgraded my Dell Inspiron 1440 from Ubuntu 9.10 to 10.04. Currently I'm running 32 bit Ubuntu. I was thinking about a change to 64 bit. 

By doing so, can I be able to do these things?

1. Play media files like mp3, avi etc.
2. Will there be drivers available for my wireless device       'Broadcom Corporation BCM4312 802.11b/g'.
3. Play flash videos in YouTube.

In case of media files, if codecs are not installed, a search option is available when clicking the media file in 32 bit OS by which I can install the codecs. Is this feature available in 64 bit OS?

Thanks in advance.

---

### Post by sikander3786 on 2010-09-10
How much RAM have you got? Using the 64-bit version doesn't give some greatly noticeable boost to the system.

1. You can play files like mp3, avi equally well on 64-bit.
2. Don't know
3. Flash seems to work sometimes while the other time, it crashes, hangs up etc. Means not equally well supported on 64-bit.

Installation of codecs process is the same in 32-bit and 64-bit.

You've got a working 32-bit system, I'll advise to stick with it unless you have got a very strong reason for switching to 64-bit.

Regards.

---

### Post by llawwehttam on 2010-09-10
I use 64 bit and flash is a nightmare. I would advise you to stick with 32 for now.

---

### Post by Vinu Raj V on 2010-09-10
My machine has 3GB RAM. I'll stick with 32bit until all my questions are cleared.

Thanks.

---

### Post by howefield on 2010-09-10
> **Vinu Raj V said:**
> can I be able to do these things?

1. Play media files like mp3, avi etc.
2. Will there be drivers available for my wireless device 'Broadcom Corporation BCM4312 802.11b/g'.
3. Play flash videos in YouTube.

In case of media files, if codecs are not installed, a search option is available when clicking the media file in 32 bit OS by which I can install the codecs. Is this feature available in 64 bit OS?

The answer to all your questions is yes, although as others have said flash might be your  biggest issue. The 64 bit version has been temporarily withdrawn meaning you would need to use the 32 bit version with nspluginwrapper. This works well for many people but not so for some. The only issue I had was with the button controls which was easily fixed by editing one file.

That said, if you have a working system, you'll probably not see a huge benefit from 64 bit. 

In any event, all you will get in this thread are opinions, you'll never know what works well on your machine unless you try it.

---

### Post by Vinu Raj V on 2010-09-11
With the help from the forum, I installed Broadcom drivers for 32bit Ubuntu in this way. 
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source

```
Is this how you do for 64bit?

I do audio production related tasks, because I really love them. Then I heard about Ubuntu Studio. Any suggestions on using 64bit Ubuntu Studio? 
What about media codecs, flash and wireless drivers?

---

### Post by beefone on 2010-09-12
> **Vinu Raj V said:**
> 
Is this how you do for 64bit?


Yes, as mentioned above, nothing changes in terms of installing and such. However, if you are going to have any issues it will most likely be flash related.

---

