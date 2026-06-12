---
title: "Deleted contents of /etc/init.d"
date: 2006-08-29
forum: Desktop Environments
---

### Post by downforce on 2006-08-29
... and now what do I do?

Is there a way to restore these files/links? 

I've read some guide on restoring deleted files and they don't exist.

I'm scared to reboot the machine now!

Can anyone help or is it a complete reinstall?

---

### Post by lzydba on 2006-08-29
You could boot using the live CD and copy the files/links over from that.

---

### Post by astoltz on 2006-08-29
I know it's a long shot, but did you try the Wastebasket?

---

### Post by downforce on 2006-08-29
> **lzydba said:**
> You could boot using the live CD and copy the files/links over from that.

Well .. I mounted the iso and extracted the initscripts_2.86.ds1-6ubuntu32_i386.deb package to a tmp location. Within there was a /etc/init.d directory which I cp'ed to the real /etc/init.d. 

> **astoltz said:**
> I know it's a long shot, but did you try the Wastebasket?

What wastebasket? I'm using ubuntu-server, no gui, therefore I assume there isn't a wastebasket? locate didn't find anything.


I haven't rebooted to test yet, as I still need to extract all my services to stick in there, apache2, squid, bind blah blah. Once i've done that, i'll reboot and let you know how it went!

---

### Post by asplode on 2006-08-29
Ext3 filesystems are very adept at permanently deleting files.  It erases ALL metadata from each file, making it virtually unrecoverable.

---

### Post by downforce on 2006-08-30
> **asplode said:**
> Ext3 filesystems are very adept at permanently deleting files.  It erases ALL metadata from each file, making it virtually unrecoverable.

Yeah, I noticed that. I looked for all deleted files and I *know* I deleted some others (ones I really did want to) and they didn't show up.

I've since discovered a apt-get alternative called wajig. It has a "integrity" checker and low and behold it told me (all*) the files I was missing from /etc/init.d as it was trying to do something with them! 

Still need to go through and install the missing files though. Some a rather crucial, like cron! 

I'm seriously leaning towards a reformat. Setting those websites up again is going to be a complete <insert expletive>, thankfully I run a mysql backup script on a daily basis. 

((* - I think!!!))

---

