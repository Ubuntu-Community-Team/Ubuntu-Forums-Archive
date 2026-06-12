---
title: "unable to boot and unable to acces HD from live CD"
date: 2009-02-10
forum: General Help
---

### Post by cholericfun on 2009-02-10
Hi,

i know there is lots and lots of threads about this problem out there,
nonetheless i havent managed to make any progress...
beeing a rather recent addition to the linux user folks probably doesnt do myself any good either...
Basically I cannot acces any bit of the hard drive
So I would be really happy if someone can give me some hints... anything rather sooner than later...



I have a dual boot xp/ubuntu computer with 4 partitions on a single drive (C(ntfs),D(ntfs),sda3(ext3),swap).

a while ago my windows broke and i havent been able to fix it yet
since my windows broke, i occasionaly got hangups in ubuntu (i think always while having firefox open)
this morning ubuntu hung up and i foolishly pressed reset.
since then .. no luck - i can't start ubuntu, (for a while BIOS didnt even find my hard drive)
i can start ubuntu or recovery but only end up with a heap of errors relating to grub e.g.
(in recovery)
MOUNT : /root/dev on /dev/.static/dev
failed: no such file or directory
same for a few other things such as /root and /sbin/init

theres not much i can do from here...

So I thought i can at least backup my data from my hard drive before causing more damage using the Live CD
not even that worked...
when trying to mount sda3 i get an error and the recommended
"dmesg |tail" gives:

[ 2445.734025] Buffer I/O error on device sda, logical block 39072725
[ 2445.734069] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2445.734073] end_request: I/O error, dev sda, sector 0
[ 2445.734076] Buffer I/O error on device sda, logical block 0
[ 2481.536852] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2481.536861] end_request: I/O error, dev sda, sector 173710847
[ 2481.536875] EXT3-fs: unable to read superblock
[ 2822.588988] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2822.588995] end_request: I/O error, dev sda, sector 173710847
[ 2822.589142] EXT3-fs: unable to read superblock


I am kind-of able to mount the C and D drives, however, when i look into the various folders (e.g. containing music) there is nothing in there. cd'ing to it via the shell tells me there is an input/output error.
Trying to copy the apparently empty folders to an external HD doesnt work with the same error.

running
"sudo fdisk -l"
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e2990de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

and running "fdisk -lu"

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4e2990de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS


looks a little strange to me, especially since theres no boot and just one sdb1 partition instead of two (not sure if that makes sense though),
i think i saw some more output here earlier, not sure what to make of it.

i followed some advice from this post here:

and changed my Live CD fstab.
that succeeded in slightly changing the output of the error message
with dmesg | tail, but nothing else.


I guess i need to run a recovery to fix the filesystem in the hard drive or something like that.

Really not sure how to go about that/ if it makes sense...

Thank you all for your help!

---

### Post by cholericfun on 2009-02-10
PS,
i just rebooted with the live cd and typed 
sudo fdisk -l

...
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd59bd59b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3928    31551628+   7  HPFS/NTFS
/dev/sda2            3929       10302    51199155    7  HPFS/NTFS
/dev/sda3           10814       19457    69432930   83  Linux
/dev/sda4           10303       10813     4104607+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e2990de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS



is this in any way enlightning?

other than that - i didnt make any progress...

---

### Post by cholericfun on 2009-02-10
one more thing for now...
attemting to mount sda3 is not successfull,
error message this time looks a bit different from what i posted the first time round, the error message (line2) is the same as when trying to boot normally into ubuntu.

ubuntu@ubuntu:~$ dmesg |tail
[  521.178467] ata2: EH complete
[  521.178478] EXT3-fs: group descriptors corrupted!
[  521.178041] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  521.178053] sd 1:0:0:0: [sda] Write Protect is off
[  521.178055] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  521.178068] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  521.178083] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  521.178090] sd 1:0:0:0: [sda] Write Protect is off
[  521.178092] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  521.178103] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by taurus on 2009-02-10
If you want to mount /dev/sda3, try something like

```
sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 /media/sda3
df -h
```

---

### Post by JK3mp on 2009-02-10
Can u show us your grub conf file...if your getting grub errors its probably an issue with your partitioning messing with the bootloader...youu can try just deleting your windows partition entirely and fresh install everything. Takes some time but could greatly increase your chance of having a functional desktop.

---

### Post by ibuclaw on 2009-02-10
While you are still in the LiveCD

Go into: **System -> Administration -> Partition Editor**

For the sda3 filesystem, right-click it and select the "**Check**" option

You should see a frame at the bottom on the window pop saying:
**Check and repair filesystem (ext3) on /dev/sda3**

