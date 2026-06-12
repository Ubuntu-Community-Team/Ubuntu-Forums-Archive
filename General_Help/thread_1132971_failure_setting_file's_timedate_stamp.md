---
title: "failure setting file's time/date stamp"
date: 2009-04-22
forum: General Help
---

### Post by NickBtheITguy on 2009-04-22
I support a software program that will typically support being installed to a share on a linux machine. The only requirements are that the Kernel version is 2.4.2 or higher and Samba is at 2.2.3a or higher.

I've been working with one of our customers who is running Ubuntu 8.04 Server as a file server. The workstation is Windows XP Pro SP 3. The end user has Admin rights to the XP machine. The user also has full control to the share on the linux machine. Running AVG 8.5 on the workstation but the resident scanner is off during install.

During updates to our program, which writes to the share on the server, we are finding that we get the message "failure setting file's time/date stamp." Is there a rights issue at the server level that could cause this message? Any other ideas that we might look at for this message?

---

### Post by StuartN on 2009-04-22
There is a bug [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/315552](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/315552) in Nautilus, cp, rcp etc that prevents Ubuntu from setting the time when a file is copied from ext3 to NTFS. The date stamp is the time (according to the receiving system's clock) at which the transfer occurred.

rsync is not affected, so dates are preserved. Dates are also preserved when transferring from NTFS to ext3.

---

### Post by NickBtheITguy on 2009-04-22
Thanks for the bug link. We found out that the files that were having the problem were owned by a different user so we ended up doing a chown on the directory. This took care of his issue.

---

### Post by StuartN on 2009-04-22
> **NickBtheITguy said:**
> Thanks for the bug link. We found out that the files that were having the problem were owned by a different user so we ended up doing a chown on the directory. This took care of his issue.

Thankyou so much! This issue has bugged me since I installed Ubuntu. Now I have added uid= to my mount and dates are preserved in terminal and Nautilus:

sudo mount -t cifs -o username=<user>,password=<password>,uid=stuart server:data data

It might sound really, really obvious but if uid= is not specified then the mount point looks identical and all files *appear* to belong to the logged in user. But during a copy the ownership is reassigned and then reverts to the logged in user - but crucially the change of attributes occurs while you do not own the file. I found this thread after reading your answer [http://www.linuxquestions.org/questions/debian-26/preserving-time-operation-not-permitted-on-fat32-on-debian-135951/?](http://www.linuxquestions.org/questions/debian-26/preserving-time-operation-not-permitted-on-fat32-on-debian-135951/?)

---

