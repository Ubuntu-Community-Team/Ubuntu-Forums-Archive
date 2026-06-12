---
title: "Re: New install Xubuntu 13.10 64-bit - Bug Report"
date: 2014-02-25
forum: Desktop Environments
---

### Post by Jacob72 on 2014-02-25
Hello,

I have the following bugs.

CHROMIUM

 Opens birefly then closes before I can read error message. 

Via Terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-l10n
Suggested packages:
  webaccounts-chromium-extension unity-chromium-extension
The following NEW packages will be installed
  chromium-browser chromium-browser-l10n
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/40.7 MB of archives.
After this operation, 165 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package chromium-browser.
(Reading database ... 171746 files and directories currently installed.)
Unpacking chromium-browser (from .../chromium-browser_32.0.1700.107-0ubuntu0.13.10.1~20140204.972.1_amd64.deb) ...
Selecting previously unselected package chromium-browser-l10n.
Unpacking chromium-browser-l10n (from .../chromium-browser-l10n_32.0.1700.107-0ubuntu0.13.10.1~20140204.972.1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
/usr/bin/mandb: can't create index cache /var/cache/man/5322: No space left on device
Setting up chromium-browser (32.0.1700.107-0ubuntu0.13.10.1~20140204.972.1) ...
Setting up chromium-browser-l10n (32.0.1700.107-0ubuntu0.13.10.1~20140204.972.1) ...

```

Using repo:

```
W: Failed to fetch http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
```

Sofware Manager - same bug.

CRHOMIUM EDIT

Now opens with this warning message:

> Your profile could not be opened correctly.

Some features may be unavailable.  Please check that the profile exists and you have permission to read and write its contents.

DESKTOP SHORCUTS

They look bad and do not always open - see attachment.

TERMINAL

Unable to set tab colour - ignores my setting. 

Incremental History - if I move my cursor over a command I am no longer able to user the arrow keys to view history?

PRINT SCREEN

Open with Gimp:

 'Fatal error in PNG image file: Write Error'

Thanks inadvance.

---

### Post by zvacet on 2014-02-25
```
/usr/bin/mandb: can't create index cache /var/cache/man/5322: No space left on device
```

I think that is your problem.Try to remove some files to make space.You can do that with 

```
sudo apt-get autoremove
sudo apt-get autoclean

```

After that try to install  chromium again.

---

### Post by Jacob72 on 2014-02-25
Thanks zvacet,

I removed and purged chromium-browser before installing. I still get the warring message "Your profile ...".

---

### Post by zvacet on 2014-02-25
> I removed and purged chromium-browser before installing.

Did you try commands I write in above post?

---

### Post by The Cog on 2014-02-25
"No space left on device" is not a good message to get. Can you post the output of the command
```
df -h
```
and we'll see how much space you have, and where.

---

### Post by Jacob72 on 2014-02-25
@zvacet

Yes

@The Cog

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             3.7G  3.5G     0 100% /
none                  4.0K     0  4.0K   0% /sys/fs/cgroup
udev                  5.9G  4.0K  5.9G   1% /dev
tmpfs                 1.2G  1.2M  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  5.9G   80K  5.9G   1% /run/shm
none                  100M   20K  100M   1% /run/user
/dev/sda6              92G  4.3G   83G   5% /home
overflow              1.0M  8.0K 1016K   1% /tmp
/home/jacob/.Private   92G  4.3G   83G   5% /home/jacob
/dev/sdc1             466G   55G  412G  12% /media/jacob/Folders
```

---

### Post by zvacet on 2014-02-25
In it not unusual that after uninstalling package some files left in system.To remove them you can use this

```
dpkg --get-selections | grep deinstall > tobepurged
```

You will find file named tobepurged in your home directory.Open it with file manager and use find & replace solution.Under find type unistalled and under replace leave blank.Save and close file.

```
cat tobepurged | xargs sudo dpkg -P
```

This should help to get some free space. :wink:

---

### Post by Jacob72 on 2014-02-25
I ran dpkg as sudo and got this.
```
bash: tobepurged: Permission denied
```

---

### Post by zvacet on 2014-02-25
> I ran dpkg as sudo and got this.

Why did you do that? Run command as normal ( not administrator privileges user) user.You can copy/paste command if you like.It is harmless.Please,try again.

---

### Post by Jacob72 on 2014-02-25
> Why did you do that? Run command as normal

Because I get 'Permissions denied' running as user!?

---

### Post by Jacob72 on 2014-02-25
I think I was getting the permission error when I tried running the command from withen the file system, running withen my folders does not seem to give the error?

I ran the command but this was all that was included in the file.

```
libcanberra-pulse:amd64                deinstall
```

Thanks!

---

### Post by zvacet on 2014-02-25
```
 
dpkg --get-selections | grep deinstall | awk '{print $1}' | xargs  sudo dpkg -P
```

Any luck with this one?

---

### Post by Jacob72 on 2014-02-25
```
(Reading database ... 175835 files and directories currently installed.)
Removing libcanberra-pulse:amd64 ...
Purging configuration files for libcanberra-pulse:amd64 ...
```
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             3.7G  3.5G     0 100% /
none                  4.0K     0  4.0K   0% /sys/fs/cgroup
udev                  5.9G  4.0K  5.9G   1% /dev
tmpfs                 1.2G  1.2M  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  5.9G   80K  5.9G   1% /run/shm
none                  100M   24K  100M   1% /run/user
overflow              1.0M   12K 1012K   2% /tmp
/dev/sda6              92G  7.7G   80G   9% /home
/home/jacob/.Private   92G  7.7G   80G   9% /home/jacob
/dev/sdc1             466G   55G  412G  12% /media/jacob/folders
/dev/sdb1             230G  5.6G  212G   3% /media/jacob/web
```

---

### Post by Yellow Pasque on 2014-02-25
Maybe you should reallocate some of the space for your /home partition to root partition, since it's full...

---

### Post by zvacet on 2014-02-25
```
sudo apt-get clean
```

---

### Post by Jacob72 on 2014-02-25
> Maybe you should reallocate some of the space for your /home partition to root partition, since it's full

I did not make such a small root partition? Gparted does not give me any options on those partitions to change anything?

```
sudo apt-get clean
```

Done

---

### Post by ajgreeny on 2014-02-25
Your root partition is only 3.7 GB, not big enough, so you really have no choice other than enlarging it or reinstalling the OS, I'm afraid.
```
/dev/sda5             3.7G  3.5G     0 100% 
``` and if you did not make it that small, who did?

Your /home partition is plenty big enough at 92GB though the double entry for that partition ```
/dev/sda6              92G  7.7G   80G   9% /home
/home/jacob/.Private   92G  7.7G   80G   9% /home/jacob
``` is a bit odd.

---

### Post by Jacob72 on 2014-02-26
&#65279;> Disk-utility shows there are two root partitions also

Hmm good point, it may have been a mistake by me, but I am aware that is not enough space. I am did re-install after catastrophic blunder as reported in the initial post, perhaps there are some corrupt parts (if that is the correct term?). I did format the disk with zeros though?

Think I will go with starting over.

Thanks everyone for helping me out!

Jacob

---

### Post by Jacob72 on 2014-02-27
Thanks again to all that helped to determine the problem! I have Xubuntu Running like a dream again :) In the end looks like there were no bugs just Human error :) Good learing experience.

---

