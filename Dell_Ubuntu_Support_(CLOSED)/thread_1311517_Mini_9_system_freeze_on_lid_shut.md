---
title: "Mini 9 system freeze on lid shut"
date: 2009-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by slugicide on 2009-11-02
Hey,
I installed UNR 9.10 on my brand new Mini 9, and now when I shut the lid, or rather, when I open the lid after shutting it the whole system freezes. It kind of ruins the whole point of a netbook. Any idea of what's going on?


Edit: the system also freezes whenever Hibernate is activated from the keyboard.

---

### Post by slugicide on 2009-11-02
Any advice?

---

### Post by kristo5747 on 2009-11-03
> **slugicide said:**
> Hey,
I installed UNR 9.10 on my brand new Mini 9, and now when I shut the lid, or rather, when I open the lid after shutting it the whole system freezes. It kind of ruins the whole point of a netbook. Any idea of what's going on?


Edit: the system also freezes whenever Hibernate is activated from the keyboard.


Had the same problem with mine (Mini 10). 

Power Management-->>Suspend->Do nothing.
[COLOR=White]Power Management[/COLOR]-->>close lid->Do nothing.

I agree: ruins the purpose of a  netbook. At least, it no longer freezes.

---

### Post by AMCYEL on 2009-11-13
Curious how this is considered Solved. Nothing was solved, this is just a workaround that is costing valuable battery life. I either have to shut it down entirely if I want to keep it close at hand, or leave it plugged in if I decide to close the lid and walk away for an undetermined amount of time. Is there no actual update or anything the peeps behind ubuntu can do to actually solve this?

Is there a specific area in these forums where such things are put to light for those that are working on the OS and it's updates? (Or is this a user forum only?)

---

### Post by thornbeck@glwb.net on 2009-11-14
I am having the same issue on my Mini 9 and the full version of 9.10.  Here is a link to the bug reporting site and this actual "confirmed" bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/353387](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/353387)

If you can contribute, please do so.  Otherwise, you can just watch the bug for a solution.

Thanks,

Tim

---

### Post by Sonomaa on 2010-02-20
I was having the same issue of my mini 9 freezing on hibernate with Ubuntu Netbook Remix, either when I closed the lid or selected it. I found it tied to having an SD card mounted. If you remove the card it hibernates no problem. Someone on the bug page said they set their SD to a ext file system. I erased my SD card and reformatted it with an EXT4 file system, so far the problem has not returned.

---

