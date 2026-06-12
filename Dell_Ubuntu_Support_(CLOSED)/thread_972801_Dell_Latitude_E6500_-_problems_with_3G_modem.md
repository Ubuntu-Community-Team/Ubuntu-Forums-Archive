---
title: "Dell Latitude E6500 - problems with 3G modem"
date: 2008-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tma_it on 2008-11-06
Hi,

I'm using Ubuntu 8.10 on my Dell Latitude E6500 which has a build-in Wireless 5530 HSPA Mobile Broadband Minicard Device. I'm unable to get this device to work. There's no /dev/ttyUSB0 and the status led is not on. The network manager shows 3 entries for the card but nothing happens when i choose one of them. I read that drivers are included in the latest kernel, but how do i get it to work?

Thanks in advance.

Best regards,
Thomas

---

### Post by fiendishlyclever on 2008-11-06
I installed ubuntu on my Dell Mini 9 in preference to the Windows XP install.  It took a fraction of the space of XP and ran much faster.  Unfortunately I had the same problem as the poster above with my internal 5530 hsdpa modem (Dell).

The modem was auto detected by Ubuntu and I was asked for my cellular provider.  I was unable to connect through any of the 3 entries that appeared.  One of the entries went through the process of trying to connect, the next 2 were useless and did nothing.

I would dearly love to abandon XP (which hogs most of my 8gb SSD) and install Ubuntu.  I bought this Dell Mini specially for the internal 3g and so it is important to me that it works.

Any one any ideas?

---

### Post by Yoke &amp; Chung on 2008-11-07
> **fiendishlyclever said:**
> I installed ubuntu on my Dell Mini 9 in preference to the Windows XP install.  It took a fraction of the space of XP and ran much faster.  Unfortunately I had the same problem as the poster above with my internal 5530 hsdpa modem (Dell).

The modem was auto detected by Ubuntu and I was asked for my cellular provider.  I was unable to connect through any of the 3 entries that appeared.  One of the entries went through the process of trying to connect, the next 2 were useless and did nothing.

I would dearly love to abandon XP (which hogs most of my 8gb SSD) and install Ubuntu.  I bought this Dell Mini specially for the internal 3g and so it is important to me that it works.

Any one any ideas?

Tried my Ubuntu 8.10 USB card on a friend's new Inspiron Mini, looks like same problem, the hardware is detected, but can't connect to the WWAN. 

I have searched around and seems like re-compiling the kernal is the only optio :/

See thread as follow:

[http://ubuntuforums.org/showthread.php?t=941079](http://ubuntuforums.org/showthread.php?t=941079)

Regards

---

### Post by fiendishlyclever on 2008-11-07
> **Yoke & Chung said:**
> Tried my Ubuntu 8.10 USB card on a friend's new Inspiron Mini, looks like same problem, the hardware is detected, but can't connect to the WWAN. 

I have searched around and seems like re-compiling the kernal is the only optio :/


I sadly came to that conclusion after an evening of fiddling.  I'm not that big of an Ubuntu fan-boy (and I lack the Linux technical knowledge) so I gave up and reinstalled windoze XP.  I'll keep an eye on the forums and will maybe try again when a fix for this problems arrives.

As I said it's a shame because the rest of the system outperformed windows XP in every way (and was a pleasure to use).  If the 3g connectivity hadn't been so important to me I would have kept Ubuntu installed.

Let's hope someone cracks the Dell 5530 HSDPA modem driver problem and I can rid my machine of XP once and for all :-)

---

### Post by steve_d on 2008-11-21
[http://ubuntuforums.org/showthread.php?t=941079&highlight=hsdpa](http://ubuntuforums.org/showthread.php?t=941079&highlight=hsdpa)

Some success here in the forums

---

### Post by fiendishlyclever on 2008-11-22
> **steve_d said:**
> [http://ubuntuforums.org/showthread.php?t=941079&highlight=hsdpa](http://ubuntuforums.org/showthread.php?t=941079&highlight=hsdpa)

Some success here in the forums

Unfortunately that is the thread that is referred to earlier in this sequence.

As I said earlier, I'm not interested in fiddling and spending ages getting it to work when it does so flawlessly under XP.  I've taken a performance hit and reinstalled XP on my netbook.

I continue to monitor Ubuntu forums and bug reports for an easier solution :-)  (but thanks anyway)

---

