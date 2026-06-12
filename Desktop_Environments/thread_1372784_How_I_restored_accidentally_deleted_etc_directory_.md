---
title: "How I restored accidentally deleted /etc directory from backups"
date: 2010-01-04
forum: Desktop Environments
---

### Post by dgermann on 2010-01-04
Hi--

Last night I did it. After probably 5 years of using linux, I managed to accidentally delete my /etc directory. Here's what worked for me--ymmv--it took me a couple of hours to figure out what to do, but if you do these steps it should be lots shorter for you:

1. I started out with a fairly up to date backup of my /etc directory--it was about 2 weeks old. These I make automatically with a cron job using rsync.

2. Place live CD in the drive. (I am running 8.04.1.)

3. Ctrl-alt-delete would not restart the system. Had to manually pull the power and restart.

4. Started live CD in safe graphics mode (I have dual screen using nvidia, and using the standard mode gave me a screen that was unreadable).

5. Went to terminal and created mountpoints:
sudo mkdir /media/main
sudo mkdir /media/sdb1

6. sudo gedit /etc/fstab, and copied the mount lines for these two hard drives from the backup files I had, one character at a time.

7. sudo mount -a

8. rsync -av /media/sdb1/route/to/etc/ /media/main/etc
(Note the trailing / on the source only.)

9. sudo reboot

10. removed live cd when it ejected.

I then seemed to be back in business.

The only glitch I found--firefox would not start. Tried it from command line and got "Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*."

I fixed this with: sudo xulrunner-1.9 --register-global 

I do not guarantee this will work in your situation, but I thought it might be useful to others in the same predicament--or me if I do it again!

---

### Post by kellemes on 2010-01-05
Just bookmarked your post ;-)

---

### Post by dgermann on 2010-01-05
kellemes--

Thanks.

I hope it helps someone some day!

---

