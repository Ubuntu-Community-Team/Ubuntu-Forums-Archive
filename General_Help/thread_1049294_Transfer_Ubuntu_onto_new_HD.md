---
title: "Transfer Ubuntu onto new HD"
date: 2009-01-24
forum: General Help
---

### Post by Valkhorn on 2009-01-24
Currently I have a dev box for my job that is 8.04 64-bit server edition. I have GNOME installed and all the other goodies as well. 

The thing is I initially installed Ubuntu on a 640 gig hard drive because I thought I could double this dev box as a file server. Eventually I got a separate Ubuntu box, used that as a file server, and so I want to move this drive to the file server while transferring Ubuntu to a smaller SSD drive.

So my question is this: How can I transfer everything already installed with Ubuntu over to the smaller SSD drive? I want to keep all of the MySQL data, PHP packages (including Pear), so I can't just copy the etc and home folders. 

I figure I could do this with a tar or something but I'm still only one year into Linux - so how does one do it? Is there a program built into the Ubuntu GUI that already does this?

Thanks!

---

### Post by dcstar on 2009-01-24
> **Valkhorn said:**
> Currently I have a dev box for my job that is 8.04 64-bit server edition. I have GNOME installed and all the other goodies as well. 

The thing is I initially installed Ubuntu on a 640 gig hard drive because I thought I could double this dev box as a file server. Eventually I got a separate Ubuntu box, used that as a file server, and so I want to move this drive to the file server while transferring Ubuntu to a smaller SSD drive.

So my question is this: How can I transfer everything already installed with Ubuntu over to the smaller SSD drive? I want to keep all of the MySQL data, PHP packages (including Pear), so I can't just copy the etc and home folders. 

I figure I could do this with a tar or something but I'm still only one year into Linux - so how does one do it? Is there a program built into the Ubuntu GUI that already does this?

Thanks!

If you are able to shrink the partition to fit on the SSD then you can use the partition manager to do that and then copy the whole partition as is (use a Live CD).

Once copied you can then grow the partition (if you want to).

---

### Post by Valkhorn on 2009-01-24
Well it can't hurt to try. The good thing is even if something happens on the new disk I'll still be able to boot off the old OS

*or*

Pop it into my linux fileserver's hot swap bay and get the data from there.

---

