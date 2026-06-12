---
title: "Better swap usage"
date: 2009-03-13
forum: General Help
---

### Post by Orlsend on 2009-03-13
Hi! I am on a eeepc with 1 GB of ram and with 2 GB of swap,I do alot of web browsing( Specially watching videos), in my older computer that had less ram I used to do the same thing.except it used the swap more. which made my experience way better. The problem is that my Ubuntu does not seam to use the swap at all.

Is there a file I could edit and add a command so it will use my swap file more?

---

### Post by iaculallad on 2009-03-13
Post whatever displays when you issue the terminal command below:

```
free -m
```

---

### Post by Orlsend on 2009-03-13
[B]orlsend@orlsend-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        746        254          0         27        355
-/+ buffers/cache:        363        637
Swap:         2933          0       2933[/B]

---

### Post by lloyd_b on 2009-03-13
It probably just doesn't need to use swap.  I'm currently on a machine with 512MB, with Firefox loaded, and I'm not using any swap to speak of.

Remember, the only time swap is really used is when you don't have enough actual RAM to meet the needs of your programs (leaving aside "suspend to disk", which I believe uses the swap partition to save the state of RAM).

Lloyd B.

---

### Post by Orlsend on 2009-03-13
Well I guess it could a be a setting in my cache in firefox, it prov needs some more.

I am stil courious if theirs still a command.

---

### Post by iaculallad on 2009-03-13
There's a probability that the swap partition is not needed in an instance. Try opening multiple applications (OO Word Processor, OO Spreadsheet, Firefox) at the same time then re-issue the command **free -m** and observe the changes.

---

### Post by iaculallad on 2009-03-13
> **Orlsend said:**
> 
I am stil courious if theirs still a command.

You could try the command below to output the UUID of your swap partition and compare it with /etc/fstab file.

```
blkid | grep -i swap
```

For sure, both will have a similar UUID since the **free -m** command displays your swap partition capacity.

---

### Post by Orlsend on 2009-03-13
I did as told still my ram its just getting used more. its about 400/1000MB. the case I watch video on line that are about 1GB big and I think it could be a good use for my swap.

---

