---
title: "Boot fails"
date: 2009-03-28
forum: General Help
---

### Post by Erik. on 2009-03-28
Hello,

I had some problems installing ubuntu.
I am using 3 hdd's 

1 for windows
1 for ubuntu and the last one for my data etc.

After installing ubuntu i had boot problems, booting the wrong hdd.
I fixed the problem.

After 2 days i got another problem.
I want to boot ubuntu, i got my loading bar.
Then i get a black screen whit text on it.

I made a photo of it and you can find it in this post.
I really do not know what the problem is.

What could be the problem of this boot?

I also had some other problems,

I have an geforce 6600 video card, ubuntu gave me some drivers, the last one was recommend so i used that one, the 7xx am i right?
After a shutdown i got a boot fail, something whit the x server, after a reboot and system check everything worked fine.
I always needed to boot 2 times.

Hope you can help me.

---

### Post by drs305 on 2009-03-28
Regarding the stale NFS error, have you tried booting to the recovery mode and running fsck? Are you even using NFS?

---

### Post by Erik. on 2009-03-28
No i did not run the recovery mode, i do not have an menu at the boot, only grub loading and then ubuntu loading.
Do i need to go into the menu at booting?

I do not use NFS, never used also.

---

### Post by drs305 on 2009-03-28
If you don't see the grub menu, after the system boots (you may hear a beep) start hitting ESC and the grub menu may appear. Hopefully you will get the grub menu with a *Recovery mode* option. In the recovery mode one of the options should be to perform an fsck check. If you don't get that option, or if you have to boot from the livecd, run fsck from the command prompt, specifying your system partition.

---

### Post by Erik. on 2009-03-28
Oke, i will take an try.

The wierd thing is, every time i want to boot my pc i got the x-server error.
Then the system does an disk check, that is the same one i am now going to do.
Could there be some other problem?

---

### Post by Erik. on 2009-03-28
Update:

I can try what i want, it does the check but after the reboot i still have the same problem.

I made some screen shots whit my phone, hope you can see some information we need.
Could it be that my hdd is to old and going to crash?

Little translation for photo 2

Server indification foler (deamon/ServAuthDir) is set on /var/lib/gdm but is does not exists Configure the GDM and restart GDM

---

