---
title: "Bug in sbackup"
date: 2011-04-28
forum: Desktop Environments
---

### Post by paul_a_bennett on 2011-04-28
For a while, I've been having trouble figuring out how to configure sbackup correctly, as it never seemed to do what I wanted it to.  I've finally figured out that sbackup's configuration GUI appears to have a bug in it.

Let me explain.

I wanted to set up daily backups.  I used the GUI to do so, setting the backup time to 00:30 daily.  When I clicked 'Save', a dialog informed me that the save had been successful.  However, I noticed that the machine continued to slow down every hour and a check of the backup media verified that a backup was being done every hour of every day.

Tracking through things, I uncovered the file [FONT="Courier New"]/etc/cron.d/sbackup[/FONT] which the sbackup configuration GUI writes.  It contained the line:

[FONT="Courier New"]30 * * * *	root	if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;[/FONT]


(i.e., backup every half hour of every hour of every day - not what was intended!)

Of course, I restarted the sbackup configuration GUI again, and sure enough, it indicated that backups were to be done hourly on the half hour.

I changed the value to hourly (again) and sent the time to 00:30.

Again I saved, again I was told that the save was successful.  Immediately on checking the file [FONT="Courier New"]/etc/cron.d/sbackup[/FONT], I noticed that the line had reverted to the same as above:

[FONT="Courier New"]30 * * * *	root	if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;[/FONT]

On a whim, I entered the sbackup configuration GUI again and set the time to 01:30, daily.  Immediately checking [FONT="Courier New"]/etc/cron.d/sbackup[/FONT], I noticed that the line now read:

[FONT="Courier New"]30 1 * * *	root	if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;[/FONT]

(i.e., do the backup at 01:30 every day: what WAS desired!)

From this I conclude that there is a bug in the sbackup GUI which causes it to assume that a 0 hour (midnight) should be written as a '*' instead of as a '0'.

Two conceivable workarounds suggest themselves:

Never use the sbackup configuration GUI to set a time between midnight and 01:00. (Set it to some time after 01:00.)

Alternatively, edit the file [FONT="Courier New"]/etc/cron.d/sbackup[/FONT] by hand and replace the first '*' (in the second position) by a '0' and NEVER USE THE SBACKUP CONFIGURATION GUI AGAIN unless you're going to set a time after 01:00, or you'll be back in the same pickle that I was in.

Hopefully the kind author of sbackup can resolve this small problem in the next release.

---

