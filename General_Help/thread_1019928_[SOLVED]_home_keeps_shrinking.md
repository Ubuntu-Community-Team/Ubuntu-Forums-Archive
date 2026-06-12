---
title: "[SOLVED] /home keeps shrinking"
date: 2008-12-23
forum: General Help
---

### Post by NSAJEFF on 2008-12-23
So, I've run into something odd. When I first setup my system I simply created 3 partitions. 6.5gb swap, 5gb /root and 305gb /. Initially, my /home/jeff folder was huge, allowing unlimited usage of space for my home directory. I maxed the drive out and had used nearly 280gb in /home/jeff and began offloading files to a NAS raid setup. I got it all down to only 120gb used but my home directory keeps shrinking in size and not allowing me to expand. Any ideas? Thanks.

---

### Post by NSAJEFF on 2008-12-23
Few notes:

Ubuntu 8.10 64bit
Checked around for suggestions and only option seems to use Gparted but /home is not a separate partition - this is not intended to be a long term/secure installation.

Thanks for your time.

---

### Post by fjgaude on 2008-12-23
Not sure what is going on... are you sure that the Trash is empty?

---

### Post by Elfy on 2008-12-23
Can you run this from a terminal and post the output

```
df -h
```

---

### Post by NSAJEFF on 2008-12-23
> **forestpixie said:**
> Can you run this from a terminal and post the output

```
df -h
```

/dev/sda1             309G  120G   11G  95% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  332K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  696K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6              76G   61G   11G  86% /media/disk


And to the above poster, my trash is cleared on the hour courtesy of Cron.

---

### Post by NSAJEFF on 2008-12-23
Gentle bump. :)

---

### Post by unutbu on 2008-12-23
How about posting ```


sudo tune2fs -l /dev/sda1
```

---

### Post by dcstar on 2008-12-23
> **NSAJEFF said:**
> So, I've run into something odd. When I first setup my system I simply created 3 partitions. 6.5gb swap, 5gb /root and 305gb /. Initially, my /home/jeff folder was huge, allowing unlimited usage of space for my home directory. I maxed the drive out and had used nearly 280gb in /home/jeff and began offloading files to a NAS raid setup. I got it all down to only 120gb used but my home directory keeps shrinking in size and not allowing me to expand. Any ideas? Thanks.

It is your whole root directory, not your "home" directory that is the issue.

Use the Disk Usage Analyzer to show you where all the space is used.

---

### Post by dcstar on 2008-12-23
> **NSAJEFF said:**
> /dev/sda1             309G  120G   11G  95% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  332K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  696K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6              76G   61G   11G  86% /media/disk


And to the above poster, my trash is cleared on the hour courtesy of Cron.

Do it again with this:

```
sudo df -h
```

---

### Post by NSAJEFF on 2008-12-24
> **dcstar said:**
> Do it again with this:

```
sudo df -h
```

No change from original output.

---

### Post by NSAJEFF on 2008-12-24
> **dcstar said:**
> It is your whole root directory, not your "home" directory that is the issue.

Use the Disk Usage Analyzer to show you where all the space is used.

No, it's not. My root directory appears to be quite alright with plenty of space to spare. It's my /home directories that keep shrinking as I clear space.

---

### Post by jerome1232 on 2008-12-24
> **NSAJEFF said:**
> /dev/sda1             309G  120G   11G  95% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  332K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  696K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6              76G   61G   11G  86% /media/disk


According to this, /dev/sda6 is mounted at /. 

This says /dev/sda6 has a capacity of 309G of which 120G are used. It then goes on to state that only 11G are free and that 95% of the disk is used up.

wtf...

There shouldn't be any reason that / would have any difference in space than /home as they are both on the same partition in this instance.

---

### Post by dcstar on 2008-12-25
> **fjgaude said:**
> Not sure what is going on... are you sure that the Trash is empty?

Exactly, and even if the user trash is empty the root trash also needs to be checked.

---

### Post by fjgaude on 2008-12-25
> **dcstar said:**
> Exactly, and even if the user trash is empty the root trash also needs to be checked.

