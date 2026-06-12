---
title: "sudo cron - error (grandchild #1234 failed with exit status 126"
date: 2011-08-02
forum: Desktop Environments
---

### Post by fritserasmus on 2011-08-02
I have a desktop environment with Apache2.

(If someone asks why desktop to run Apache2, its because the desktop must display a local website)

When I update the html files from a windows box it is being copied in a home/user folder.

Cron now has to copy the files with r to the localhost area.

sudo cp -R home/myself/Downloads/* /var/www/      works fine:

The script containing just that one line is in a file in my /home/myself/Documents folder named: copy_site_localhost.

Cron entry in turn was created with the command: sudo crontab -e and the entry is:
*/10 * * * * /home/myself/Documents/copy_site_localhost

The error in the syslog file in /var/logs is as follows:
[COLOR="Blue"].......CRON[1234] (root) CMD (home/myself/Documents?copy_site_localhost)
.......CRON[1236] error (grandchild #1234 failed with exit status126)
.......CRON{1236] info (No MTA installed, disregarding output)[/COLOR]

Any pointers/advice as how to fix this would be appreciated.

I also want to add a backup procedure of the folder that will TAR and RAR the folder, add a date stamp and move to a separate folder that will keep all the backup RAR files and then send an email to list succesfull steps

If anyaone can help or give me pointers so I can get it to work I would be very glad.

Kind Regards

Frits

---

### Post by gmargo on 2011-08-02
> **fritserasmus said:**
> [COLOR=Blue]
.......CRON{1236] info (No MTA installed, disregarding output)[/COLOR]


Install an MTA (Message Transfer Agent, aka Mail Server) so you get the email from cron telling you what went wrong.  It contains the stdout/stderr from your command.

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[http://en.wikipedia.org/wiki/Message_transfer_agent](http://en.wikipedia.org/wiki/Message_transfer_agent)

---

