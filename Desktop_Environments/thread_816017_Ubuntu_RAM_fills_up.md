---
title: "Ubuntu RAM fills up"
date: 2008-06-02
forum: Desktop Environments
---

### Post by chandlerC on 2008-06-02
Hi guys,

I just upgraded my Ubuntu 6.06 Dapper to 8.04 Hardy. I was very happy with it for a few hours until it started to slow down and use the HDD for minutes. I realized it was out of RAM and it was using almost 1 gig of swap. I rebooted it. It was fine, but after a few hours of settings, installing some software from the reps, and some internet browsing the machine became super slow again and the Ram was full again and the swap was going up. I closed everything but it remained like that and after some time it just froze completely.
It happened 3-4 times in one day. 

The machine is HP DV2000 laptop with 1Gig of Ram and 1 Gig of Swap Space. Gnome 2.22.2
2.6.24-17 kernel
Intel 1.73 Cpu

 Before it uses the whole RAM space it is super fast. For some reason it just fills up the RAM and Swap until the machine locks up... I used just 1-2 browsers, RhythmBox player, Open Office and Quanta Plus , the last time when it froze. 

If someone can help me, I'll be very thankful!

thanks!

cj

---

### Post by mcduck on 2008-06-02
Next time the RAM starts to fill up open a terminal and run "top" to check what program is eating all your memory. (Well, of course you could just use the System Monitor application as well).

---

### Post by chandlerC on 2008-06-02
Actually whatever I close no RAM is freed, even when the machine is ot of Ram and it uses the Swap, and thus when I open and close applications and gradually grows up, and slows the machine down. That's why i don't think it is problem with particular application....

---

### Post by perlluver on 2008-06-02
> **chandlerC said:**
> Actually whatever I close no RAM is freed, even when the machine is ot of Ram and it uses the Swap, and thus when I open and close applications and gradually grows up, and slows the machine down. That's why i don't think it is problem with particular application....

Memory is used differently in Linux, as in my case I start out about 128 used and in a couple of hours after using it, it is up to 498MB out of 512.  Things are stored in a sleeping state so that they will start up faster if you need them again.

---

### Post by tribaal on 2008-06-02
See link in my signature :)

- Trib'

---

### Post by chandlerC on 2008-06-02
> **perlluver said:**
> Memory is used differently in Linux, as in my case I start out about 128 used and in a couple of hours after using it, it is up to 498MB out of 512.  Things are stored in a sleeping state so that they will start up faster if you need them again.

that absolutely makes sense, but it doesn't make sense when i'm out of ram the machine to keep piling up in the swap until it gets full and the machine crashes with just 2-3 applications opened...

---

### Post by chandlerC on 2008-06-02
> **tribaal said:**
> See link in my signature :)

- Trib'

yeah, the article brings more light into the subject. I'll try that when I get home tonight... I'll keep you posted...

---

