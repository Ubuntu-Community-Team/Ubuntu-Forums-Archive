---
title: "File redirection to a variable filename"
date: 2009-01-15
forum: General Help
---

### Post by dm993 on 2009-01-15
I'd like to automate a process where I read the contents of one or more files and write them to a file using the date as the filename.

I can create a variable as follows to capture the date
**myFileName= date '+%Y%m%d'**
which gives me 20090115

But I'm new to scripting and if I do the following command
**cat fileToRead >> $myFileName**
I get an ambiguous redirect error. I added quotes as follows
**cat fileToRead >> "$myFileName"**
but this gives No Such File or Directory error

Can anyone help me understand what I'm doing wrong? Thanks!

---

### Post by albinootje on 2009-01-15
> **dm993 said:**
> 
I can create a variable as follows to capture the date
**myFileName= date '+%Y%m%d'**
which gives me 20090115

But I'm new to scripting and if I do the following command
**cat fileToRead >> $myFileName**
I get an ambiguous redirect error. I added quotes as follows
**cat fileToRead >> "$myFileName"**
but this gives No Such File or Directory error


I don't know why it doesn't work, but I just fiddled around, and this, as an example, works :

#!/bin/bash
touch $(date '+%Y%m%d')
cat /var/log/syslog.0 >> $(date '+%Y%m%d')

---

### Post by KeyserSoze93 on 2009-01-15
> **dm993 said:**
> I'd like to automate a process where I read the contents of one or more files and write them to a file using the date as the filename.

I can create a variable as follows to capture the date
**myFileName= date '+%Y%m%d'**
which gives me 20090115

But I'm new to scripting and if I do the following command
**cat fileToRead >> $myFileName**
I get an ambiguous redirect error. I added quotes as follows
**cat fileToRead >> "$myFileName"**
but this gives No Such File or Directory error

Can anyone help me understand what I'm doing wrong? Thanks!

You were almost right, however it should be myFileName=$(date '+%Y%m%d')

The $() around the command returns the output, rather than simply running the command and displaying it on the screen.

The ` symbol (NOT a single quote) can also be used, however $() is preferred, since it is more readable.

---

### Post by dm993 on 2009-01-15
Guys that's a great response and really useful to me, I have it sorted now, thanks!

The next thing I am going to try and do is automate this shell script to run at a set time each day, I don't mind figuring it out, but if you can point me to the right commands to use I would be extremely thankful!

:)

---

### Post by albinootje on 2009-01-15
> **dm993 said:**
> Guys that's a great response and really useful to me, I have it sorted now, thanks!

Good :)
> 
The next thing I am going to try and do is automate this shell script to run at a set time each day 

Check out :
```

man cron
man crontab

```

I recommend using the crontab -e command to avoid syntax errors, for example, with my favorite editor joe (as an example in case you don't like vi) :
```

export EDITOR=joe
sudo crontab -e

```
[http://www.pantz.org/software/cron/croninfo.html](http://www.pantz.org/software/cron/croninfo.html)
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

---

### Post by dm993 on 2009-01-15
Linux is just so much more interesting than Windows! :)

---

### Post by kaibob on 2009-01-15
The following is an Ubuntu Cron Howto to add to your reading list: 

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Slim Odds on 2009-01-15
I've added this to many bash related posts, but anyone who's doing bash scripting should have a copy of the Advanced Bash Scripting Guide. It's a fantastic resource for both beginners and experts.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Don't leave $HOME without it.

---

### Post by dm993 on 2009-01-15
> **kaibob said:**
> The following is an Ubuntu Cron Howto to add to your reading list: 

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

thanks for this, I've used the crontab -l command and my script is ready to be ran tonight, one thing I am missing is the cron.allow & cron.deny files in /etc

should I expect my job to fail tonight without one of these?

---

### Post by dm993 on 2009-01-15
> **dm993 said:**
> thanks for this, I've used the crontab -l command and my script is ready to be ran tonight, one thing I am missing is the cron.allow & cron.deny files in /etc

should I expect my job to fail tonight without one of these?

Am I right this will just allow any user to run cron (unrestricted)?

Guys, you're awesome, thanks for the links!

---

