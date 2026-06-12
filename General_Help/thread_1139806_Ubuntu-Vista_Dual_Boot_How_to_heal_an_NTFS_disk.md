---
title: "Ubuntu-Vista Dual Boot: How to heal an NTFS disk?"
date: 2009-04-27
forum: General Help
---

### Post by savdevito on 2009-04-27
Hello,
I have (had?) a dual boot laptop hosting Vista and Ubuntu.
Unfortunately after a while Vista began to complain about the need
of a Checkdisk that It wasn't able to complete while booting for 
single access problems.
Now It goes Blue Screen of the Death while booting, Ubuntu However is still
on so I am able to log on in it.
BSD is probably due to disk problems, sound strange that i ask this question here but I really can think at a better place to get help.
I will be grateful is someone could post me some good information on how to try to recover starting from Ubuntu. Is there a good "NTFS Disk doctor" available in Ubuntu distro?
Thanks,
savdevito

---

### Post by danwood76 on 2009-04-27
there is a couple of ntfs tools for checking disks, but none can actually repair much.
The best tool is in windows.

Can you get to safemode in windows?
If you can order a disk check from there.

I had a very similar problem with my vista when I cloned it from one disk to another (mainly just to see if I could do it) oddly after I fixed disk permissions and so on it was fine.
Then I reinstalled anyway. :)

---

### Post by savdevito on 2009-04-27
> Can you get safemode?

Unfortunately no. If left alone, it also try to go System Recovery, but an error occu
"The installed program cannot start. Click OK to turn off the computer."
Funny.

At least data can be read by Ubuntu so  I  made a backup of the important data.
 
Could you please point me out some tools to try a disk repair? (Based on Ubuntu or not.)

Thank you.
savdevito

---

### Post by danwood76 on 2009-04-27
The best thing to do is stick in a Vista installation disk and enter the recovery console. From there you can run a check disk.

If you choose 'Fix Boot' it will overwrite you MBR and you wqont be able to boot ubuntu unless you use a live disk to reinstall grub.

---

### Post by danwood76 on 2009-04-27
There is a tool in linux that will cause vista to checkdisk on boot.
Its called ntfsfix and is in the ntfsprogs package.

---

