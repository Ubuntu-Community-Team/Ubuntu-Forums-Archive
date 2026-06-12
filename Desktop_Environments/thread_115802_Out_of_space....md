---
title: "Out of space..."
date: 2006-01-11
forum: Desktop Environments
---

### Post by hamil on 2006-01-11
Hello!

Had some troubles getting logged into X earlier tody. Looked like i have some disk issues... I would appreciate any help on getting control over my machine again.. It can not be true that my root system is overloaded already...
I have partioned it up, so I do have the Home directory on a separate partition. This is the output that df -h, gives me, after an apt-get clean and a apt-get autoclean command..

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             8,3G  7,8G   61M 100% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/hda6              52G   43G  6,2G  88% /home
/dev/sda1             233G  204G   29G  88% /media/LACIE

```

Where hda2 is the root system, hda6 is the home system and sda1 is my external HD.

I do not know where to start cleaning, and for what kind of files I safely can remove. And I can not understand how my system can take 7.8 G of space.
I checked the file system, and it seems like /var/log is taking almost 5 G, how can i reduce its size without any complications?

Looking forward to some guidance.

---

### Post by Dr. Nick on 2006-01-11
You can clear your apt-get cache by running
**sudo apt-get clean **That should erase all the saved packae files you have downloaded from synaptic and apt-get. 

I have heard about /var/log getting big, I think its safe to erase but not sure.

EDIT
[http://www.ubuntuforums.org/showthread.php?t=87342&highlight=clean+log+files]("http://www.ubuntuforums.org/showthread.php?t=87342&highlight=clean+log+files")
their is a link to another thread about large log files, It appears safe to remove them.

EDIT 2
Is this a fresh install, or an upgrade from a previous version? If its and upgrade and you have several kernels installed then that is alot of "wasted" space that can be cured by removing older kernel versions that you dont need/use

---

### Post by hamil on 2006-01-11
The apt-get is allready cleaned, but I did not want to delete any of the files in /var/log, before I knew why they were there, and why they were so big. After reading the post you so kindly linked for me, I found out that it was the same files making troubles for me. 
The kern.log.0 messages.0 and syslog.0 had grown to 1.8G each..
Not sure how to do the:
true > /var/log/kern.log.0
true > /var/log/messages.0
true > /var/log/syslog.0

It just gave me the error message that I did not have access, even though I tried it with the sudo command also. So I simply just deleted the files... Hope that it will work??

Is there anyone who knows why these files grow so much as they have on my system??

---

### Post by Dr. Nick on 2006-01-11
Not sure if simply "deleting" them would be safe or not, I assume they would be automatically recreated but cant guarntee it. I checked my logs and total size for all of them is just under 300mb. Open up the "system log" program that is in the gnome menu somewhere, cant check at the moment but most likely under the administration section. Look at how many days are in your logs, I have only the last 2 days.

Also if something isnt working correctly it could be constataly writing messges to the logs causing them to get that big. While in the system log look for alot of duplicate errors.

---

### Post by GeneralZod on 2006-01-11
Keep a terminal open and running 

```

tail -f /var/log/kern.log.0

```

This will let you see additions to the log file in real-time.  For comparison, mine gets an entry every few seconds, and that's usually from the firewall.

---

### Post by hamil on 2006-01-11
Well, I will try it later. I have now deleted the log-files that took up 1.8G, so at this moment, I do not have any files to tail... Probably they will be recreated after a reboot?

Thanks for all help!

---

### Post by Dr. Nick on 2006-01-11
I imagine a reboot will recreate them, You may not even have to wait till then as they may be recreated whenever one is written to.

---

### Post by hamil on 2006-01-12
Well, a last update from my side regarding my issues.

I deleted the log files named:
/var/log/kern.log.0
/var/log/messages.0
/var/log/syslog.0
And got alot of more free space (1.8G * 3) odd that those files have the exact same file size...

After a reboot, the files was recreated, so it seems like it was no problems deleting them.

Thanks for the help guys!

---

### Post by Dr. Nick on 2006-01-12
Cool glad it worked. Just remember that if you ever run out of space again ;)

---

### Post by leech on 2006-01-12
Check out the program logrotate.  You can customize it to remove the logs, compress them, etc.  I'm surprised it's not installed by default, the logs shouldn't ever get quite that big.

Leech

---

### Post by lamego on 2006-01-12
I would advice you too look at the logfiles with "tail" as suggested on a prior post, is not normal to hav e such bug files unless you are running the system for years... there must be some application or hw configuration causing extreme logging, even if you resolved by cleaning the logs this will always hurt your system performance because of the log writes...
Deleting logfiles is usually safe but as the side effect of stopping the log activiy.
To safely "clean" your log files use:
> sudo echo > file.log

---

