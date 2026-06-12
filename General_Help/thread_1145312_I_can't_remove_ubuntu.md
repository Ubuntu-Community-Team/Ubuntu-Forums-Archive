---
title: "I can't remove ubuntu"
date: 2009-05-01
forum: General Help
---

### Post by Sadguy on 2009-05-01
Hey there Ubuntu people :).

I have a problem here - I have been trying to remove my non-dual booted Ubuntu only OS on my computer for a really long time, but I can't get anything seem to work. I know it is sad that I am removing Ubuntu, but I really need to remove it for a short while. Can you people help me? I'll be thankfull :)

---

### Post by Legace on 2009-05-01
Do you have Windows (or an other OS) installed?
Are you using Wubi?

---

### Post by kestrel1 on 2009-05-01
If you don't have another OS installed, use the Live Ubuntu CD run Gparted & format the Ubuntu partitions or just remove them leaving free space to install another OS.

---

### Post by Sadguy on 2009-05-01
kestrel, can you explain in detail? I'm not very much into computers :)

---

### Post by miegiel on 2009-05-01
> **kestrel1 said:**
> If you don't have another OS installed, use the Live Ubuntu CD run Gparted & format the Ubuntu partitions or just remove them leaving free space to install another OS.

That will work, but you can also just install a new OS. Every OS installer (I know of) has a partitioner that lets you delete any partitions on your disk(s).

---

### Post by Sadguy on 2009-05-01
I have the Windows live CD, but it dosn't work with ubuntu. It comes with an error before I get to delete any partitions

---

### Post by kestrel1 on 2009-05-01
I have found that if a partition is set up with a Linux OS that Windows will sometimes refuse to install stating that it cannot find any suitable paritions. That is why I would remove the Linux partitions first.
To do this, start your machine with the Live Ubuntu CD & go to System -> Administration -> Partition Editor.
Select the partition/s that you want to remove & either format them as NTFS (For Windows NT & above or FAT32 (Windows 98 etc) or you could just click on Delete & remove the partitions leaving the free space for your other OS to use.

---

### Post by Sadguy on 2009-05-01
well, why do I need the live CD for that?

---

### Post by miegiel on 2009-05-01
> **Sadguy said:**
> I have the Windows live CD, but it dosn't work with ubuntu. It comes with an error before I get to delete any partitions

It doesn't need to work with ubuntu :) Just boot from the windows CD. You might need to set your PC to boot from CD's in the BIOS if your PC doesn't boot from CD's by default.

---

### Post by Legace on 2009-05-01
Do you want to completely wipe out all data from you disk?
Or do you have Windows (or other Linux systems) installed?

---

### Post by miegiel on 2009-05-01
> **Sadguy said:**
> well, why do I need the live CD for that?

If you don't boot from a CD but from your hard disk, you can't delete the partition ubuntu is running from. If you boot ubuntu (or anything else) from a CD the hard disk (partitions) won't be mounted and can be deleted.

---

### Post by Sadguy on 2009-05-01
But when I boot from the windows CD it just loads and crashes into an error message saying something with CHKDSK

---

### Post by kestrel1 on 2009-05-01
To run Gparted you either need the Ubuntu Live CD or the Gparted bootable CD. There are other options for partitioning your hard drive, but this is the best I have found so far.

---

### Post by kestrel1 on 2009-05-01
> **Sadguy said:**
> But when I boot from the windows CD it just loads and crashes into an error message saying something with CHKDSK
That is basically Windows moaning about the partition. Use my method. You will then be able to boot from the Windows CD once the hard drive is free.

---

### Post by Sadguy on 2009-05-01
So, I boot from the Live CD?

---

### Post by kestrel1 on 2009-05-01
> **Sadguy said:**
> So, I boot from the Live CD?
Yes, use the Live CD to boot & then run Gparted.

---

### Post by Sadguy on 2009-05-01
Thanks, here goes. And thanks to all of your for being to helping and overbearing with a computer rookie :)

---

### Post by kestrel1 on 2009-05-01
Good luck.

---

### Post by Sadguy on 2009-05-01
I found the Gparted, but I can't format to NTFS or unmount the partition

---

### Post by kestrel1 on 2009-05-01
Go to System -> Administration -> Partition Editor.
That is Gparted.
Alternativly type ```
sudo gparted
``` in a terminal.

---

### Post by kestrel1 on 2009-05-01
Sorry miss read your previous post.
The partition shouldn't be mounted unless you have mounted it.
If you highlight the partition you should get the option to delete it at least.

---

### Post by Sadguy on 2009-05-01
I have Gparted, I tried it before, but it seems I can't figure it out

---

### Post by Sadguy on 2009-05-01
Should I provide a screenshot to make things easier?

---

### Post by miegiel on 2009-05-01
> **Sadguy said:**
> I found the Gparted, but I can't format to NTFS or unmount the partition

You could try *fdisk*.
```
sudo fdisk /dev/sda
```
(assuming sda is the disk you need to change)

yay! screenshots \\:D/

---

### Post by Sadguy on 2009-05-01
"The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually." 

The message when i try to unmount

---

### Post by kestrel1 on 2009-05-01
Have a look at the screen shot.
You should see that when the partition is highlighted that Delete is available.[ATTACH]112031[/ATTACH]

---

### Post by kestrel1 on 2009-05-01
> **Sadguy said:**
> "The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually." 

The message when i try to unmount
If you are using the Live CD to boot your machine the drive shouldn't be mounted.

---

### Post by Sadguy on 2009-05-01
I messed around with the terminal until I changed the parition to NTFS or so it seems

it says "Changed system type of partition 1 to 86 (NTFS volume set)"

Is that good?

---

