---
title: "Disk Usage Analyzer Wrong"
date: 2009-04-21
forum: General Help
---

### Post by haok on 2009-04-21
Hi All

I'm currently running 8.10. I have /home on a separate partition.

I have a problem with Disk Usage Analyser showing wrong storage figures for /. It says I have used 14GB but the real figure is more like 8 GB.  It seems to have robbed me of at least 6 GB. Are there any solutions for this weirdness?

Recently, because of this wrong figure, Ubuntu would not allow me to fully boot until I created more space for /. I did this with gParted and was able to resume work.

Thanks Henry

[IMG]http://www.bigjolt.com/images/disk.png[/IMG]

---

### Post by John Cheng on 2009-04-21
It is possible that the drive that is mounted at "/" (root) has a /home folder that contains 6 GB of data. If this guess is true, when your computer mounts the other drive at "/home", it prevents you from seeing the "missing" 6 GB of data.

Boot using your Ubuntu CD or some other safe method and mount your "/" (root) drive at /mnt/root_drive. Do not mount "/home".

What is the result of the "df -h" command? What is found at /mnt/root_drive/home?

---

### Post by Slim Odds on 2009-04-21
How did you get the "real" value?

---

### Post by haok on 2009-04-21
My mistake ~ the 'real' value should be 3.7 GB. 

I think that the culprit is explained here - [https://bugs.launchpad.net/ubuntu/+bug/217389]("https://bugs.launchpad.net/ubuntu/+bug/217389")

I use Simple Backup and write to a network location 'lacie2'. However, sometimes it's not mounted and I think Simple Backup is writing it to /media/lacie2/System_Backup_Ubuntu on the local drive. 

I can see this directory in File Browser now eventhough the network drive is not mounted. How can I check it's contents and see if it has any volume? It has root permissions and does not allow me open it.

---

### Post by haok on 2009-04-21
Indeed, that was the issue as I described above. 

I changed the ownership using chown and then found the backup files. I have deleted them. My filesystem is now a lot healthier. 

Thanks for your help.

---

