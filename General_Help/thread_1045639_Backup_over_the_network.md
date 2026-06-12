---
title: "Backup over the network"
date: 2009-01-20
forum: General Help
---

### Post by supanatral on 2009-01-20
I'm trying to find a good program that you guys would suggest to backup files over the network (preferably even if the file is open). Actually, if it can backup outlook pst files while outlook is open, that would be amazing! Also, these are all windows computers. Any suggestions?

P.S. I did some research and I found rsync, how would that work in the environment I described?

---

### Post by dcstar on 2009-01-20
> **supanatral said:**
> I'm trying to find a good program that you guys would suggest to backup files over the network (preferably even if the file is open). Actually, if it can backup outlook pst files while outlook is open, that would be amazing! Also, these are all windows computers. Any suggestions?

P.S. I did some research and I found rsync, how would that work in the environment I described?

Commercial programs that can backup open files are available, they are commercial because features like that are not easy to do and these programs costs hundreds of dollars.

rsync might do basic backups if you can get whatever client setup is required working on the Windows machines.

---

### Post by jonobr on 2009-01-20
Hello


Rsync could be considered more a secure file moving and transferring application, thats liteweight and easy to use.

You would have a machine that copies over the differences in files between the two machines and copies it copies over is very configurable, however, it sounds as if you are looking for an actual backup as opposed to a copying program.

I have tried sbackup before myself, it does work but its not 100%.

---

### Post by supanatral on 2009-01-21
Thank you for your help! so if I were looking into a better backup program that can accomplish backing up outlook, what is a good program to look at?

---

### Post by jonobr on 2009-01-21
Hi,


It seems you are really more worried about the pst in outlook then anything else.

If I could make a recommendation if outlook is your primary concern..
Heres some information for a backup tool from microsoft.

[http://office.microsoft.com/en-us/outlook/HA010875321033.aspx](http://office.microsoft.com/en-us/outlook/HA010875321033.aspx)

This software backsup to local or network devices.
You could do one of two....

Storing it to local, you could then use rsync to backup that file to your other machine, you could automate it, or manually do it, 
or when the back up is done, you could save it to your server as a file share.
You could do this by sharing a directory on your server.


I have not seen anything that would actively backup..........
Although I havent done a complete search.

---

### Post by sedawk on 2009-01-21
There are many expensive backup solutions out there (software and
hardware). If you do not want to pay (for the software) have a look
at the Amanda project - Amanda seems to be popular and can do cross-platform backups: [http://amanda.zmanda.com/](http://amanda.zmanda.com/)

---

