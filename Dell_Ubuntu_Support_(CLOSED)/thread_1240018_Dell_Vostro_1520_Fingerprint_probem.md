---
title: "Dell Vostro 1520 Fingerprint probem"
date: 2009-08-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x53x6ex69x67x67x65x72 on 2009-08-14
Hi
I tried to make My Dell Vostro 1520 's FingerPrint work according to this:
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

But testing fingerprint with "sudo tf-tool --acquire" says:
```
ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.
```

I'm using Ubuntu 8.04 (Hardy Heron).
What's the problem?
Thank You.

---

### Post by pvrm on 2010-03-12
I had the exactly same problem here! 
But I'm using the Ubuntu 9.10

---

### Post by Kixtosh on 2010-03-12
Have you figured out what hardware device your Vostro uses?
 
I have a Toshiba Portégé R205 ultra-light that I want to use with Lucid Lynx, when it's released. Anyhow, I want to be able to use the Fingerprint reader too. I followed the ThinkFinger link above, but that procedure only works with ThinkFinger. My Portégé uses the AuthenTec Inc. AES2501 (according to the Device Manager in Win XP), for which there is some useful information in these links:
 
[http://ubuntuforums.org/showthread.php?t=503928](http://ubuntuforums.org/showthread.php?t=503928)
[http://hardware4linux.info/component/15599/](http://hardware4linux.info/component/15599/)
[http://home.gna.org/aes2501/index_en.html](http://home.gna.org/aes2501/index_en.html)
 
If I am understanding the information correctly in the "hardware4linux" link, it would seem that support for this AuthenTec device improved substantially with the 9.04 Ubuntu release.

---

