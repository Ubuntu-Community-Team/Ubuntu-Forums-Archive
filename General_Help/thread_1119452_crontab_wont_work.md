---
title: "crontab wont work"
date: 2009-04-08
forum: General Help
---

### Post by racu on 2009-04-08
Hi! I am having problems with crontab. It wont work with my Ubuntu:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

These were the steps I did:

1. crontab -e in my terminal
2. 10 * * * * /my_directory/run.sh
3. put "mkdir samp" in run.sh (without the double qoutes)
4. chmod 755 /my_directory/run.sh
5. crontab -l in my terminal

And these were the results:

1. "crontab: installing new crontab" appeared in terminal
2. no samp directory was made after the 10th minute of the hour
3. crontab -l output was "10 * * * * /my_directory/run.sh"

What might be the cause of my problem? Thanks!

---

### Post by kpkeerthi on 2009-04-08
What happens when you run run.sh from the command prompt?
```
sh /my_directory/run.sh
```

Do you really have a folder called my_directory under / ?

What does ```
ls -l /my_directory/run.sh
``` print?

Assuming /my_directory exists, you may want to check if you have permissions to create directories under it: apparently, run.sh is attempting to create "samp" under /my_directory.

---

### Post by Xiangxianni on 2009-04-08
I think you should record the log of your cron jobs,then you can find the error easily.
Just:
1.crontab -e
2.change your command to :
   10 * * * * /my_directory/run.sh 2>&1 | tee /tmp/mycron.log

---

### Post by racu on 2009-04-08
Thanks for your replies! I finally got it working!

I did

```

10 * * * * /my_directory/run.sh 2>&1 | tee /tmp/mycron.log 

```

The log said that the samp directory already exists. I checked it in my home folder and there it is! My problem was that I am expecting the samp folder to be in the /my_directory folder. My file run.sh should contain ```
mkdir ~/my_directory/samp
``` instead of ```
mkdir samp
```

Again, thanks for the help!

---

