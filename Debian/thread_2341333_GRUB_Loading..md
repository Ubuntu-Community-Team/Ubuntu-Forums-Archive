---
title: "GRUB Loading."
date: 2016-10-27
forum: Debian
---

### Post by danfryfisk on 2016-10-27
Hello,

Long time listener, first time caller.

I'm really struggling to get my server running. After a reboot a couple of days ago it would not boot up. 
At first it was stuck on Grub Minimal, Then I used Boot Repair and Grub Started but linux kernel header could not be found. 

Then after following may different forum posts I am stuck on GRUB Loading. Thats it, just says GRUB loading. 

I delete /dev/sda1 and recreate it on gparted as I thought that would fix it and that what caused GRUB Loading. Could somebody please take a look at this and help me out? 

[http://paste.ubuntu.com/23387463/](http://paste.ubuntu.com/23387463/)

Thanks in advance.

---

### Post by howefield on 2016-10-27
Debian Server ?

Moved to the "*Debian*" sub forum.

---

### Post by oldfred on 2016-10-27
Is this an older system, with a new very large hard drive?
Some BIOS do not like boot files beyond certain points.

You may want a smaller / partition and large /home or data partition(s).
But since server, you could use /boot partition and / as large partition. It may depend on what you are planning on using server for and if then it will install a lot of software or data in / or just files in /home.
Additional partitions require you to have some idea of use to size them correctly and then regular maintenance to make sure size is correct or housecleaning required.

       Updates, backups, delete old kernels - TheFu in Forums
[URL="http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs"]http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs
[/URL]
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/) 

[URL="http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs"]
[/URL]

---

