---
title: "viable raid setup?"
date: 2009-04-24
forum: General Help
---

### Post by FeraTech on 2009-04-24
So for 9.4 I decided to get 3 500gig drives and play with raid5

I was just wondering how viable this setup is.

Each drive is partitioned:

500mb sd1
10gig sd3
989gig sd5

sd1 boot raid1 - mirrored all 3 drives
sd3 swap raid5 - raided swap
sd5 ext3 raid5 - /root

From what I gather if any drive fails as long as I should be able to boot from any drive. Also, opinions on bet performance for a setup like this would also be appreciated. ie, do you actually get any advantage from raid5 swap?

---

### Post by Menschenfresser on 2009-04-24
I would not put swap on raid5, you don't need the extra security and it will be (slightly) slower. About the rest of the setup, I personally would put give / less (around 10 GB?) and make a dedicated partition only for data. That way if you ever need to reformat / nothing will happen to the data. And speaking of which, perhaps another partition for /home would be another good idea for the same reasons.

---

### Post by fjgaude on 2009-04-24
And no matter what, do backups of all important data. Raid doesn't replace backups.

---

### Post by FeraTech on 2009-04-24
Backups are done off-site daily. So that isn't an issue. 

I'm just looking at the best possible performance gain.

Would the swap partition benefit at all by being raided? Would it work better/faster as raid 1?

---

### Post by fjgaude on 2009-04-24
For swap raid1, faster? I don't think so! Such is as fast as one drive, raid0 and raid5/6 are faster than one drive.

---

### Post by FeraTech on 2009-04-24
So is it possible to have swap setup as Raid0 and not lose anything when a drive fails?

Would this also provide any performance improvements?

---

### Post by fjgaude on 2009-04-24
No, raid0 looses all its data if one or more of the drives in its array goes bad.

RAM cache is a good way to not use swap at all... or do you have something unusual in mind?

Here's a link all about raid:

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

---

### Post by bsmith1051 on 2009-04-24
unless you have a dedicated hardware RAID controller, I wouldn't bother with RAID-5 or any other form that requires massive CRC or PAR or whatever calculations.

Basic RAID-1 mirror is generally best.  The Linux kernel 'knows' how to distribute read-requests across both drives and I was able to do a test that showed a 25% improvement in read-speed.  If you get a 4th drive you could do RAID-10, i.e., both RAID-0 (striping) and RAID-1 (mirror).

And I wouldn't RAID the swap file, at all.

---

### Post by FeraTech on 2009-04-25
Just out of curiosity how viable is it to have /boot and /swap on a USB 2.0 16 gig thumb drive?

Then have all 3 500gig drives in a raid 5 config? 

Would the swap partition on a USB drive be any faster? This would leave the drives free from sharing a swap. 

I have 8gig of ram in the machine so I'm not too worried about swap.

---

### Post by fjgaude on 2009-04-25
Most fast memory and CPUs these days are faster than hardware raid cards, because the cards have slow CPUs to control the price. Now $2000.00 cards are as fast as software raid5/6 in late-model computers.

My box is fast and so is my **mdadm** raid5:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates.

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

Those four Seagates have a throughput of about 70MB/sec each. Sotware raid rocks!

---

### Post by Tanker Bob on 2009-04-25
I have a 320 GB NVidia RAID1 setup as:

/ 15 GB
/home 303 GB
/swap 2 GB

I still have 8.3 GB free on /, so except for temporary files working with a video editor, I could probably shrink it to 10 GB and be fine.

---