You are so right.

See what these say about Trash:

```
cd /root
```
```
ls -a
```

Another area that has Trash is /root/.local/share/Trash

I'm sure if you search you will find your lost space!

---

### Post by NSAJEFF on 2008-12-25
> **fjgaude said:**
> You are so right.

See what these say about Trash:

```
cd /root
```
```
ls -a
```

Another area that has Trash is /root/.local/share/Trash

I'm sure if you search you will find your lost space!

Ok, I explained this. Both trashes are empty. The space alloted/quota for /home keeps shrinking.

---

### Post by cariboo on 2008-12-25
You may want to clean out the archived package files in /var/cache/apt/archives, to do this in a terminal type:

```
sudo apt-get autoremove
```

and then

```
sudo apt-get clean
```

This will remove the archived packages and any no longer needed dependencies from uninstalled packages. This won't clear up your problem, there must be some space wasting files in your home directory. Give this command a try to see which files and directories are taking up all the space in your home folder:

```
du -cksh * | sort -rn |head -10
```

Jim

---

### Post by Elfy on 2008-12-26
Ok - can you run these please - post the outputs

```
du -h /var/log
sudo find / -name '*' -size +500M
```

Also run ```
df -h
``` once more so we can see how much it's changing

---

### Post by NSAJEFF on 2008-12-26
Guys, I appreciate the help but you're getting away from the issue. I have plenty of space internally. However, as I clear files within my /home/jeff directory it shrinks. So, I delete a 25gb file from my originally 85gb home directory and then my quota is reduced to 60gb and no way to increase it so I run out of space there. However, I can save to various locations other than my personal home directory.

---

### Post by ibuclaw on 2008-12-26
So you have implemented a disk quota on your hard drive?

```
cat /etc/fstab
```
Regards
Iain

---

### Post by NSAJEFF on 2008-12-26
> **tinivole said:**
> So you have implemented a disk quota on your hard drive?

```
cat /etc/fstab
```
Regards
Iain


There is no pre-set quota on my disks. My system seems to be enforcing some arbitrary rule of "let's take space away as it becomes available and assign it to / instead of /home".

---

### Post by NSAJEFF on 2008-12-27
Bump so that I may actually start saving to my home directory again. Thanks.

---

### Post by dcstar on 2008-12-27
> **NSAJEFF said:**
> /dev/sda1             309G  120G   11G  95% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  332K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  696K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6              76G   61G   11G  86% /media/disk


Can you please point out where the "/home" mount point you believes exists is?

You have a SINGLE root partition on this output, nothing more.

This is what a "df -h" shows on a system with a /home partition:

```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda7             9.3G  5.3G  3.5G  61% /
varrun                2.0G  256K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  104K  2.0G   1% /dev
devshm                2.0G   60K  2.0G   1% /dev/shm
lrm                   2.0G   44M  1.9G   3% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1             9.7G  9.0G  756M  93% /c
/dev/sda5              11G  3.3G  6.6G  34% /home
```

---

### Post by neur0 on 2008-12-27
Do you have more then one user?
If not, create a new user and... 

..try to copy some files into its home directory. First try with adding files from other file systems (NFS, CD...) and see if this is possible, effectively making your /home larger for a change. Also copy some files from your personal home directory to another user's home directory and see if your personal quota has shrunk again.

---

### Post by NSAJEFF on 2008-12-27
> **dcstar said:**
> Can you please point out where the "/home" mount point you believes exists is?

You have a SINGLE root partition on this output, nothing more.

This is what a "df -h" shows on a system with a /home partition:

```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda7             9.3G  5.3G  3.5G  61% /
varrun                2.0G  256K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  104K  2.0G   1% /dev
devshm                2.0G   60K  2.0G   1% /dev/shm
lrm                   2.0G   44M  1.9G   3% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1             9.7G  9.0G  756M  93% /c
/dev/sda5              11G  3.3G  6.6G  34% /home
```

/home is in /dev/sda1/ it was never within another partition.

---

