---
title: "System freezes for 25 secs after desktop appears"
date: 2009-06-15
forum: General Help
---

### Post by jacktar on 2009-06-15
I have UNR 9.04 on my Aspire One netbook. I works fine apart from this annoying problem at startup.

The system boots up and the desktop appears and it looks ready for use. But after about 10 seconds there is disk activity for about 25 seconds, during which I can do nothing.

I have checked the logfile and started htop before it freezes, but that didn't help.

What can I do to trace this problem ?

---

### Post by jacktar on 2009-06-15
*bump*

---

### Post by procras on 2009-06-15
Looks like some intensive process is using swap. Look at your memory usage. 

Is this the SSD 6 Gb version with the low amount of RAM? or the HDD version with more RAM.

Try not to use the process that is eating up the memory.

Try to run the desktop as a new user (that you create) if this runs better then maybe some of the gnome start up files are corrupted. Delete them one by one until you find the culprit.

That desktop search thingy can be a real drag, turn it off. All that indexing takes time.

---

### Post by jacktar on 2009-06-15
What is the desktop search thing ? I was not sure if it was safe to delete everything from the startup menu, but I'll try that.

My system is the 8Gb SSD version, 1.5GB ram, ext2 and no swap partition.

---

### Post by procras on 2009-06-15
I found the [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne") info invaluable in setting up my Aspire One.

The search thing looks like a magnifying glass it tries to catalog all the files every now and again.

Most people would have the main installation on ext3 not ext2.

You really should have a swap partition!
Post the output of /etc/fstab

---

### Post by jacktar on 2009-06-15
This is my /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file sy
stem> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fc6d31ba-4421-4cb4-96c1-96c36faef048 /               ext2    relatime,errors=remount-ro 0       1
jim@jim-netbook:~$ 

I tried deleting things from startup but it had very little effect. I just re-installed UNR last week because it had slowed down so much. I used ext2 this time to avoid journaling. I think that with 1.5GB RAM I shouldn't need swap.

---

### Post by procras on 2009-06-15
Try and set up a swap file or partition now.
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by procras on 2009-06-15
From the community help pages [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")


> OPTIMIZING SSD PERFORMANCE:

    *

      Note: (Skip this step if you have the hard disk Acer Aspire One) 

The performance of the SSD drive can be significantly improved by a few tweaks described in an article by Jason Perlow (But ignore Tweak #1, which does not apply.). The most important of these are described here.

Change the file system mount options on SSDs to “noatime”

Edit /etc/fstab (gksudo gedit /etc/fstab) and change the the option “relatime” to “noatime”. The line for the root partition should then be something like:

UUID=f0ae2c59-83d2-42e7-81c4-2e870b6b255d / ext2 noatime,errors=remount-ro 0 1

Try to edit your fstab as above when you have swap set up.

---

### Post by procras on 2009-06-15
The search thingy :) is found in Preferances->Search and Indexing


If you are brave and not too ham fisted you can add some RAM.
[http://www.youtube.com/watch?v=-EfzckyZMTk]("http://www.youtube.com/watch?v=-EfzckyZMTk")

---

### Post by jacktar on 2009-06-15
I don't really have a problem with the speed of the system, it is quite fast. It's just that I have to wait half a minute after the desktop appears before I can do anything. (a bit like Windows)

---

### Post by jacktar on 2009-06-15
I already have the maximum ram (1.5GB)

---

### Post by procras on 2009-06-15
I have two AAO, one like yours and another with the HDD. 
Neither one gives this problem with the delay after I log onto the desktop.

* I think you really should have some swap.

* Disable the tracker (search thingy)

* If the delay persists, try creating a new user and logon to that account to see if the same thing happens. If that account is good then something is screwed up in your gnome startup files, session properties etc.

I have just timed login on my HDD AAO.
After I press enter after my password, it takes 22 seconds to see the UNR window with all the applications. But I can start clicking on the icons to start an application straight away.

---

### Post by jacktar on 2009-06-15
I created a new user but its still the same. I dont seem to have the tracker. I'll try adding a swap file when I can get the instructions printed out tomorrow.

Thanks for your help.

---

### Post by procras on 2009-06-15
I will time the password to UNR window appearnce on my SDD AAO tomorrow and post time when done.

---

### Post by jacktar on 2009-06-16
Used desktop switcher and totally lost my desktop. Reloaded UNR with a swap file this time and system is now ok.

---

