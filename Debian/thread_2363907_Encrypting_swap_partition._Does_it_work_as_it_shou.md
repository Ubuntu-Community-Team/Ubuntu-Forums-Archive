---
title: "Encrypting swap partition. Does it work as it should?"
date: 2017-06-16
forum: Debian
---

### Post by vol24pl on 2017-06-16
Hello. This is my first post so go easy on me :) As I like my tinfoil hat I like to have every device encrypted. When I decided to install Debian 8 as my desktop OS encryption was implied. So let me start at the beginning:

1. I installed Windows 10 with 200GB partition out of 305GB (partition #2)
2. I encrypted it with bitlocker which made another partition (stealing space from partition #2) for booting and encrypting Windows (partition #1) at the beginning of the HDD

I just mentioned this partitions to make print screens below more understandable :)

3. I booted Debian installation and went for graphical installation
4. In partition manager I created 500MB partition (#3) and selected it as primary partition, mounted as boot
5. Then I created 100GB (#5) partition and chose "encrypted"
6. Then I created 5GB (#6) partition and choose "encrypted"
7. I saved changes and went to choosing what to do with encrypted partitions
8. I used #5 as ext4 partition and mounted root there
9. I used #6 partition as swap partition
10. #5 and #6 made "extended partition #4"
10. I installed rest of the stuff and started to use OS
11. So my config look like this


Partition #3 [http://imgur.com/FzUwIIZ](http://imgur.com/FzUwIIZ)
Partition #4 [http://imgur.com/yJlwvCA](http://imgur.com/yJlwvCA)
Partition #5-1 [http://imgur.com/xgQXmig](http://imgur.com/xgQXmig)
Partition #5-2 [http://imgur.com/LhXHWBn](http://imgur.com/LhXHWBn)
Partition #6-1 [http://imgur.com/57ZHVsT](http://imgur.com/57ZHVsT)
Partition #6-2 [http://imgur.com/WufJVr8](http://imgur.com/WufJVr8)

12. After rebooting I have to provide password for #5, I provide it
13. After rebooting I have to provide password for #6, I provide it.
14. AND HERE IT IS! [http://imgur.com/51KBwgX](http://imgur.com/51KBwgX)

So i typed the command as told and here it is:

```
vol@vol-debian:~$ systemctl status systemd-cryptsetup@sda6_crypt.service
&#9679; systemd-cryptsetup@sda6_crypt.service - Cryptography Setup for sda6_crypt
   Loaded: loaded (/etc/crypttab)
   Active: failed (Result: exit-code) since Sat 2017-05-20 12:25:54 CEST; 30min ago
     Docs: man:crypttab(5)
           man:systemd-cryptsetup-generator(8)
           man:systemd-cryptsetup@.service(8)
  Process: 385 ExecStop=/lib/systemd/systemd-cryptsetup detach sda6_crypt (code=exited, status=1/FAILURE)
  Process: 382 ExecStartPost=/sbin/mkswap /dev/mapper/sda6_crypt (code=exited, status=1/FAILURE)
  Process: 364 ExecStart=/lib/systemd/systemd-cryptsetup attach sda6_crypt /dev/disk/by-uuid/9df317c7-bd1e-4c93-b2ba-5c30169e02fb none luks,swap (code=exited, status=0/SUCCESS)
 Main PID: 364 (code=exited, status=0/SUCCESS
```
Output of command "sudo blkid | grep swap:

```
/dev/mapper/sda6_crypt: UUID="590cf396-192d-4739-93b2-f0a6d6955078" TYPE="swap"
```
My question are: What should I do to make it work? Is my swap encrypted? Is it working?!

---

### Post by TheFu on 2017-06-16
What does **swapon -s** show?

Normally, people create 2 partitions - /boot and {everything else}.  Inside {everything else}, we create an encrypted container using cryptsetup, then add LVM PVs, VGs, and LVs.  The LVs are extremely flexible partitions that can be modified without rebooting.  Both resized bigger and smaller, if ext4 is used. A swap LV can be used too. The result of doing all this is that only 1 partition is encrypted, thus only 1 partition prompt for a passphrase.

I don't use Windows on this machine, but ...
```
$ lsblk
NAME                          MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                          8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                          8:2    0   488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0  70.8G  0 part  
&#9474; &#9492;&#9472;crypt1                    252:0    0  70.7G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--mate--vg-root   252:1    0  57.4G  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--mate--vg-swap_1 252:2    0   4.1G  0 lvm   [SWAP]
&#9492;&#9472;sda4                          8:4    0  47.5G  0 part  /misc/Stuff
```
that's the result. Note how /boot and efi and sda4 are not encrypted.  This is a UEFI system with GPT disk format, not MBR/DOS.  UEFI is **not** important. I ran with legacy boot for a few years with encryption. Works fine.  If GPT isn't used, then it would be best to create an extended partition and single logical partition to put the encrypted container inside.  Then use LVM.

Clear as mud?  I should mention, that to achieve this requires lots and lots of CLI commands. There ain't no GUI.

The **lsblk** for your box would be helpful.

---

### Post by vol24pl on 2017-06-28
Sorry for the delay. Here it is:```

root@vol-debian:/home/vol# swapon -s
Filename				Type		Size	Used	Priority
/dev/dm-1                              	partition	4151292	0	-1
root@vol-debian:/home/vol# lsblk
NAME           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda              8:0    0 298.1G  0 disk  
&#9500;&#9472;sda1           8:1    0   500M  0 part  
&#9500;&#9472;sda2           8:2    0   200G  0 part  
&#9500;&#9472;sda3           8:3    0   477M  0 part  /boot
&#9500;&#9472;sda4           8:4    0     1K  0 part  
&#9500;&#9472;sda5           8:5    0  93.1G  0 part  
&#9474; &#9492;&#9472;sda5_crypt 254:0    0  93.1G  0 crypt /
&#9492;&#9472;sda6           8:6    0     4G  0 part  
  &#9492;&#9472;sda6_crypt 254:1    0     4G  0 crypt [SWAP]
sr0             11:0    1  1024M  0 rom 

```

---

### Post by TheFu on 2017-06-28
So you didn't use LVM. That makes it hard (impossible?) to be prompted once for a password. Oh well, to each their own.

**swapon** shows an encrypted partition is available for use. You can also check with **free -hm** to see swap and buffers used.

There are other ways to confirm all this stuff under /dev/ ... through links for the different partitions and encrypted devices.

You might want to use LVM next time. Makes for a cleaner and easier use of encrypted partitions, yes?

---

### Post by vol24pl on 2017-07-04
> **TheFu said:**
> So you didn't use LVM. That makes it hard (impossible?) to be prompted once for a password. Oh well, to each their own.

**swapon** shows an encrypted partition is available for use. You can also check with **free -hm** to see swap and buffers used.

There are other ways to confirm all this stuff under /dev/ ... through links for the different partitions and encrypted devices.

You might want to use LVM next time. Makes for a cleaner and easier use of encrypted partitions, yes?
I don't mind providing password 2 times, as the current encrypted debian setup is just a proof-of-concept for learning purposes. Next time of course I will think about your setup (can you provide me links or small tutorial on how to set it up from scratch?)
```

root@vol-debian:/home/vol# swapon
NAME      TYPE      SIZE USED PRIO
/dev/dm-1 partition   4G   0B   -1
root@vol-debian:/home/vol# free -hm
             total       used       free     shared    buffers     cached
Mem:          3.9G       1.4G       2.5G        13M        39M       595M
-/+ buffers/cache:       772M       3.1G
Swap:         4.0G         0B       4.0G

```

---

### Post by TheFu on 2017-07-04
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) ?

---

### Post by vol24pl on 2017-07-11
> **TheFu said:**
> [https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) ?

Thanks!

can you tell me is my swap working? For me it looks like it's working but it's always used in 0%

Any ideas on how to test it for sure? Is it working? Is it really encrypted?

---

### Post by TheFu on 2017-07-11
You have the commands above. There isn't any more.

---

