---
title: "Gparted Help"
date: 2009-02-18
forum: General Help
---

### Post by Chris^%$£&quot;! on 2009-02-18
Hello all,

I am having understanding problems of how to use this application, and after making a nearly 500gb swap partition, thought I would ask for some advice:
Have tried to attach a screenshot to illustrate.

I want to move my Ubuntu install to the large unallocated space, and remove the odd 2 48.3 partitions so I just have 1 big drive and the swap, thanks in advance for any assistance.

---

### Post by whoop on 2009-02-18
Can't you just first resize extended to use all space, then resize ext3 to use all space in extended?

---

### Post by taurus on 2009-02-18
First off, you cannot resize a partition, /, while you are using it.  So if you run gparted from Ubuntu, you cannot resize.  Therefore, you need to use gparted from either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Now, if you want to expand /dev/sdb5 to take up that unallocated space, you first need to expand the extended partition, /dev/sdb2, since /dev/sdb5 is a logical partition under the extended partition.  One you have expand /dev/sdb2 to take up that empty space, then you can expanded /dev/sdb5 to take up that space.  Again, you have to do all that from a LiveCD.

---

### Post by wildman4god on 2009-02-18
all the options you need you can get to by right clicking the partitions, just tool around alittle, thats the best way to learn anything, don't worry about messsing anything up the changes don't take effect untill you click apply so if you mess up just close gparted and you'll see everything back to the way it was. also try this website: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

it has a tutorial on how to use gparted, also in the future try googleing a problem first before asking for help, you can find many problem fixes online or in other parts of the forum and you can fix you problem faster than having to wait on us.

---

### Post by Chris^%$£&quot;! on 2009-02-18
Thanks very much for the advice.

---

### Post by Chris^%$£&quot;! on 2009-02-20
Hello, I followed the tutorial as advised very carefully, and resized the partitions as advised, Gparted told me this would take 6 hours, so I dutifully left it overnight to cook!
Just took a look at the machune and Gparted said all operations completed sucessfully.
Re-booted the machine to see:

Grub loading, please wait....
Error 22.

Machine just boots back to this error message every time, cannot even get a boot menu anymore to try and boot back in to windows to clear up this horrendous mess.

From brief reading elsewhere, I am getting the hint that Gparted has now destroyed the mbr.

Couple of points:
If I wasnt at all computer minded this would have left a very bad taste in my mouth and would have gone running back to microsoft with tales of Ubuntu woes.

In order to get more people to use Ubuntu it has to be more than trouble free  install novices need to be able to install and run the OS easily.

My personal opinion is that Ubuntu is great when it's working but is a nightmare when it isn't which isn't much different from Microsoft at the moment, there is a long way to go I feel.

Now, rant over, does anybody here know how to fix my PC, before I pull the disks and strip them back to bare metal and have to re-install my now broken Vista and then Re-install Ubuntu, any help much appreciated, thank you.

PS. Have been reading elsewhere that I need to go in to my bios now to get the PC to boot from my windows disk to repair what Gparted has done to my disks, would this be correct?

---

### Post by geirha on 2009-02-20
Error 22 means that GRUB no longer finds the partition where the grub-menu is located. Boot your ubuntu CD, run ```
sudo grub
``` in a terminal, then at the grub prompt, run ```
find /boot/grub/stage1
``` Does that return anything?

---

### Post by Chris^%$£&quot;! on 2009-02-20
Well I couldnt get into my DVD drive till going in to bios to get the door open.

Returned the following:

(hd1,2)

---

### Post by geirha on 2009-02-20
I see, with your previous setup, that would've returned (hd1,4) most likely. In the grub shell, run the following to tell grub which partition to find /boot/grub/
```
root (hd1,2)
```
Then, to save the new settings to the MBR again
```
setup (hd0)
quit
```
This is assuming GRUB is currently installed on the first harddrive (hd0).

Reboot, and GRUB should now work again.

---

### Post by Chris^%$£&quot;! on 2009-02-20
Thanks for that, ubuntu was setup on a second hard drive with vista on C: so should i use hd1 in the second command, thanks?

---

### Post by geirha on 2009-02-20
> **Chris^%$£"! said:**
> Thanks for that, ubuntu was setup on a second hard drive with vista on C: so should i use hd,1 in the second command, thanks?

GRUB is usually installed on hd0 no matter which drive you install ubuntu on. Unless you specifically told the installer to put the boot loader elsewhere, it is most likely on hd0 since hd0 is the first hard drive, and usually the first hard drive the BIOS will attempt to boot.

---

### Post by Chris^%$£&quot;! on 2009-02-20
Thank you very much that has fixed the problem for me, very much appreciated, saved me a sunny day inside, now going to dig my garden! all the best.

---

