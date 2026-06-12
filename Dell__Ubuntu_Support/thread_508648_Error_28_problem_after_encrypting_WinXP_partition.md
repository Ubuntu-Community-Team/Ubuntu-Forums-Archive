---
title: "Error 28 problem after encrypting WinXP partition"
date: 2007-07-24
forum: Dell  Ubuntu Support
---

### Post by sbumgarner on 2007-07-24
I have a Dell Inspiron 1505E laptop dual booting WinXP MCE and Xubuntu 7.04. All worked fine until I encrypted my WinXP partition with Utimaco SafeGuard Easy (required by my company). Now when I try to boot to Xubuntu, I get a message that reads "Error 28: Selected item cannot fit into memory." I don't have a clue what to do. I have a call to Utimaco but suspect they won't have a clue either.

I can access my WinXP partition just fine, and that partition displays a key icon indicating encryption. None of the other partitions shows that icon.

Anyone have any ideas?

Thanks,
Stan

---

### Post by ridgeland on 2007-08-16
Did you solve this and get back on track with Linux?

If not,
Can you boot a Linux live CD?  I don't remember if Xubuntu is a LiveCD or just an install CD.
Did you have the Windows partition visible in Xubuntu?  If so did you change /etc/fstab to take it out?

---

### Post by captevo on 2007-08-29
I have the same problem.
LiveCD did not see the drive, even Gparted Live CD couldn't see drive.
Any idea?

---

### Post by ridgeland on 2007-08-29
If you encrypted the Win partition isn't this exactly the result you want?
Any OS, LiveCD etc should now be blocked from seeing the partition.

---

### Post by twenty20 on 2008-02-05
I have the same problem. I did however have a working configuration with Winxp, Ubuntu 6.10 and the disks encrypted with safeguard 4.2. 
But now with Ubuntu 7.10 i get error 28 in grub while trying to boot Ubuntu ( xp boots fine)
Next I´m gonna try an older version of grub, the one that came with 6.10 and see if that helps.
Btw i´m on a ibm thinkpad

Here is one workaround that boots grub on another disk ( USB stick) and then boots the drive with xp,sge
[http://ubuntuforums.org/showthread.php?t=664401&highlight=safeguard](http://ubuntuforums.org/showthread.php?t=664401&highlight=safeguard)

Another more compilcated workaround
[http://keitin.net/jarpatus/articles/safeguard_easy_grub/index_fin.shtml](http://keitin.net/jarpatus/articles/safeguard_easy_grub/index_fin.shtml)

---

