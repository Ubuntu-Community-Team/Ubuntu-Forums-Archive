---
title: "Webalizer using Crontab Problem"
date: 2009-02-20
forum: General Help
---

### Post by thomsonm on 2009-02-20
I'm running Ubuntu Server 8.10 (logged in as root) and I've got Squid installed and configured to work with Webalizer just fine. I can manually run webalizer and add the new data to my charts. My problem is trying to get get Webalizer to run every hour using crontab so that it updates automatically. It seems no matter what I try it just won't run.

At Terminal I type:
crontab -e
Then I've tried all the different lines below:
0 * * * * /usr/bin/webalizer
0 * * * * /usr/bin/webalizer -p
0 * * * * /usr/bin/webalizer -c /etc/webalizer/webalizer.conf
(the last line was reported to work in the Ubuntu forums but it doesn't for me)
And I've tried many combinations of minutes and hours. I even read that you need a carriage return at the end of the last line of code (sounded sketchy but I've tried everything so why not), this didn't solve the issue either.

In crontab after my webalizer line I also have the line:
59 23 * * * /etc/squid/rotate.sh
This works perfectly fine. It rotates my logs to another directory and renames them (based on the date), creating a new blank log for the next day.

Any help/suggestions would be greatly appreciated.

---

