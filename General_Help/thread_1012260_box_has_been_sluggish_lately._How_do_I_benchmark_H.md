---
title: "box has been sluggish lately. How do I benchmark HD?"
date: 2008-12-15
forum: General Help
---

### Post by memories on 2008-12-15
My computer has been very sluggish lately. It might of happened right after going Hardy to Intrepid but I'm not sure. I ignored it at first but its getting worse day by day. It has been about 2 weeks now.

According to 'uptime' my load is around .9 - 1.20. There's no 1 process taking too many resources/CPU usage.

firefox does but closing it and reopening it only helps a little. 

I think my hard drive is dying. There are no ticks or sounds, but my computer has been on since 2006.

How can I test/benchmark my HD to make sure it's not crapping out? What can I do to find the bottleneck here? 

By "sluggish" I mean there's a visible delay when I open a page with JS on it. My mouse / kb pauses for a sec while the JS loads. Switching windows shows them being redrawn, and having multiple tabs open wrecks havoc on performance and memory. 

specs aren't bad. athlon xp 2100+, 2gb of RAM (new), geforce 6600

help!

---

### Post by nielz on 2008-12-16
You can do a simple benchmark on your hd using hdparm. Watch out with hdparm though, it's been know to break hard drives if you feed it the wrong commands. The example below is safe though:

```

root@c014:~# hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1672 MB in  2.00 seconds = 836.30 MB/sec
 Timing buffered disk reads:  262 MB in  3.02 seconds =  86.88 MB/sec

```

You can also try looking at the output of the dmesg command. If you have lots of bad sectors it should show in this log.

There's also smartctl (in the smartmontools package) which you can use to interrogate your hard drive's SMART tables which can also give clue's if something is about to break.

---

### Post by memories on 2008-12-29
Thanks. Ran it, here are the results:
> 
/dev/sda:
 Timing cached reads:   1000 MB in  2.00 seconds = 499.34 MB/sec
 Timing buffered disk reads:  192 MB in  3.02 seconds =  63.57 MB/sec


(this is avg, I ran it a few times). The HD is 7200 (100 gigs). 

Any other benchmarks I can do to figure out the bottleneck here?

---

