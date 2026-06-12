---
title: "Problems getting error messages out of crontab shell scripts"
date: 2009-02-27
forum: General Help
---

### Post by damonrand on 2009-02-27
Hi there,

I've got a fairly standard Ubuntu 8.10 install. 

I've just spent a couple of hours working out what was wrong with a very simple shell script. Problem was I couldn't get any output for some reason so I couldn't see the error telling me "blahblahbadcommand" was wrong. 

# This works fine and outputs --help to the log
/usr/bin/dar --help >> /tmp/my.log

# This doesn't output anything to the log
/usr/bin/dar -blahblahbadcommand >> /tmp/my.log

I was initiating both commands from crontab. Something to do with the difference between stdout and errout?

I'm not a shell expert as you can tell. ;-)

Damon.

---

### Post by trwww on 2009-02-27
STDERR is usually emailed to the owner of the crontab file.

Type 'mail' (without the quotes) at a terminal to see if the data you are looking for is there.

To get STDERR to your log file, try:

/usr/bin/dar -blahblahbadcommand 2>&1 >> /tmp/my.log

---

### Post by Lars Stokholm on 2009-02-27
> **trwww said:**
> STDERR is usually emailed to the owner of the crontab file.Do you know if this is also true if you don't have any mail program installed (default)? If so, where is this mail kept? /var/mail is empty.

---

### Post by KeyserSoze93 on 2009-02-27
> **Lars Stokholm said:**
> Do you know if this is also true if you don't have any mail program installed (default)? If so, where is this mail kept? /var/mail is empty.

type mail

Otherwise, just do:

/usr/bin/dar -blahblahbadcommand 2>&1 >> /tmp/my.log

---

### Post by Lars Stokholm on 2009-02-27
> **KeyserSoze93 said:**
> type mail> $ mail
The program 'mail' can be found in the following packages:
 * heirloom-mailx
 * mailutils
Try: sudo apt-get install <selected package>
bash: mail: command not foundWhich brings me back to my question:> **Lars Stokholm said:**
> Do you know if this is also true if you don't have any mail program installed (default)? If so, where is this mail kept? /var/mail is empty.

---

### Post by geirha on 2009-02-27
Install [bsd-mailx](apt:bsd-mailx) if you are using Intrepid, and [mailx](apt:mailx) if you are using Hardy or older. Once it is installed, cron will start mailing you the output (both stdout and stderr) of commands run from cron, and you can read them with the mail command.

To append all output (stdout and stderr) from a command to a file, you'll want to do
```
command >>file 2>&1
```
The order of >> and 2> is important. "command 2>&1 >>file" will not send stderr to the file.

---

### Post by damonrand on 2009-02-28
Thanks guys, the command >>file 2>&1 solution will do me nicely!

Damon.

---

