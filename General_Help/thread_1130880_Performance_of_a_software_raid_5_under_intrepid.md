---
title: "Performance of a software raid 5 under intrepid"
date: 2009-04-20
forum: General Help
---

### Post by swarsron on 2009-04-20
Hi,

i'm currently trying to create a raid 5 out of three 1 TB hdd. For now there is one hdd missing so i get 3 TB of usable space.

One hdd is connected to
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)

the other two to
04:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

The CPU is a AMD X2 4200+ and the system has 2 GB RAM.

The performance of the array is underwhelming.
time dd if=/dev/zero of=big_file bs=4096 count=2560000
10485760000 bytes (10 GB) copied, 187.691 s, 55.9 MB/s
dd if=/dev/zero of=big_file bs=4096 count=2560000  0.70s user 26.05s system 14% cpu 3:08.12 total

time dd if=big_file of=/dev/null bs=4096 count=2560000
10485760000 bytes (10 GB) copied, 297.345 s, 35.3 MB/s
dd if=big_file of=/dev/null bs=4096 count=2560000  0.50s user 10.60s system 3% cpu 4:57.35 total

So i get a write performance of 55 MB/s and a read speed of 35 MB/s.

The details for the raid device:
```
/dev/md6:
        Version : 00.90
  Creation Time : Sun Apr 19 22:30:23 2009
     Raid Level : raid5
     Array Size : 2930279424 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 6
    Persistence : Superblock is persistent

    Update Time : Mon Apr 20 14:45:32 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 584a0f66:3c075c23:9cae9464:25382498 (local to host johannes-desktop)
         Events : 0.21396

    Number   Major   Minor   RaidDevice State
       0       8       97        0      active sync   /dev/sdg1
       1       8      145        1      active sync   /dev/sdj1
       2       8      161        2      active sync   /dev/sdk1
       3       0        0        3      removed
```

On top of the raid device there is a crypto layer
cryptsetup --verify-passphrase -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/md6
and then ext4
mkfs.ext4 -v -b 4096 -E lazy_itable_init,stride=64,stripe-width=256 -O large_file,dir_index,extent,sparse_super,uninit_bg -m0 /dev/mapper/data

Stride and stripe-width will be correct when i add another two hdd of which one will carry data. Can someone please give me a hint why i could get such bad performance especially while reading? I don't think its the crypto layer since kcryptd doesn't go over 50% cpu and having two cores should prevent other users from starving. The stride and stripe-width aren't correct right now but can it degrade performance like that? I would expect 100+ MB/s on reading and writing.

Thanks

---

### Post by fjgaude on 2009-04-20
Is the array fully synced up? What does this show:

```
sudo watch cat /proc/mdstat
```

---

### Post by swarsron on 2009-04-20
Yes it is (no other way when running with n-1 drives)

md6 : active raid5 sdg1[0] sdk1[2] sdj1[1]
      2930279424 blocks level 5, 256k chunk, algorithm 2 [4/3] [UUU_]

The missing disk shouldn't hurt performance (probably should improve it since no parity calculations are needet)

---

### Post by ronparent on 2009-04-20
Unlikely, but, is the silicon image raid bios turned off? If you are using a software raid solution it could be getting in the way.

---

### Post by swarsron on 2009-04-20
i don't really know. I just plugged the card in and configured nothing further. so i asume that it's just working as a sata connection which is what i want. I can't reboot right now but i'll check it tomorrow. But i doubt that is the problem. Do you have other suggestions? Thanks you two for answering.

---

### Post by fjgaude on 2009-04-20
How did one of the four drives get removed from the array?

You should be getting the read speed of twice one of the drives... knowing these are fast your read speed should be about 200MB/sec.

Are you on a PCI bus with the two SATA drives? Mixing IDE and SATA could be the issue.

The PCI bus only goes to about 110MB/sec. For what you are seeking you need PCI-E.

---

### Post by swarsron on 2009-04-20
i created it degraded. you can specify one "missing" drive

the controller is on pci-e so that shouldn't be the problem. i get the same behaviour with all drives on the internal nvidia controller

---

### Post by fjgaude on 2009-04-21
What thru-put do you get using **hdparm** on just one of the drives in the array:

```
sudo hdparm -tT /dev/sdg1
```

If you don't get over 100MB/sec then something is wrong... have to dig deeper.

---

### Post by swarsron on 2009-04-21
hdparm -tT /dev/sdg1

 Timing cached reads:   1080 MB in  2.00 seconds = 539.64 MB/sec
 Timing buffered disk reads:  322 MB in  3.01 seconds = 107.13 MB/sec

so this shouldn't be the problem

---

### Post by fjgaude on 2009-04-21
Problem, maybe! Here's my score:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

Your cached reads are very low and may be why software raid is not working as it should. Your CPU and memory seem slow, but here again, my box is fast:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates.

These Seagates each have a buffered read of about 70MB/sec.

I can't say that your CPU and memory is the botterneck but they could be.

---

### Post by swarsron on 2009-04-21
> **fjgaude said:**
> 
Your cached reads are very low and may be why software raid is not working as it should. Your CPU and memory seem slow, but here again, my box is fast:


I don't think that that could be the problem since cached reads aren't important in this case. That could be a factor if i ran something like bonnie++ but with dd there is nothing to be cached, everything is only read once.

> **fjgaude said:**
> 
I can't say that your CPU and memory is the botterneck but they could be.


i don't think so, CPU doesn't go above 50%. Memory isn't the newest stuff but it's not like i have a pentium 90 so i can't explain the low speed

---

### Post by fjgaude on 2009-04-21
Okay, what is the answer? Individual drives are fast... but the array isn't. We are left with how **mdadm** created the array, eh? 

Are you able to re-create the array?

---

### Post by swarsron on 2009-04-22
> **fjgaude said:**
> Are you able to re-create the array?

no i'm not. At least not without a real effort for me. I just added another two drives, in 5 hours the reshape is complete and then i'll try it again. I'm also working with the people on linux-raid to get to the problem so i'll post if i find a solution there

---

### Post by fjgaude on 2009-04-22
Okay, please do post any news.

---

