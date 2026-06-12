---
title: "Script to shutdown."
date: 2010-02-21
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-21
Hi all, can somebody tell me what is wrong in the following script.
```
#!/bin/sh
# Shutdown if no instance of virtualbox is running.

if pidof VirtualBox | grep [0-9] > /dev/null
then
exec clear
else
exec shutdown -h now
exit
fi
```
It gets executed if double clicked, but not as cronjob of root scheduled to run every minute.
```
* * * * * /home/root/sd.sh # JOB_ID_1

```

Thank you for any help.

---

### Post by Barriehie on 2010-02-21
Try this, you've got to tell cron what user to run the script as:

> **hariks0 said:**
> 
```
* * * * * [COLOR="Red"]**root**[/COLOR] /home/root/sd.sh # JOB_ID_1

```

Thank you for any help.

---

### Post by hariks0 on 2010-02-21
I tried ```
* * * * * [COLOR="SeaGreen"]root[/COLOR] /home/root/sd.sh # JOB_ID_1
``` and ```
* * * * * root [COLOR="Red"]sh[/COLOR] /home/root/sd.sh # JOB_ID_1
``` They worked when executed from Terminal and when double clicked but _not_ automatically.

It seems that there is some problem in running crontab. Can somebody tell me whether ```
sudo crontab -e
``` is the right command to add cron jobs to root?

---

### Post by Barriehie on 2010-02-21
Oops, I just noticed something, perhaps you should be telling cron WHEN to run the job.  As it stands now you have no delimiters for when the action is supposed to occur, i.e. check every minute, every 5 minutes, etc.

Edit: I've got all my crontab entries in /etc/crontab and edit as root.

---

### Post by amac777 on 2010-02-21
Hi, when scripts don't work from cron but they do from the command line, usually the culprit is the environment variables. There are very few of them set within cron. In your case, the problem is likely that the $PATH variable only includes /bin and /usr/bin; however, shutdown is located in /sbin so it won't be found. However, when you run it from the command line, the path includes sbin so it works. To fix this, you probably just need to change the script to indicate the full path for the shutdown command:

```
exec /sbin/shutdown -h now
```

Also, 'sudo crontab -e' is the correct way to call scripts from cron for root, and you don't need to specify the user root in that crontab when you do it this way.

---

### Post by falconindy on 2010-02-21
exec replaces the current shell with the process provided as an argument. You should not be using it in this manner.

---

### Post by hariks0 on 2010-02-21
Now I got it. After posting the last one, I edited again and while exiting Nano saw that the file being saved is one in /tmp. I opened a terminal and as root edited /etc/crontab and that did the trick. Now my entry in looks like ```
*/5 2-8 * * * root /home/root/sd.sh #JOB_ID_1
```.

It checks the presence of a virtualbox process each 5 minutes and shuts down when none is found.

FYI, let me put the whole story before you. My actual requirement was to do the downloads between 02:00 - 08:00 a.m during which period I have unlimited downloads. The steps are as follows :-

1. I have setup to power on my PC automatically at 02.00 at morning.
2. GBUB selects Ubuntu as the default OS after 10 seconds.
3. wxp is started in VirtualBox with ```
VBoxManage startvm wxp
```
4. In wxp FDM is started at startup.
5. FDM does the scheduled downloads and shuts down wxp after completion.
6. OR wxp does shutdown at 08:00 a.m if the downloads are not finished.
7. [Here comes the role of this post] Cron checks the presence of a virtualbox process each 5 minutes and shuts down Ubuntu when none is found.

Of course it is a very clumsy way. But I do not have any other option as FreeDownloadManager is not available for Linux.

Barriehie, thank you very much for the help.

---

### Post by hariks0 on 2010-02-21
> **falconindy said:**
> exec replaces the current shell with the process provided as an argument. You should not be using it in this manner.

Can you please elaborate? I had just edited another script to suit my needs. What is the correct syntax in your opinion?

Thank you.

---

