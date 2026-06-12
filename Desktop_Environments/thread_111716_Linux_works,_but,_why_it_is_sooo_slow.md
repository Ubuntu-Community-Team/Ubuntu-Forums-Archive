---
title: "Linux works, but, why it is sooo slow?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by spier on 2006-01-02
I`m  used to use those nice computers  not for toy, but to do my job, basically, programming in java. Then my question... why it seems linux is soooo slow comparing with  windows? I have to wait an eternity  to get my desktop, just because my wifi? This makes no sense!  Is there a way to get my desktop _automatically_ right BEFORE my computer decide my wireless is (or not) ok? 

(forgive my wrong english)

---

### Post by ysse on 2006-01-02
Well, to be fair I've had Windows do the same to me when no network cable was connected. It hung until the network driver timed out before proceeding with the boot process.

If you don't want to use your wireless network, or use it infrequently, then you can disable it. System/Administration/Networking and Deactivate the network connection you don't want to start by default.

Or, you could just press Ctrl-C to interrupt the wait when you get to the point where the boot-up process waits for the network.

---

### Post by soulestream on 2006-01-02
1. I imagine(and from my own experience) that the problem is NTP. You system is trying to sync with a network time site and with no wireless it cant so you have to wait till it times out. 

2. Ubuntu(and linux in general) will boot slower than XP. M$ spent a great deal of time and effort for a asynchronous bootup. Depending on what you have loading in each OS, one can be faster than the other, but generally XP boots pretty quick, you just wind up with a quickly booted M$ product. Ill take 15 extra seconds on boot.


soule

---

### Post by Tipo on 2006-01-02
Also, correct me if I am wrong, but Unix based operating systems are designed and stable enough to run for long periods of time, like weeks (or more) at a time. So there is less booting required in the first place.

---

### Post by mcduck on 2006-01-03
In my experience XP is not a bit faste to boot than Ubuntu. Yes, you see your desktop quicker, but it still continues to start diferent things after that and it can take some time before everything is running. Ubuntu starts everything first and then shows your desktop..

Anyway, it's true that the timeouts with network related things are way too long, and with a laptopsand other computers that are not always connected to net that sure is a trouble. Ctrl-C will fix it, but you'll have to do that every time :/

---

