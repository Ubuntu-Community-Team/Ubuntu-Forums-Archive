---
title: "[SOLVED] Synchronizing data partition &amp;amp; backup HD"
date: 2006-10-25
forum: Desktop Environments
---

### Post by wieman01 on 2006-10-25
Hello, 

My idea is to sychronize my data & my backup partition, but I don't know what's the most convenient/reliable tool I ought to use. Any suggestions are welcome.

One restriction, however: My backup HD is running only on occasion. So a sync process should only run on demand, not automatically during startup.

Thanks in advance!

---

### Post by wieman01 on 2006-10-26
It appears to me that "rsync" is the right choice for backups. I am using Unison/SSH for synchronizing laptop & desktop, however, for simple backups (one direction) "rsync" seems to do the job.

Any comments? 

I'll give it a go anyway.

---

### Post by sv452 on 2006-10-26
hi,

mind telling me how u using rsync ?? i have a mobile usb hdd for use between my work pc and my home pc... i mainly wanna have my /var/cache/apt/archives folder to be synced between the two pc's - but it would be marvelous if it can work for backups between the two as well...

thanx

SV452

---

### Post by wieman01 on 2006-10-26
Synchronized (both directions) or a simply backup (only either direction)?

Unison is a great tool for synchronization. I'll check out "rsync" today or tomorrow & get back to you on this.

---

### Post by sv452 on 2006-10-26
well, when it comes to my /var/cache/apt/archives backup i recon is only either direction since i have to sync my work pc with the usb drive and then i will have to sync my home pc again with the usb drive.

i'll check out unison and see what it does ...

laterz then....

---

### Post by wieman01 on 2006-10-26
Understand... This is a superb howto for Unison: [http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html]("http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html")

---

### Post by wieman01 on 2006-10-26
RSync comes preinstalled and is super-simple. Simply had to run this command to synchronize data & backup partition:
> rsync -avrb --delete /data/ /media/sda1/
"--delete" will delete files on the backup partition that have been removed on the source partition (data). Works flawless.

---

