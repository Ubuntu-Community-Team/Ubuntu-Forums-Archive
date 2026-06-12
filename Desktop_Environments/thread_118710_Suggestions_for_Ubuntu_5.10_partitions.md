---
title: "Suggestions for Ubuntu 5.10 partitions"
date: 2006-01-17
forum: Desktop Environments
---

### Post by gbold on 2006-01-17
Greetings all-
I'm a Linux newbie who is trying to set up an Intel P3-850 computer with 512MB RAM, 2 WD-40GB hard drives on a Promise Controller, ATI 9250 video card and an Asus CUV4X-C motherboard.  I have the Ubuntu 5.10 install disk and have been playing around with it and have been learning a lot.  As a Windows user, it's been a lot more fun...

My question is what would you recommend for setting up my partitions to utilize both disks, ie, put what partitions where...?  I plan on using this for a webserver in the future for my American Cancer Society Relay for Life website.

I have read as much as I can on the subject and I'm not sure what sizes/partitions to break out...  Iwas thinking along the lines of:
/ (root) 10GB on drive 1
/usr      20GB on drive 1

swap     1 GB on drive 2
/home    20 GB on drive 2
/var       rest of space on drive 2

Any help is certainly appreciated and thanks in advance.
Greg

---

### Post by j_monty10 on 2006-01-17
[QUOTE=gbold]Greetings all-
I'm a Linux newbie who is trying to set up an Intel P3-850 computer with 512MB RAM, 2 WD-40GB hard drives on a Promise Controller, ATI 9250 video card and an Asus CUV4X-C motherboard.  I have the Ubuntu 5.10 install disk and have been playing around with it and have been learning a lot.  As a Windows user, it's been a lot more fun...

My question is what would you recommend for setting up my partitions to utilize both disks, ie, put what partitions where...?  I plan on using this for a webserver in the future for my American Cancer Society Relay for Life website.

I have read as much as I can on the subject and I'm not sure what sizes/partitions to break out...  Iwas thinking along the lines of:
/ (root) 10GB on drive 1
/usr      20GB on drive 1

swap     1 GB on drive 2
/home    20 GB on drive 2
/var       rest of space on drive 2

Any help is certainly appreciated and thanks in advance.
Greg[/QUOTE]

I don't know if you need to split /var /usr off of /
10gb is usually plenty for / including /var and /usr, but if you want to be safe you could do something like:
Drive 1
/        15 or 20gb 
/web   remaining space
Drive 2
swap   1 GB
/home  20GB
/backups    rest of space 

This will let you backup your important directories using rsync or another utility.  Also, from personal experience, don't mess with /etc/fstab until your system is stable.  Here is a good [tut ]("http://www.ubuntuforums.org/showthread.php?t=46866&highlight=move+home+directory+partition") that will help you with setting up fstab once you have your system stable.  Good luck and hope your linux journey is as fun as mine has been.

---

### Post by fourchannel on 2006-01-17
you might check into LVM, to let you merge the drives together, fluid resizing of partitions. Kinda complicated and I have no idea how to set it up.

---

### Post by healychan on 2006-01-17
[QUOTE=j_monty10]Drive 1
/        15 or 20gb 
/web   remaining space
Drive 2
swap   1 GB
/home  20GB
/backups    rest of space [/QUOTE]
I don't think today's computer need 1GB swap area, it is kind of waste....
Even though you have only 64MB of RAM, 1GB swap is still too much.
My old laptop has 128MB of RAM with 128MB swap works perfectly under normal circumstance( browsing web pages, word processing, small programming....etc )

Remember that the system use swap only when you are out of physical RAM.

---

### Post by gbold on 2006-01-17
Thanks for the replies.  I just wanted to utilize both drives in a way that I don't run out od room for anything.  The website I'm hosting has lots of pictures and I wanted to be able to get off of Comcast since they don't support mail from the site (I'm going to try and set up a mail server also...).
Thanks j_monty10... your reply was along the lines I was looking for.
Greg

---

