---
title: "Problems after resizing partitions"
date: 2009-02-03
forum: General Help
---

### Post by Terraman on 2009-02-03
Hi Ubuntu friends,

I had the following partitions:

sda3: 10 GiB Swap
sda5: 35 Gib Ubuntu Intrepid
sda6: 35 Gib Freespire

So, I decided to shrink the swap partition (sda3) to 512 MB, I have shrunk the Ubuntu partition (sda5) to 17 GiB, and replaced the Freespire partition (sda6) with a separate home partition and re-sized it to 60 GiB or so.

After this, I have some problems with some applications, i.e. when I start Synaptic, it takes an endless time to run when I try to uninstall an application, and, moreover, it freezes all the other applications that I have opened. So, I have to wait 8 hours until it ends.

Does someone know what is going on, why, and how can I fix it.

Thanks in advance!

Edit: Terminal session triggers a 'process' and slows down the computer too.

---

### Post by Terraman on 2009-02-04
Anyone?

---

### Post by redilyn on 2009-02-04
can you run the following and post back the output

```

free -m

```

---

### Post by Terraman on 2009-02-04
redilyn,

I boot the computer from LiveCD, because Terminal takes a lot of time to load and apparently takes 100% of CPU.

> ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           438        431          7          0         37        168
-/+ buffers/cache:        225        213
Swap:          572         18        554
ubuntu@ubuntu:~$ 


From my current system using full screen terminal:

>              total       used       free     shared    buffers     cached
Mem:           437        432          5          0          2         51
-/+ buffers/cache:        378         58
Swap:            0          0          0


---

### Post by redilyn on 2009-02-05
Okay, if the second output was from your currently installed system I think I see the problem.

You do not have any swap space turned on.

Try this from your installed system (not the livecd)

```

sudo swapon -a

```

Then run the following again and post the output

```

free -m

```

---

### Post by Terraman on 2009-02-05
redilyn,

This massage shows up, it may sound funny, because I have translated it from Spanish.

> 
sudo swapon -a
swapon: 'stat' could not be executed for /dev/disk/by-uuid/5edd8501-32ad-429c-a26-f5a838b01763: filename or directory does not exist


---

### Post by redilyn on 2009-02-05
Okay, Do the following and let me know if it works

```

sudo vol_id -u /dev/sda5

```

Copy the string of characters that it prints out

```

sudo gedit /etc/fstab

```

Look for the entry relating to swap.

Replace the string after UUID= with the string you copied above.

Save and close this file.

Then try again

```

sudo swapon -a

```

---

### Post by Terraman on 2009-02-05
redilyn,

I have changed sudo 'vol_id -u /dev/sda5' to sudo 'vol_id -u /dev/sda1', because it is the swap partition, sda5 is the root partition.

> herman@patricia-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           437        360         77          0         10        131
-/+ buffers/cache:        218        219
Swap:          572          0        572
herman@patricia-desktop:~$ 


Apparently it works.

Thank you very much!

---

### Post by redilyn on 2009-02-06
Opps, good catch!

I'm glad you have it working now.

Cheers

---