### Post by NSAJEFF on 2008-12-27
> **neur0 said:**
> Do you have more then one user?
If not, create a new user and... 

..try to copy some files into its home directory. First try with adding files from other file systems (NFS, CD...) and see if this is possible, effectively making your /home larger for a change. Also copy some files from your personal home directory to another user's home directory and see if your personal quota has shrunk again.

Thank you. I made another user and was able to move files into the users directory. Disk usage analyzer also quoted this new user as having all my left over space on the disk(what I'm going for). Moving files from /home/jeff to /home/test did again shrink the space /home/jeff had. I'm baffled but appreciate the help so far.

---

### Post by Elfy on 2008-12-27
Then home isn't shrinking - the root drive is, which is why people were checking that trash was empty - are there hidden files in your trash?

When you say you can save to other locations, are they other partitions and thus seperate from your / ?

There was a bug early with intrepid where logs became very big, running a parrtition out of room. That was the reason for the du -h /var/log command I gave earlier.

---

### Post by neur0 on 2008-12-27
No, actually, neither /home nor / is shrinking, it's just like one user's home directory has become unable to grow.
Weird problem, maybe there's some .dot file in the user's directory that sets some strange behavior. Did you make custom changes to .bashrc or some other config file/script in your user directory?

---

### Post by ajcham on 2008-12-27
Could you post the contents of fstab (just use: ```
more /etc/fstab
``` or something like that) to see if a quota has been set somehow.

---

### Post by NSAJEFF on 2008-12-27
> **neur0 said:**
> No, actually, neither /home nor / is shrinking, it's just like one user's home directory has become unable to grow.
Weird problem, maybe there's some .dot file in the user's directory that sets some strange behavior. Did you make custom changes to .bashrc or some other config file/script in your user directory?

That describes the problem perfectly. The only scripts running are designed to clear my trash automatically and run rkhunter at 4am and output a small log file to the desktop(which is deleted at 1pm with another script). No other customization has been made.

---

### Post by NSAJEFF on 2008-12-27
> **ajcham said:**
> Could you post the contents of fstab (just use: ```
more /etc/fstab
``` or something like that) to see if a quota has been set somehow.



No quotas have been set by me at any point.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f1167db8-bc92-42f2-b636-7eb87a895c1b /               ext3    relatime,error
s=remount-ro 0       1
/dev/sda5 none swap sw 0 0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by NSAJEFF on 2008-12-28
Bump for a solution...?

---

### Post by ibuclaw on 2008-12-28
Perhaps the answer is in **where** all the used space is coming from:
```
sudo du / -xh --max-depth=1 | grep G
```

I have a small hunch that your log files have exploded to being gigabytes, rather than kilo/megabytes in size, but we may soon see.

Regards
Iain

---

### Post by NSAJEFF on 2008-12-28
> **tinivole said:**
> Perhaps the answer is in **where** all the used space is coming from:
```
sudo du / -xh --max-depth=1 | grep G
```

I have a small hunch that your log files have exploded to being gigabytes, rather than kilo/megabytes in size, but we may soon see.

Regards
Iain

Interesting idea, here is my output:

> 
54G	/home
133G	/var
4.9G	/usr


However, when I look at the output from disk usage analyzer it says /var is only using 780.1mb...:confused:

---

### Post by dcstar on 2008-12-28
> **NSAJEFF said:**
> .......
However, when I look at the output from disk usage analyzer it says /var is only using 780.1mb...:confused:

Because USER based commands do not see files that only ROOT has access to, which is why some of us have been trying to have you run sudo commands and post the output.

---

### Post by NSAJEFF on 2008-12-28
> **dcstar said:**
> Because USER based commands do not see files that only ROOT has access to, which is why some of us have been trying to have you run sudo commands and post the output.


Every command I have run has been as sudo.

---

### Post by ibuclaw on 2008-12-28
> 133G /var
See that! Your /var directory is huge.

I suspect your log files have flooded your filesystem!

This is an unfortunate problem with Intel Wireless cards in Laptops at the current time.

Your best safety is to delete these logs and reboot your system, immediately.
```
sudo du /var/log/ -xha --max-depth=1 | grep G | cut -f2 | while read log; do sudo rm $log; done
```
After reboot, someone with a fine knowledge could perhaps suggest a way to set the rotation of logging to prevent this from happening again.

Regards
Iain

---

### Post by NSAJEFF on 2008-12-31
> **tinivole said:**
> See that! Your /var directory is huge.

I suspect your log files have flooded your filesystem!

This is an unfortunate problem with Intel Wireless cards in Laptops at the current time.

Your best safety is to delete these logs and reboot your system, immediately.
```
sudo du /var/log/ -xha --max-depth=1 | grep G | cut -f2 | while read log; do sudo rm $log; done
```
After reboot, someone with a fine knowledge could perhaps suggest a way to set the rotation of logging to prevent this from happening again.

Regards
Iain

Hi Iain;

I did some digging after that snippit of code didn't quite work. I found that /var/backup had exploded to 178gb. I was able to delete it, however, now I need to find out how to keep that from happening again. Thanks for all your help.

---

### Post by NSAJEFF on 2008-12-31
I may have found a solution(not permanent); I changed access to /var/backup with chmod 777 and now I can go in and clear the folder as I see fit...now to find out what is creating these backups.

---

### Post by dcstar on 2008-12-31
> **NSAJEFF said:**
> Every command I have run has been as sudo.

I have been trying to explain to you that running applications like Disk Usage Analyzer are user based and will not show files restricted to root users, but you seem to know better and keep on doing what you want to do rather than specifically follow the instructions some have given you in an attempt to fix you problem.

Just saying "It is the same" is not the same as posting the output you were specifically asked to do.

Over 1 week to get to the root of an issue that could have taken minutes if the right information was provided.

---

### Post by NSAJEFF on 2008-12-31
> **dcstar said:**
> I have been trying to explain to you that running applications like Disk Usage Analyzer are user based and will not show files restricted to root users, but you seem to know better and keep on doing what you want to do rather than specifically follow the instructions some have given you in an attempt to fix you problem.

Just saying "It is the same" is not the same as posting the output you were specifically asked to do.

Over 1 week to get to the root of an issue that could have taken minutes if the right information was provided.
EDIT: Simple response: **** off. You clearly still don't understand.

---

### Post by fjgaude on 2009-01-01
> **NSAJEFF said:**
> EDIT: Simple response: **** off. You clearly still don't understand.

A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. -- Archbishop Desmond Tutu, 1999

---

### Post by ibuclaw on 2009-01-01
> **NSAJEFF said:**
> Hi Iain;

I did some digging after that snippit of code didn't quite work. I found that /var/backup had exploded to 178gb. I was able to delete it, however, now I need to find out how to keep that from happening again. Thanks for all your help.
Is this /var/backups or /var/backup ?
```
ls /var
```
Anyhow, running dpkg -S will output the names of all packages that have the directory in their files/folders list.
```
dpkg -S /var/backup
```
And post the output, if any.
Regards
Iain



> **dcstar said:**
> I have been trying to explain to you that running applications like Disk Usage Analyzer are user based and will not show files restricted to root users, but you seem to know better and keep on doing what you want to do rather than specifically follow the instructions some have given you in an attempt to fix you problem.

Just saying "It is the same" is not the same as posting the output you were specifically asked to do.

Over 1 week to get to the root of an issue that could have taken minutes if the right information was provided.
@dcstar, unfortunately it is the holiday season, and people aren't around here that often this time of year. And, I suppose the fact that this thread is marked as "Solved" doesn't really help the matter that the OP still has the problem either.

As for DYI tasks, users can either do as they please and possibly escalate the problem, or ask for reassurance on what they are doing.
As far as I see it, you will not be in the blame if such an occurrence happens if someone tries to tackle an issue themselves and fails miserably. They are free to do so, and they will, afterall, learn much more from it than just copy and pasting random text from a codeblock.
But you can either choose to try and help reverse the damage, or you can just keep your thoughts to yourself.

But, in my opinion, you are not in the wrong either.

---

