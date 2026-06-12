---
title: "Information on /etc/rc*.d?"
date: 2009-03-25
forum: General Help
---

### Post by Huufarted on 2009-03-25
I'm looking at increasing my boot time on my Asus eee 1000HA.  It's a phenomenal laptop, but the boot time really increased over Xandros.  I'm looking at some info from [http://hehe2.net/linuxhowto/howto-your-perfect-ubuntu-on-your-perfect-eee-pc/](http://hehe2.net/linuxhowto/howto-your-perfect-ubuntu-on-your-perfect-eee-pc/) and have just a few questions.

It shows this as an example:
```
sudo mv /etc/rc2.d/S12hal /etc/rc2.d/S13hal
```

But on my system, it's in there as S24hal instead.  Does this make a difference?  Why is it being renamed in the first place?

Another of the suggestions is "CONCURRENCY=none" gets changed to "CONCURRENCY=shell".  Why is this?  What does it accomplish?  From their description, it allows the scripts to run at the same time instead of sequentially.  Now, does it run all of the scripts on rc2.d at the same time or all of the S01* scripts in each of the directories at the same time?

What is the purpose of the suggestions they're giving?

---

### Post by dcstar on 2009-03-26
> **Huufarted said:**
> 
.........
Another of the suggestions is "CONCURRENCY=none" gets changed to "CONCURRENCY=shell".  Why is this?  What does it accomplish?  From their description, it allows the scripts to run at the same time instead of sequentially.  Now, does it run all of the scripts on rc2.d at the same time or all of the S01* scripts in each of the directories at the same time?

What is the purpose of the suggestions they're giving?

All files in those directories are started in ASCII order.

For machines with mechanical drives it is usually quicker to allow one process to start before going onto the next one because of a condition called "thrashing". This is where you load up so many simultaneous disk requests that the poor disk spends too much time physically moving the heads from one spot of the disk to another rather than staying in one area and doing what it needs to in one hit (the disk heads "Thrash" all over the place, very inefficient).

For Solid-state drives (SSDs) this is not a problem, they do not have mechanical heads to move and therefore can access data spread across them far (FAR) more quickly than a mechanical storage device.

This means you can start the next process before waiting for the previous one to conclude ("Concurrently"), thus minimising any time previously spent waiting for a mechanical storage device to do its thing. *******

Bottom line: Your system *should* start up quicker.


******* Big caveat for SSDs, if the start-up process causes a lot of writes then you may also end up with a slower system because some SSDs are very slow on the write phase, and they can write large minimum physical blocks of data even though the system may only want to write a small amount of data - slowing things down even further......

---

### Post by Huufarted on 2009-03-26
I'm not using an SSD, so I'll be disabling that!

---

### Post by oldos2er on 2009-03-26
"Another of the suggestions is "CONCURRENCY=none" gets changed to "CONCURRENCY=shell".  Why is this?  What does it accomplish?"

 If you have a dual core (or greater) processor, changing to CONCURRENCY=shell allows the boot process to take advantage of both cores, thus decreasing boot time. It's useless on single core systems.

---

### Post by Huufarted on 2009-03-26
> **oldos2er said:**
> "Another of the suggestions is "CONCURRENCY=none" gets changed to "CONCURRENCY=shell".  Why is this?  What does it accomplish?"

 If you have a dual core (or greater) processor, changing to CONCURRENCY=shell allows the boot process to take advantage of both cores, thus decreasing boot time. It's useless on single core systems.

So the CONCURRENCY change won't slow my loading times even though I'm not on SSD?  Renaming the hal scripts is what I want to avoid, but the CONCURRENCY is good to go to modify?

I'm following you guys.  At least I think I am.

---