Then click **Apply** and let it run. (If you get any errors omitted, please tell us).

After it finishes, then try mounting it.

Regards
Iain

---

### Post by cholericfun on 2009-02-10
ah great,
well 
trying out
ubuntu@ubuntu:/dev$ sudo mount -t ext3 /dev/sda3 /media/sda3
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
and 
ubuntu@ubuntu:/dev$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 471M   13M  458M   3% /lib/modules/2.6.24-19-generic/volatile
tmpfs                 471M   13M  458M   3% /lib/modules/2.6.24-19-generic/volatile
varrun                471M  100K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M   48K  471M   1% /dev
devshm                471M   12K  471M   1% /dev/shm
tmpfs                 471M   20K  471M   1% /tmp
gvfs-fuse-daemon      471M  103M  368M  22% /home/ubuntu/.gvfs
ubuntu@ubuntu:/dev$

---

### Post by cholericfun on 2009-02-10
wow, replies come in faster than i can type, thanks a lot guys!!!

@ JK3mp ... not sure how i can get to the grub file, especially since i guess you mean the one on the HD.
but will certainly consider kicking windows out altogether...
just need one single program in it...will figure out some other ways of doing that.

gonna try the partition manager... 
thanks again

---

### Post by cholericfun on 2009-02-10
Ok, well, 
the partition manager doesn't detect anything...
(why can ubuntu see them though?)

any "force mount" options that might help?

actually - could you give me a hint as to how to force a mount .. last time i did that i froze the computer, ctrl-alt-F4 revealed a sort of ping pong game going on in the back...

---

### Post by ibuclaw on 2009-02-10
@JK3mp
You should try reading a bit more thoroughly.
For example, examine the following line from the OP.
> **cholericfun said:**
> 
i can start ubuntu or recovery but only end up with a heap of errors relating to grub
What is wrong with that statement?
GRUB **does not produce a heap of error messages**. Grub will only ever print out a short, punchy one-liner error message onscreen, [as enlisted on this site.]("http://www.uruk.org/orig-grub/errors.html")

> 
[ 2445.734025] Buffer I/O error on device sda, logical block 39072725
[ 2445.734069] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2445.734073] end_request: I/O error, dev sda, sector 0
[ 2445.734076] Buffer I/O error on device sda, logical block 0
[ 2481.536852] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2481.536861] end_request: I/O error, dev sda, sector 173710847
[ 2481.536875] EXT3-fs: unable to read superblock
[ 2822.588988] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2822.588995] end_request: I/O error, dev sda, sector 173710847
[ 2822.589142] EXT3-fs: unable to read superblock

This is the Linux Kernel talking ... and it is saying that his filesystem is bad and requires checking/fixing.

Regards
Iain

---

### Post by ibuclaw on 2009-02-10
> **cholericfun said:**
> Ok, well, 
the partition manager doesn't detect anything...
(why can ubuntu see them though?)

any "force mount" options that might help?

actually - could you give me a hint as to how to force a mount .. last time i did that i froze the computer, ctrl-alt-F4 revealed a sort of ping pong game going on in the back...

Doesn't detect **anything**? Could you make a small screenshot while on the PartManager Window? (**Alt+Printscreen**)


Regards
Iain

---

### Post by cholericfun on 2009-02-10
Well, tried a forced mount with
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda3 /media/sda3  -o force
and again got:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
dmesg gives same errors as before...

so.. 

quote:
   This is the Linux Kernel talking ... and it is saying that his
   filesystem is bad and requires checking/fixing.

how to go about that.. i dont see anything actually beeing able to get at the HD...
having read that some simple hardware changes can bring about such problems i'm going to try and unplug/plug in the HD...

hope that doesnt cause more of mess.

---

### Post by cholericfun on 2009-02-10
heres the screenshot attached (i hope)

its jst all gray... not very exciting

---

### Post by cholericfun on 2009-02-10
Ok, i swallowed some dust and plugged the HD in again and eveything is as bad as before...BUT 
gparted found the HD!
im running check and repair on sda3 at the mo..
fingers crossed...

thanks for your disbelief!

cheers Leo

---

### Post by cholericfun on 2009-02-10
that was quick,
currently cpying my home folder to an external HD

will do the same for the ntfs partitions then

---

### Post by cholericfun on 2009-02-10
actually didnt bother with the gparted fix on the ntfs partitions..
it just suddenly worked fine

all seems to be up and running.

what still baffles me is what happend..
especially since i created a heap of partitions in order to not loose everything once an OS gets faulty - and then have them as broken as the rest.
well, 

thanks to all of you for your help
cheers,
Leo

---

