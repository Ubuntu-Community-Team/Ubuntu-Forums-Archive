---
title: "Can't turn swap on after repartition"
date: 2009-03-31
forum: General Help
---

### Post by Patrick Snyder on 2009-03-31
Hello everyone (^_^)/

I had less than 500MB of swap, so I recently repartitioned it to approx. 3GB.
I used Ubuntu's 8.10 live CD and GParted, turned swap off to unlock it, and then repartitioned.

Now, everytime I reboot normally, conky tells me swap is off, and I have to go into GParted (in my normal Ubuntu) to turn it back on.


I tried swapon in the terminal but get this error:

```
patrick@patrick-laptop:~$ swapon -a
swapon: cannot stat /dev/disk/by-uuid/e625afb7-bbed-426b-81d1-bdda1c84e114: No such file or directory
```


1)  Is there a way to turn it on in terminal that I'm missing?

If there is, I know I can add it to "Sessions" but:
2)  Is there a more permanent, normal functioning way to turn it on at boot?


Thanks in advance (^_^)
Best Wishes,
Patrick

---

### Post by pennacook on 2009-03-31
You may need to update your /etc/fstab to point to the correct partition. 
1. Find out what partition it is on now:
  ```
sudo fdisk -l
```
Look for the partition that has Linux swap listed for type.
2. Update /etc/fstab to that partition (/dev/sda5 for example)

3. swapon -a

---

### Post by NT4usB on 2009-03-31
When you repartitioned, the UUID of swap changed. Need to change the UUID of swap in fstab, then mount -a.

...just went through this, making more room in /root so I could upgrade. Moved everything over to the right a tad on drive 0.
fstab is completely bjorked now. sda is Drive 1, a data drive on it's own. 
Drive 0 is sdb and has all the partitions for root, boot, swap. home, etc. sdc is a partition on drive 0.
It ain't pretty but it works... sort it out another day.

---

### Post by drs305 on 2009-03-31
It's your swap UUID that probably changed, as was mentioned. 
```
sudo swapoff -a    # turns off all current swap files/partitions
```
Run this to check your new UUIDs:
```

sudo blkid -c /dev/null | grep 'swap' # ensures the current UUIDs are reported

```
Compare the UUID above to those in /etc/fstab and resume:
```

cat /etc/fstab | grep 'swap' 
cat /etc/initramfs-tools/conf.d/resume

```
The first line is the swap UUID in fstab
The second is the swap UUID stored in /etc/initramfs-tools/conf.d/resume.

IF either/both of these do not agree with the first result, edit the fstab and/or resume files and make them match the output of the *blkid* command.

Open both files as root to edit:
```
gksudo gedit /etc/fstab /etc/initramfs-tools/conf.d/resume
```
Update the system:
```
sudo update-initramfs -uk all
sudo swapon -a
```
Check your swap usage. You may need to reboot.

---

### Post by Patrick Snyder on 2009-03-31
Thank you so much everyone!  Your posts were easy to understand and helpful.
drs305, I followed your post step by step, and everything seems to be working just right now.

I switched to Ubuntu because I was curious, I stayed because of support like this, from people like you! (^_^)


Hopefully, in the future, I'll get to that point where I can give back to the community, instead of just asking the questions. =p

Take care!
Best Wishes,
Patrick

---

### Post by kimharding on 2009-10-13
I have been trying to follow the advice given above but after 

sudo update-initramfs -uk all
sudo swapon -a

I get:
swapon: cannot stat /dev/disk/by-uuid/17e9d245-a5bc-4ec8-9bbc-a5e000d5bb61: No such file or directory

where am I going wrong?

---

### Post by drs305 on 2009-10-13
> **kimharding said:**
> I have been trying to follow the advice given above but after 

sudo update-initramfs -uk all
sudo swapon -a

I get:
swapon: cannot stat /dev/disk/by-uuid/17e9d245-a5bc-4ec8-9bbc-a5e000d5bb61: No such file or directory

where am I going wrong?

You are making posts in multiple threads. Please choose one - it will make it easier to follow what is happening. 

Do your fstab, the blkid results and resume results all match? 
Since I made a post in the other thread, you can reference that post if you don't understand the question. Please respond there if you still need assistance.

---

### Post by aswhad on 2010-01-18
Thanks a lot drs305, i'm smiling again ;)

---

