---
title: "Curious:  32 bit vs. 64 bit versions of Ubuntu"
date: 2014-10-26
forum: Desktop Environments
---

### Post by michael-piziak on 2014-10-26
I'm using Ubuntu 12.04 LTS  32 bit.  I tried 14.x, but that version didn't work as good on my particular system, so I went back to 12.04 LTS 32 bit.

I'm curious.  What would the 64 bit versions speed up for me?  I mostly use the system to watch youtube movies, use Gimp, and email.   My computer is an Intel Core 2 Duo with 4 gigs ram and around a 2.8 ghz processor.  When I use system monitor, it reports that both of my chips are working together as it is - usually each chip is working at 50% capacity during videos.

---

### Post by yancek on 2014-10-26
If you're not having problems with a 32bit system there is no reason to change.  An average user generally won't notice the difference between a 32/64bit system.  A 32bit system will not be able to access more than 4GB memory but a 64 bit will.  You can run 32bit on 32bit hardware and on 64bit hardware.  You can not run 64bit software on 32bit hardware.  The link below has a more detailed explanation. 

[http://www.computerhope.com/issues/ch001498.htm](http://www.computerhope.com/issues/ch001498.htm)

---

### Post by Impavidus on 2014-10-27
64 bit can simply use more than 4GiB memory. 32 bit can address at most 4GiB, some of which is reserved for other purposes than memory, so it can only use about 3GiB of memory. There is a hack, called PAE, which allows a 32 bit system to use more than that 3GiB of memory. Apart from Xubuntu 12.04, all currently supported Ubuntu flavours come with PAE enabled. But even with PAE, avery individual application is still limited to 4GiB total address space.

As your total memory is 4GiB, there is little benefit from moving to 64 bit. Watching youtube is usually limited by network speed, monitor resolution or processing capacity of your eyes and brain. 64 bit has some speed advantage, but in most cases not enough to notice. Gimp shouldn't be very heavy on resources, unless you process 200 megapixel images. Email worked fine on computers 20 years ago, system requirements haven't changed much.

---

### Post by grahammechanical on 2014-10-27
But what graphic adapter do you have? How powerful is it and how much of its own memory does it have? Another question. Applications may run on a 64 bit OS but do they make full use of the 64 bit OS? Or are they 32 bit applications that have been re-written to run on a 64 bit OS without taking full advantage of the 64 bit architecture?

Regards.

---

