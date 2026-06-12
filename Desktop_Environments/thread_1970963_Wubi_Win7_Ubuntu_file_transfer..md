---
title: "Wubi Win7 Ubuntu file transfer."
date: 2012-05-01
forum: Desktop Environments
---

### Post by danebramaged on 2012-05-01
I have a dual boot setup on my laptop now after using Wubi under Win7.  12.04 is installed on the same partition and all is well.   I would now like to transfer everything from mydocuments, mymusic, mythis and mythat to the ubuntu subdirectories of Documents, Pictures, Video that we typically find under the /Home directory of the Linux file system.

Am I going to have to pull everything off of windoze with a thumb drive, dual boot and move it back after dual booting into ubuntu or is there a more straight forward method.  

These files are all on the same disk and, they are all on the same partition because I used Wubi.exe.

Any suggestions would be appreciated.

thanx

---

### Post by bcbc on 2012-05-02
You windows host partition is mounted on /host

I don't recommend copying your data files to your /home directory though, because Wubi uses a virtual disk (root.disk) that is a single file stored on your Windows partition. And when you copy files to Ubuntu, they are stored within this single file. That works fine, but there is a higher risk of data loss if you have file system corruption (e.g. from a hard shutdown).

If you do copy files to /home then consider using Ubuntu One or take regular backups. Or consider doing a normal dual boot (not with Wubi).

PS if Ubuntu does freeze, resist the urge to power off. Use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") instead.

---

### Post by danebramaged on 2012-05-02
Thanks for the info ...

I'll probably pull everything across a USB port to spare drive and put it in my sock drawer.;)

tayl

---