### Post by Ericyzfr1 on 2009-05-01
I would suggest that you consider Gparted LiveCD. Then you will be able to boot from the CD format you partitions or delete them and install your new OS.

---

### Post by Sadguy on 2009-05-01
If I could attach a screeny. Then I can show you what I see.

---

### Post by miegiel on 2009-05-01
> **Sadguy said:**
> I messed around with the terminal until I changed the parition to NTFS or so it seems

it says "Changed system type of partition 1 to 86 (NTFS volume set)"

Is that good?

Could be, give the windows install CD another shot

---

### Post by kestrel1 on 2009-05-01
> **Sadguy said:**
> If I could attach a screeny. Then I can show you what I see.
Yes you can attach a screen shot.
Use ALT - Print screen to save the active window as a screen shot. Then on the forum use the Advanced reply option & use the attach button to attach your screen shot.

---

### Post by Sadguy on 2009-05-01
I tried, but it crashed again.

And here is the screeny

---

### Post by miegiel on 2009-05-01
> **Sadguy said:**
> And here is the screeny

Is that a screenshot from ubuntu started with the* ubuntu live CD*?

---

### Post by Sadguy on 2009-05-01
oh no, I popped the windows back in, sorry. Do I have to restart the computer now?

---

### Post by miegiel on 2009-05-01
It make a difference because:

> **miegiel said:**
> If you don't boot from a CD but from your hard disk, you can't delete the partition ubuntu is running from. If you boot ubuntu (or anything else) from a CD the hard disk (partitions) won't be mounted and can be deleted.

---

### Post by Sadguy on 2009-05-01
aha. so I boot into the Ubuntu cd?

---

### Post by miegiel on 2009-05-01
> **Sadguy said:**
> aha. so I boot into the Ubuntu cd?

Yes, if you boot ubuntu from your harddisk the partition with ubuntu will be locked and you can't remove it.

---

### Post by kestrel1 on 2009-05-01
> **Sadguy said:**
> aha. so I boot into the Ubuntu cd?
I thought we said this earlier.
Use the Live CD to boot your computer. Then run Gparted.

---

### Post by Sadguy on 2009-05-01
I just booted into the CD and deleted the partition and run Gparted then I formatet the partition to NTFS and tried to run the windows CD but it crashed again. here\s what the Partition looks like now

---

### Post by test_test_testing on 2009-05-01
> **Sadguy said:**
> I just booted into the CD and deleted the partition and run Gparted then I formatet the partition to NTFS and tried to run the windows CD but it crashed again. here\s what the Partition looks like now

Try and delete the partition and start afresh.

GParted -> right-click /dev/sda1 -> find the menu item labeled '_D_elete' -> click it -> apply

Hopefully now you can boot using your Windows CD and create a partition from there.

Hope that helps.

---

### Post by Sadguy on 2009-05-01
I also tried that, it still crashed

---

### Post by test_test_testing on 2009-05-01
What's the exact error message you're getting? Can you write it down? What exactly do you mean by 'crashed' - did you need to hard-reset it? That might help us solve your problem.

---

### Post by Sadguy on 2009-05-01
Sure. I will be back soon

---

### Post by Sadguy on 2009-05-01
The message is follows 

STOP 0x0000007b(0xF6063848,0xC0000034,0x00000000,0x00000000

---

### Post by kestrel1 on 2009-05-01
> **Sadguy said:**
> The message is follows 

STOP 0x0000007b(0xF6063848,0xC0000034,0x00000000,0x00000000

Have a look at this artical & see if anything helps: [http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

---

### Post by kestrel1 on 2009-05-01
Just had a thought. Is your hard drive SATA? If so are you installing the SATA controller drivers or is the BIOS set up to make the drive look like an ATA drive?

---

### Post by Sadguy on 2009-05-01
One last thing before I stop bothering. If I get a new harddisk - will I then be able to install windows and solve my problem by replacing the harddisk?

---

### Post by Sadguy on 2009-05-01
It says ATA on my harddisk

---

### Post by kestrel1 on 2009-05-01
Why? do you believe that your drive is faulty?

---

### Post by Sadguy on 2009-05-01
Well, the reason that I installed ubuntu was because my vista failed and then I installed ubuntu since it was the only thing I had at hand and now that I want Ubuntu off my computer I can\t seem to get it off. I have been figthing this problem for about 4 months now and no forum could help and I come to think that my hard drive is faulty.

---

### Post by kestrel1 on 2009-05-01
It is a possibility. Download the drive testing tool from the drive manufacturer if there is one available. Most have them these days. This should tell you if the drive has some sort of fault.

---

### Post by Sadguy on 2009-05-01
And if I get a new drive. Would I then be able to just install windows?

---

### Post by BslBryan on 2009-05-01
Yes, that is correct.  You could write whatever you wanted to it.

---

### Post by Sadguy on 2009-05-01
Thank you all for the support. Seems I will have to buy a new hard drive and solve this problem another time. I\ll probally return tomorrow with some more questions. :)

---

### Post by kestrel1 on 2009-05-01
Yes as long as the other drive is actually faulty & that is the problem, which by the sound of it could be the cause. I would strongly advise you to try the manufacturers tool first though, before wasting money on a new drive. Some of these tools can perform a low level format of the drive that may fix the problem.
What make is your current drive?

---

### Post by miegiel on 2009-05-01
> **Sadguy said:**
> One last thing before I stop bothering. If I get a new harddisk - will I then be able to install windows and solve my problem by replacing the harddisk?

It might and it might not. I can imagine you're getting frustrated enough to consider getting a new disk. For example, if it's a [_Device Driver Issue_]("http://support.microsoft.com/kb/324103") using a different motherboard might help, but a different disk won't. 

Something else you could try is a *low level format*. On your harddisk's manufacturer's site you can download bootable live CDs with tools to test and wipe your disk.

---

