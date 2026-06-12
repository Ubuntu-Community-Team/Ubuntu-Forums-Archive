---
title: "hard drive performance"
date: 2011-03-08
forum: Desktop Environments
---

### Post by kylegio on 2011-03-08
Hello, I've been trying to test disk performance on my computer.
ive read that the hdparm command can be useful for this 
"sudo hdparm -tT /dev/***"

The only problem is im not really sure how the performance stacks up against others. Could someone give me a quick answer as to if these are good numbers or if there is room for improvement/ should be getting better numbers 


 Timing cached reads:   2840 MB in  2.00 seconds = 1420.72 MB/sec
 Timing buffered disk reads:  772 MB in  3.01 seconds = 266.81 MB/sec

running it a few times there is very little variance in the output ( a few mb/s either way)


ps: this is on a 6 disk(SATA) soft-raid5.

Thanks :)
kyle

---

### Post by amauk on 2011-03-08
seems fine to me
You've got through-put of 266.81 mega-bytes / sec
Max. real-world throughput for SATA II is 300 mega-bytes / sec (which is approx. 2.4 giga-bits / sec)

you can ignore the "cached reads" measurement, as this tests data through-put from cache (Ie. not reading from disk) and is a measurement determined by the CPU and RAM

---

