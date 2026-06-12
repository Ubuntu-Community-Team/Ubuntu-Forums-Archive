---
title: "Combine OS's to one HDD"
date: 2009-06-06
forum: General Help
---

### Post by carterw65 on 2009-06-06
Hi all!

I have two HDD's, one with XP and one with Ubuntu. My XP drive crashed so I bought a new one and reloaded windows. Since the drive is bigger than the old one I would like to combine the two and not have to swap HDD's when I get the urge (rare thing) to use windows. Any thoughts on how to do this? I did save some unformatted space on the windows drive just for this purpose.

thanks!):P

---

### Post by ronparent on 2009-06-06
1st off, what I would do is not necessarily the best or the easiest way, but, one my simple mind can comprehend.

What I would do is to use gparted to copy your current ubuntu install to the vacant space on your new drive (GUI copy, paste). Then I would use the live cd to setup grub to write the grub mbr to the new drive (this will probably replace the windows mbr if that is your boot drive in bios). You should set the new drive as boot in bios. Then you will probably have to edit /boot/grub/menu.lst to locate windows. If the new drive is boot, windows will be on (hd0) - in grub terms. Once you have verified that everything works, you can delete the old ubuntu partition. It sounds like a piece of cake. Call if you need help.

---

### Post by colau on 2009-06-06
> **ronparent said:**
> 1st off, what I would do is not necessarily the best or the easiest way, but, one my simple mind can comprehend.

What I would do is to use gparted to copy your current ubuntu install to the vacant space on your new drive (GUI copy, paste). Then I would use the live cd to setup grub to write the grub mbr to the new drive (this will probably replace the windows mbr if that is your boot drive in bios). You should set the new drive as boot in bios. Then you will probably have to edit /boot/grub/menu.lst to locate windows. If the new drive is boot, windows will be on (hd0) - in grub terms. Once you have verified that everything works, you can delete the old ubuntu partition. It sounds like a piece of cake. Call if you need help.
Sorry for this post.
Will gparted work booting in ubuntu 9.04 system(logging in ubuntu)?
Or it will work only with some live cd?
:);)

---

### Post by ronparent on 2009-06-06
Good point. Live cd. I believe the current ubuntu partition has to be unmounted to do the copy from.

---

### Post by carterw65 on 2009-06-06
Would it be beneficial to copy my current HDD with Ubuntu on it to an external drive and then reinstall it on the new HDD with the window partition? Or is this not the correct way? I really do not know linux very well. I guess I am confused how to get it on the new drive. I upgraded to 9.04 from 8.10 so I don't have a live cd, I would have to make one.

Thanks

---

### Post by colau on 2009-06-06
> **carterw65 said:**
> Would it be beneficial to copy my current HDD with Ubuntu on it to an external drive and then reinstall it on the new HDD with the window partition? Or is this not the correct way? I really do not know linux very well. I guess I am confused how to get it on the new drive. I upgraded to 9.04 from 8.10 so I don't have a live cd, I would have to make one.

Thanks
You can use the 8.10 cd.

---

### Post by ronparent on 2009-06-06
You don't need the 9.04 live cd. The 8.10 live cd would accomplish the same thing. If you were concerned about the grub (I don't know if it was updated also?) You could boot into your old 9.04 install to do the grub reconfigure and mbr things to boot to your new install!

---

### Post by jflaker on 2009-06-06
> **carterw65 said:**
> Would it be beneficial to copy my current HDD with Ubuntu on it to an external drive and then reinstall it on the new HDD with the window partition? Or is this not the correct way? I really do not know linux very well. I guess I am confused how to get it on the new drive. I upgraded to 9.04 from 8.10 so I don't have a live cd, I would have to make one.

Thanks

If you have external storage, copy off your data and don't forget about your hidden folders like .purple and .evoulution and maybe some others....

Remember, if you are doing a dual boot, it is windows first, then ubuntu

---

### Post by carterw65 on 2009-06-25
> **ronparent said:**
> Good point. Live cd. I believe the current ubuntu partition has to be unmounted to do the copy from.

Hi Ronparent!

I installed a fresh copy of Ubuntu onto the drive and then installed a grub and everything is working, other than I severly broke my sprint wireless card and can't get it working again, and I didn't ever move my data over either. I still want to try to get the original Ubuntu drive moved over.

So this is were I am at. I have my old ubuntu drive in an external case, I have a 500gb external drive, and the internal drive with XP, a Fat32 partition, and the Ubuntu/swap partitions. I figure if I get the original Ubuntu OS onto the new drive I will need to use gparted and some how figure out the grub thing so it will dual boot.

Thanks!

Bill

---

### Post by ronparent on 2009-06-27
Regarding your private post, yes, what you want is doable and fairly simple. Boot to a live cd (8.04 or 8.10 will work fine). In the partition manager, simply copy (<ctrl>c) your old ubuntu partition and paste <ctrl>v)to a vacant space on your new drive. While your at it, after the copy is complete, run grub in a terminal window - **sudo gru**b - and find the new drive in grub terms - **find /boot/grub/stage1**. Note that the output will find both the old and the new unless you remove the old drive. Plus the new instance of install will be unmistakenly found with the old drive removed. Now inserting the output of the find command type **root (hdx,y)**. Now **setup (hdx)** will write the grub boot record to the new hd. A reboot should allow you to boot to the new drive. Note two things. 1) You will probably have to edit menu.lst after booting to find win xp - **sudo gedit /boot/grub/menu.lst**. Hint - it probably be on (hd0,0). 2) The new install is identical to the old install includig UUID. Unless the drive with the new is 1st in boot order you won't be certain of which you are booting to. Likewise if you set the disk with the old install as 1st in boot order, you should be able to boot to it.

In summation your new disk should now be bootable to either windows or ubuntu through the grub boot menu. If things don't seem to be working right, post here again and someone should be able to talk you through it. 

Regards, Ron

---

