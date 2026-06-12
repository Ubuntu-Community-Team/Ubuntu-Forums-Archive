---
title: "Script wont work under cron but does normally!"
date: 2005-11-30
forum: Desktop Environments
---

### Post by pabc on 2005-11-30
Morning.

I have a strange problem.

Crontab;
```
# Daily reboot at 5am
00 05 * * * admin sudo reboot

# Daily backup at 4am
00 04 * * * admin sudo /home/admin/backup_logs

# Daily backup at 4:01
01 04 * * * admin /home/admin/backup_medchem
```

the backuplog script works fine but the backup_medchem seems to prematurely exit.

When I run the backup_medchem directly it works fine producing a 100MB tar.gz but when run from cron it produces a 50MB tar which is corrupt.

I set a crontab entry to a time when I could watch it and the tar file starts to get created then 10 or 11 seconds in the script just quits leaving the incomplete tar.

backup_medchem;
```
#!/bin/sh

# script to backup /var/www and to tidy up log files
webfilename=web_$(date '+%d-%m-%y')

# backup the website
cd /var/www/
tar -cvvf /home/admin/$webfilename.tar *
gzip -3 /home/admin/$webfilename.tar /home/admin/$webfilename.tar.gz

rm /home/admin/$webfilename.tar
```

Anyone any ideas on why I get this behaviour?

P

---

### Post by frodon on 2005-11-30
Do you use root crontabs ? (sudo crontab -e command)
Did you get any error messages when the tar file starts to get created ?
You could try to create a debug file wich could contain the error messages, using a line like that : ```
tar -cvvf /home/admin/$webfilename.tar * >& debug_tar.txt
```

---

### Post by pabc on 2005-11-30
Hi,

I added the cron jobs by directly editing system crontab (/etc/crontab) rather than adding them to indivual user crontabs (/var/cron/tabs) for ease really as one backup job runs as admin and one as root.

I've now changed the tar command to 

```
tar -cvvf /home/admin/$webfilename.tar /var/www/ 
```

and it works fine running directly or via cron. I dont understand it but I'm happy now.

---

### Post by Bil-E-daKid on 2006-11-24
Hey there,

I'm this exact same thing happen on three different ubuntu boxes - 2 edgy, 1 dapper server. 

Does anyone have any idea why this would be? script or command works fine if run manually but doesn't out of the root crontab.  Although, the dapper one was working mostly and has recently stopped working at all.

Really odd - no updates, no changes to crontab file etc.  It just stopped making a complete tar file.

---

### Post by guruofquality on 2006-11-24
> **Bil-E-daKid said:**
> Hey there,

I'm this exact same thing happen on three different ubuntu boxes - 2 edgy, 1 dapper server. 

Does anyone have any idea why this would be? script or command works fine if run manually but doesn't out of the root crontab.  Although, the dapper one was working mostly and has recently stopped working at all.

Really odd - no updates, no changes to crontab file etc.  It just stopped making a complete tar file.

This happens a lot to me, and in all distros. It seems that the PATH env variable for you and your shell is not the same for the root crontab. Therefore, the script you wrote may not be able to find certain binaries it needs to execute when run by the root's crontab. I usually specify an absolute path for each binary in my cron job scripts.

---

### Post by Bil-E-daKid on 2006-11-24
Hey there guru,

Thanks for that - I'll give it a go.

It does seem odd that it partially completes the process but seems to give up during the tar process once it's done a little tarring.

Maybe it equates to how much of the stuff fit into it's memory space before it needs to spawn the compression program and parse the output through - and it can't find that bit so it just writes what it's got so far to disk and ends.

Odd.  Thanks again though - I will try your suggestion.

:-)

---

