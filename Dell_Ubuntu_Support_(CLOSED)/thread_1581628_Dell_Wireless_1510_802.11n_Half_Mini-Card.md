---
title: "Dell Wireless 1510 802.11n Half Mini-Card"
date: 2010-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mpnordland on 2010-09-25
ok, I had installed a 32bit version of Karmic, and then upgraded to lucid, but, I have a Studio 1747 with an i7 processor, and I am dual-booting with Windows 7.
I like ubuntu, it is my main operating system, and whenld I realized that the reason Windows 7 seemed to perform better was that it was 64bit, I backed up my data, downloaded the 64bit version of lucid. Now, when I first installed ubuntu, the wireless worked great! but now it doesn't work at all :(. I have the proprietary drivers installed, like before, only now they don't work. I also had the proprietary Ati driver installed before, and now I don't, could that be the problem?
please rsvp.
ps. my wireless card is the one in the thread name

---

### Post by mpnordland on 2010-09-25
Also, my card reader isn't detected/doesn't work.
anything I can do for that?

---

### Post by mörgæs on 2010-09-25
Please post the output from

```
hwinfo --netcard
```

---

### Post by mpnordland on 2010-09-26
I have switched back to 32bit ubuntu, my wireless is working, and now ubuntu is peppier, so I guess my problem was the 64bit version, so i guess this thread is solved, though you might want to submit a bug about this.

---

### Post by mörgæs on 2010-09-27
Good. Please mark the thread 'solved'.

I am not going going to submit a bug report, first of all because I don't have your hardware, but if you do so, best is to test if the bug is also present in 10.10.

---

