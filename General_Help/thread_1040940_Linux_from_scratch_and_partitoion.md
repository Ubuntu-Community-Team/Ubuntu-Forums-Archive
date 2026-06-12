---
title: "Linux from scratch and partitoion"
date: 2009-01-16
forum: General Help
---

### Post by Saeen on 2009-01-16
Hi
this is goin to sound real stupid...but i want to try out the LFS system, no real experience with Linux based systems but i can find my way around usually. Anyways when i installed Ubuntu i created a drive mounted at / and a swap space + i also created another drive and mounted at /usr with ext3.
The book requires ext2 so i wanted to delete that partition and recreate it, after a little googling around i got here:
[B]junaid@ALM:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda6             11811996    499628  10712344   5% /
tmpfs                   511964         0    511964   0% /lib/init/rw
varrun                  511964       104    511860   1% /var/run
varlock                 511964         0    511964   0% /var/lock
udev                    511964      2744    509220   1% /dev
tmpfs                   511964       488    511476   1% /dev/shm
lrm                     511964      2000    509964   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda8              4411616   1833276   2354236  44% /usr
/dev/sda5             20707752  20475324    232428  99% /media/New Volume
/dev/sda1             17406392  16340892   1065500  94% /media/disk
[/B]

This shows that drive mounted under /usr is 44% used even though i havnt stored anything thr. So possibly since drive under / is used 5% that means ubuntu installation used the other drive? How can i solve this problem, any help would be much appreciated as i cant wait to start with my LFS experience. Thank You

---

### Post by dcstar on 2009-01-16
> **Saeen said:**
> 
........
This shows that drive mounted under /usr is 44% used even though i havnt stored anything thr. So possibly since drive under / is used 5% that means ubuntu installation used the other drive? How can i solve this problem, any help would be much appreciated as i cant wait to start with my LFS experience. Thank You

/usr is a SYSTEM folder that has NOTHING to do with user data. You do not touch it under any circumstances, program data essential to the proper operation of you system is stored there.

You should create a new directory on your root folder (like /usr2), copy every file from /usr into it (ensuring all permission are the same), then reboot with a Live CD, mount that partition and rename the /usr2 folder to /usr.

Then edit the /etc/fstab file on that partition so /usr is **not** mounted on that other partition.

After a normal boot you then can use the old /usr partition for whatever you like.

---

