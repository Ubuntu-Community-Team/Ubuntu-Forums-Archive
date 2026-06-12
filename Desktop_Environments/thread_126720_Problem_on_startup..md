---
title: "Problem on startup."
date: 2006-02-07
forum: Desktop Environments
---

### Post by Janzuka on 2006-02-07
When starting the computer, and ubuntu is loading. There occured a problem there, it fails mounting local filesystems. I have absolutely no idea what that means, and everything seems to be working well. But the question is, what am i supposed to do with that. How do i fix it, or is it even necessary?

---

### Post by zxee on 2006-02-07
Can you take a look at the output of 'dmesg' from a terminal/shell and maybe post it here? Also are you dual booting with windows? Ubuntu should be able to load other filesystems unless the partition table is corrupted/unreadable.

---

### Post by taurus on 2006-02-07
And if you can get to a terminal, then either look at your /etc/fstab to make sure everything is fine in there and if you are not sure, just paste it here and somebody will have a look at it for you.  Also, it would be real helpful if you can specify which partitions are for Ubuntu/Windows...

To view it, type

more /etc/fstab

To edit it, type

sudo gedit /etc/fstab
-or-
sudo pico /etc/fstab

---

### Post by Janzuka on 2006-02-07
Ok. I followed your instructions as well as i could. At first, zxee when you talk about output of 'dmesg',is it simply viewed by typing 'dmesg'? I was wondering that because the list that appeared was pretty long.If it's it i'll somehow link it here or something. And yes i am dualbooting with windows. I suppose that Ubuntu has been able to load them, because the problem just occured. Taurus, i think that i was able to do according to your advice, i checked out the  /etc/fstab and i think that i located the problem in there, it's the following,correct me if i'm wrong. 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
     /dev/hda5          /                         ext3    defaults,errors=remount-ro 0       1


This is the partition where i am running Ubuntu. No errors appeared in other partitions.

Thank you, and if you need more information to locate the problem, i will give it to you.

---

### Post by Janzuka on 2006-02-13
Hello,

The weirdest thing happened with this mounting thing. I was starting my computer, and during boot an announcement appeared telling me that the system had been rebooted 30 times without being checked, after that it fixed the system, and the problem disappeared. \\:D/

---

