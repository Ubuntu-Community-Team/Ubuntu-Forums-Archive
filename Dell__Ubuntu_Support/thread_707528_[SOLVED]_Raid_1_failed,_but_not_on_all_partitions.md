---
title: "[SOLVED] Raid 1 failed, but not on all partitions?"
date: 2008-02-25
forum: Dell  Ubuntu Support
---

### Post by check on 2008-02-25
I have a bit of a unique situation, or at least i havent been able to find other posts about this on the forums or on google etc.

I have a basic raid 1 config with just 2 serial ata drives. I used mdadm originally, I did it during the install of my ubuntu 6.06 server. Im using the server as a web server so I really wanted to have some redundancy.

The other day I restarted the machine for maintenance and noticed that a couple of the partitions were only booting with 1 drive. I am somewhat new to ubuntu, ive been working with windows for years though so the concepts are all there. 

Anyway here is the output

root@server1:/home/thorst# cat /proc/mdstat
Personalities : [raid1]
md3 : active raid1 sda7[0]
      233335936 blocks [2/1] [U_]

md2 : active raid1 sda6[0]
      9767424 blocks [2/1] [U_]

md1 : active raid1 sda5[0] sdb5[1]
      979840 blocks [2/2] [UU]

md0 : active raid1 sda1[0]
      56128 blocks [2/1] [U_]

unused devices: <none>

as you can see on the md1 both drives are active but the rest aren't.

What is the best way to get the others online. Please be as descriptive as possible if you could....like i said i am fairly new. Has the drive failed, aka do i need to contact dell to get a parts replacement. Or is it just some bad partitions.

If your wondering why im posting in this forum its because my machine is a Dell Power Edge 440SC.

Thanks for any help

---

### Post by check on 2008-02-26
see this post if you are having the same issue.....


**[http://www.howtoforge.com/forums/showpost.php?p=75633&postcount=5](http://www.howtoforge.com/forums/showpost.php?p=75633&postcount=5)**

---

