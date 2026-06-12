---
title: "mdadm raid resync not multicore"
date: 2012-03-26
forum: Desktop Environments
---

### Post by ryannathans on 2012-03-26
I wanted to create a raid 5 array, so i did.

mdadm --create /dev/md0 --chunk=16 --level=raid5 --raid-devices=5 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

and watched /proc/mdstat with the eyes of a cat.

cat /proc/mdstat

I was getting ~49000k/sec

Not bad, I know each drive can do double that.

I had a suspicion that the 'md0_resync' and 'md0_raid5' weren't allowed to use multiple cores.

i opened 'top' and saw together their usage as about 80-100% of one core. (i5 2500 4 cores)

so the processes were 8004 and 8003.

i did a 'taskset -p 4 8004' and a 'taskset -p 4 8003' and checked my speeds and cpu usage.

speeds were now ~100000k/s (double before) and usage was spread out.


**My question is - with todays multicore cpus, why aren't these CPU bottlenecked processes allowed to use many cores? Why stuck to just one?**

Thanks!
ryannathans

---

### Post by masuch on 2012-05-24
I would like to know it as well.

---

