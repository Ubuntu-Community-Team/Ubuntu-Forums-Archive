---
title: "missing &quot;/bin/sh&quot; not able to boot"
date: 2009-04-26
forum: General Help
---

### Post by samush on 2009-04-26
Hi,
 
I think I accidently removed or renamed the /bin/sh file and now I'm not able to boot ubuntu. I was trying to fix a problem with diming on my laptop and followed a tutorial that said tha this code schould fix it:
 
sudo mv /bin/sh /bin/sh.bak
sudo ln -s /bin/bash /bin/sh
 
After using that the system wan't boot. When I used the startup cd I could find a file named sh.bak in the bin directory but no sh.
What should I do? Is it possible to repair this without reinstalling? I have a lot off research on the laptop so its important for me to restore the system.
 
Please help!!
Thanx a lot 
 
Samush

---

### Post by gali98 on 2009-04-26
I'd really like to know what tutorial this is...
Um my guess is that you should boot up the live ubuntu cd. 
Then you should just have to find that sh.bak and rename it to just sh (no extension.)
Kory

---

### Post by samush on 2009-04-26
I tried that but I didn't have permission to do that....Is there some way of overriding it?
 
Samush

---

### Post by rhcm123 on 2009-04-26
> **samush said:**
> 
sudo mv /bin/sh /bin/sh.bak
sudo ln -s /bin/bash /bin/sh
 
Samush
I would like to see this tutorial, and slap whom ever wrote it. **BASH IS NOT THE SAME AS SH!!!** This person was trying to link bash to sh, so that when a program called for sh it was redirected to bash. **THEY ARE NOT THE SAME, NOR INTERCHANGEABLE, AND THIS BROKE YOUR SYSTEM!** This is basic here - you never delete shells and link them to others. This is honestly a very dumb idea.

Also, you have to be a little bit more careful. There was an announcement on the forums a few weeks ago that warned about blindly running commands - no offence, but a quick reading of the commands should have sounded an alarm.

Now, lets try and fix this mess.

**====THE FIX====**
You said you could find sh.bak. Im assuming your using the GUI live cd. Rename it to sh and reboot, you should be fine.

**====IF ELSE====**
 You need to boot from the live cd and select "rescue a broken system". It will ask you a bunch of questions, just yes it to death. After that, it will let you chose the root of your system. (It's usually /dev/sda1, but yours may vary.) 

**====THE HARD WAY, PART 1====**
Select "execute a shell in /dev/sda1". This will only work if it can find one of your other shells - it may not, depending on the age of the live cd. If it does, then run the following command:
```
rm /bin/sh && mv /bin/sh.bak /bin/sh
```
Reboot and it should work.

**====THE HARD WAY, PART 2====**
If that doesn't work, you will have to select "run a shell on the live cd".
Then do the following commands (each line is different), these might be a bit wrong, correct me if so (this is from memory here):
```

mkdir /mnt/drive
mount -t ext3 /dev/sda1 /mnt/drive
mv /mnt/drive/bin/sh.bak /mnt/drive/bin/sh

```

Hope we help.

---

### Post by rhcm123 on 2009-04-26
> **samush said:**
> I tried that but I didn't have permission to do that....Is there some way of overriding it?
 
Samush

Do you have a gui version of the liveCD? (i.e. do you have a desktop?)

---

### Post by albinootje on 2009-04-26
> **samush said:**
> 
What should I do? Is it possible to repair this without reinstalling? I have a lot off research on the laptop so its important for me to restore the system.

By default (since a while) /bin/sh is a symlink to /bin/dash

Can you boot in "recovery mode" ?
If not, use a linux live cdrom (dvd, or usb stick) and repair it.
If that sounds too difficult, then please boot from a live cd, open a terminal, and post the output of :
```

sudo fdisk -l

```

---

### Post by samush on 2009-04-26
Yes I have a desktop when i start the liveCd.

---

### Post by samush on 2009-04-26
I run your command and I got this:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4af5371c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1218     9776128   27  Unknown
/dev/sda2   *        1219       15723   116511412+   7  HPFS/NTFS
/dev/sda3           15724       29947   114254280   83  Linux
/dev/sda4           29948       30401     3646755    5  Extended
/dev/sda5           29948       30401     3646723+  82  Linux swap / Solaris

```

---

### Post by albinootje on 2009-04-26
> **samush said:**
> 
/dev/sda3           15724       29947   114254280   83  Linux

Thanks. Please do the following :
```

sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
sudo chroot /media/sda3 /bin/bash
cd /bin
mv sh sh.bak2
ln -s /bin/dash /bin/sh
exit
umount /media/sda3

```
And reboot and test.

---

### Post by samush on 2009-04-26
I got this when I tried:

```

ubuntu@ubuntu:~$ sudo mkdir /media/sda3
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/sda3
ubuntu@ubuntu:~$ sudo chroot /media/sda3 /bin/bash
bash: /usr/bin/groups: /bin/sh: bad interpreter: No such file or directory
root@ubuntu:/# 

```

---

### Post by samush on 2009-04-26
Thank you all for being so helpful!! I now Ive screwed up and should have been more carefull. So thank you all!! I hope I dont have to reinstall...

---

### Post by albinootje on 2009-04-26
> **samush said:**
> I got this when I tried:

```

ubuntu@ubuntu:~$ sudo mkdir /media/sda3
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/sda3
ubuntu@ubuntu:~$ sudo chroot /media/sda3 /bin/bash
bash: /usr/bin/groups: /bin/sh: bad interpreter: No such file or directory
root@ubuntu:/# 

```

Okay, please try this instead now :
```

sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
chroot /media/sda3 /bin/dash
cd /bin
mv sh sh.bak2
ln -s /bin/dash /bin/sh
exit
umount /media/sda3

```

---

### Post by albinootje on 2009-04-26
Can you also post the output of the following please :
```

ls -la /bin/bash  (to check the version from the live session)
ls -la /media/sda3/bin/sh
ls -la /media/sda3/bin/dash
ls -la /media/sda3/bin/bash

```

---

### Post by samush on 2009-04-26
Hey it actually worked!! I'm writing this from my ubuntu account! Thanks!! You are the best! I hope this didn't do any other damage. 

Thanks a lot again!!

Samush

---

### Post by samush on 2009-04-26
Should I do something more to be sure everything is working like it should?
 
Samush

---

### Post by albinootje on 2009-04-26
> **samush said:**
> Hey it actually worked

Cool :)

Well, in reply to what others wrote in this thread : 
I have seen the sh suggestion you (the OP) have followed before, because some scripts don't run well with /bin/dash, but they run well with /bin/bash

However.. you might have followed an old howto or suggestion, like here (from 2006) :
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/65028](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/65028)
It is possible that newer Ubuntu releases are much more picky about the /bin/sh link.

Sounds like everything is fine now.. 

Enjoy Ubuntu! :)

---

### Post by rhcm123 on 2009-04-26
whoa, i go away for 20 minutes and all is well!

---

### Post by samush on 2009-04-26
Yes it was exactly that link. I still haven't fix that problem with the dimer though:P

---

