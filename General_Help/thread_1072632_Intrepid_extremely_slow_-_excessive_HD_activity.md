---
title: "Intrepid extremely slow - excessive HD activity"
date: 2009-02-17
forum: General Help
---

### Post by jondecker76 on 2009-02-17
After upgrading to Gutsy,  our Dell Dimension E310 has suffered sever slowdowns. Under 0704 and 0710, everything ran great and fast. After upgrading to Gutsy, things slowed to a crawl.

I just did a full fresh re-install with Intrepid, only to have the same problem. Opening something even simple, like Calculator, takes almost a minute. No matter what we try to do with this computer, the hard drive goes crazy with activity and eventually something happens on the screen. Again, this all worked great in 0704 and 0710.

The drive is a SATA drive, and I have tried 2 different drives now. The computer is a bit low on RAM (256 MB), but this has never matterred in the past.

Any suggestions?

Thanks

---

### Post by taurus on 2009-02-17
How large a swap partition do you have?

Applications -> Accessories -> Terminal
```
free -m
```

p.s.  Have you considered switching to XFce4 to go easy on the system resources?

---

### Post by whoop on 2009-02-17
Check what process is eating your ram. Is your swap file being used (how much). Is your cpu working overtime also? Might be some process going crazy.

256 mb is a little on the small size, anyway. You should consider using xubuntu. I have this running on to old machines with 256 mb of ram. Running quite well.

---

### Post by jondecker76 on 2009-02-17
I understand that 256MB is relatively low - but again, versions up to the last 2 versions of Ubuntu worked great. Besides, I already ordered 2GB or RAM for this machine (though I don't think its a RAM problem at all)

Here are the results of some commands:
```

free -m

       total    used  free
mem:     239     235     3
swap:    698     218   479


hdparm -Tt /dev/sda1
Timing cached reads:  594MB in 2.00 seconds = 296.90 MB/sec
Timing buffered disk reads: 4MB in 3.58 seconds = 1.12 MB/sec


```

Look at the output from hdparm - buffered reads are at 1.12 MB/second. I'm sure this is the problem.

Running the same on a very similarly spec'd computer results in:
```

hdparm -Tt /dev/sda1:
 Timing cached reads:   1502 MB in  2.00 seconds = 751.21 MB/sec
 Timing buffered disk reads:  202 MB in  3.02 seconds =  66.90 MB/sec


```


There is obviously a disk I/O problem. Again, I've tried 2 different SATA drives with the same result. This same computer worked fine under 0710 and 0704

Any other suggestions?

---

### Post by handy on 2009-02-18
The disk thrashing sounds like your machine is in & out of /swap all the time.  HDD read/write speeds are pitiful compared to the same tasks on RAM.

Your 256Mb is a miserable amount for Linux these days, especially Ubuntu.

I'm quite sure that when you install the 2Gb of RAM you mentioned (which will mean that you will never need to use /swap again) you will find that your machine becomes more sprightly than you have ever known it.

---

### Post by jondecker76 on 2009-02-18
I will report back here after my new RAM arrives.

I still don't think it will help, however, as buffered reads from the disk are happening at just over 1 MB/sec. This is 40-60 times slower than other similarly spec'd computers I have running Ubuntu. Also, as I have said before, despite having only 256 MB or RAM, it always ran fine in previous versions of ubuntu. In fact, I have 2 other computers that are similar in specs and have only 256 MB and they run just fine as well.

But like I said, I will report back when the RAM arrives and we can go from there

thanks

---

### Post by handy on 2009-02-19
You can't steal some RAM from one or both of the other computers & test if it makes a difference?

---

