---
title: "Hard Drive Space?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by lemonsCC on 2006-08-11
Upon logging in today I recieved a message that I was low on HD space.  This seems odd as there is not much on this computer.  When I go to Places > Computer and try to check the HDD Free Space Available it says unknown.

How can I get it to tell me the HDD size and free space available?


EDIT:  P.S. Not sure if this is the correct forum.

---

### Post by gmarton on 2006-08-11
Type in Accessories->terminal
> df -h

---

### Post by lemonsCC on 2006-08-11
Thank you!

Success!  Wow only 36 GB drive, 1.4 GB available!?

There is a program for Mac OS X that shows in graphic form all the types of files on your drive.  This especially useful for spring cleaning.  Any thing like this for Ubuntu?

---

### Post by Ocxic on 2006-08-11
system-->admin---> disks

---

### Post by gmarton on 2006-08-11
I dont know of a graphical way to show file  other than nautilus but here is a line that will give all the files added/modified in the past day and bigger than 1M and their sizes. thet will give you a clue on what might take up your space 

> find $HOME -mtime 1 -size +1M -exec ls -lh {} \;

---

### Post by lemonsCC on 2006-08-11
How big is the ubuntu distro?

is there anyway to see this list for all users?

---

### Post by orasis on 2006-08-11
If you are on Xbuntu (Im not sure if the same applies to the regular Ubuntu)
you can right click the top task bar, and "add" a free disk space "Widget" I guess you could call it. :)

---

### Post by orasis on 2006-08-11
> **lemonsCC said:**
> How big is the ubuntu distro?

is there anyway to see this list for all users?

It's about 2Gb's, standard install. - and you could always limit disk space use of certain users by instituting quota systems ;)

---

### Post by gmarton on 2006-08-11
you can use sizes home directories:
> sudo du -hs /home/*

---

### Post by lemonsCC on 2006-08-11
I checked everyones home folder.  Only 8GB total for all users + 3BG for the OS. Where is my other 22BG?

---

### Post by lemonsCC on 2006-08-11
The quota shouldn't be needed as the only larger users home folder is the one with family pictures in it.  No one esle hits over 1GB

---

### Post by NemoTheLobster on 2006-08-11
I know there's a couple of GUI's that map out file sizes and such, but I personally use durep
```
apt-get install durep
durep -td 1
```

It's command line, but quicker and more convenient than the GUI's I looked at.  It will also scan your entire drive and generate an HTML report, but I use the text report of just the current directory most often.

Just a guess, but I'd say the first place to check for something filling up your drive is either /tmp or /var/log.  I've had some kernel modules constantly generate messages and fill up 20 gigs with logs in a few days (and ended up just disabling syslog until the kernel module got fixed).  You can also have programs crash with a lot of temporary files in /tmp that you can go clean up.

---

### Post by gmarton on 2006-08-11
can you post the output of this? 

sudo du -hs /*

---

### Post by lemonsCC on 2006-08-11
the file size for the var folder is 15.6 GB!  Dear lord what is in there?  only file logs?

---

### Post by lemonsCC on 2006-08-11
Yes sir.

200M    /home/chris
130M    /home/guest
1.1G    /home/nicole
7.2G    /home/pam
40M     /home/tester
136M    /home/tim
12K     /home/username

EDIT:  pam is the user with over 3000 photos, nothing abnormal about that size

---

### Post by gmarton on 2006-08-11
lets find out what is bigger than 10 M there...

> sudo find /var -size +10M -exec ls -lh {} \;

---

### Post by lemonsCC on 2006-08-11
```
chris@ubuntu:~$ sudo find /var -size +10M -exec ls -lh {} \;
-rw-r--r-- 1 root root 13M 2006-06-08 11:06 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
-rw-r--r-- 1 root root 21M 2006-08-03 04:10 /var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.46_i386.deb
-rw-r--r-- 1 root root 21M 2006-07-11 05:10 /var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.44_i386.deb
-rw-r--r-- 1 root root 26M 2006-07-11 12:12 /var/cache/apt/archives/openoffice.org-common_2.0.2-2ubuntu12.1_all.deb
-rw-r--r-- 1 root root 29M 2006-07-11 12:12 /var/cache/apt/archives/openoffice.org-core_2.0.2-2ubuntu12.1_i386.deb
-rw-r--r-- 1 root root 21M 2006-07-18 04:11 /var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.45_i386.deb
-rw-r--r-- 1 root root 22M 2006-05-14 22:08 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
-rw-r--r-- 1 root root 38M 2006-03-07 04:04 /var/cache/apt/archives/openclipart-svg_0.18+dfsg-4_all.deb
-rw-r--r-- 1 root root 138M 2006-03-07 04:04 /var/cache/apt/archives/openclipart-png_0.18+dfsg-4_all.deb
-rw------- 1 root root 5.4G 2006-07-26 00:21 /var/backup/2006-07-26_00.00.01.983558.ubuntu.ful/files.tgz
-rw------- 1 root root 88M 2006-07-29 00:10 /var/backup/2006-07-29_00.00.03.211236.ubuntu.inc/files.tgz
-rw------- 1 root root 16M 2006-07-30 00:24 /var/backup/2006-07-30_00.00.05.609476.ubuntu.inc/files.tgz
-rw------- 1 root root 30M 2006-07-31 00:38 /var/backup/2006-07-31_00.00.12.267901.ubuntu.inc/files.tgz
-rw------- 1 root root 16M 2006-08-01 00:12 /var/backup/2006-08-01_00.00.07.169910.ubuntu.inc/files.tgz
-rw------- 1 root root 11M 2006-08-02 00:29 /var/backup/2006-08-02_00.00.17.158119.ubuntu.inc/files.tgz
-rw------- 1 root root 5.0G 2006-08-03 00:16 /var/backup/2006-08-03_00.00.03.507977.ubuntu.ful/files.tgz
-rw------- 1 root root 16M 2006-08-06 00:11 /var/backup/2006-08-06_00.00.06.451533.ubuntu.inc/files.tgz
-rw------- 1 root root 27M 2006-08-07 00:02 /var/backup/2006-08-07_00.00.03.196796.ubuntu.inc/files.tgz
-rw------- 1 root root 45M 2006-08-08 00:03 /var/backup/2006-08-08_00.00.02.766544.ubuntu.inc/files.tgz
-rw------- 1 root root 20M 2006-08-09 00:03 /var/backup/2006-08-09_00.00.03.405716.ubuntu.inc/files.tgz
-rw------- 1 root root 5.1G 2006-08-11 00:16 /var/backup/2006-08-11_00.00.02.729012.ubuntu.ful/files.tgz

```

---

### Post by gmarton on 2006-08-11
uh-oh you might have a bigger issue...

must be some log file filling up for you. can you tell which directory the files are in? have you recently upgraded from breezy?

---

### Post by gmarton on 2006-08-11
hm there are the 3 files bigger than 5GB.
looks like you are backing up too many files on a weekly basis.
What backup are you using?

you can look in 
 /etc/cron.weekly/

---

### Post by lemonsCC on 2006-08-11
I upgraded when dapper came out, i recently uninstalled the ubuntu-desktop because i wanted to get rid of some default programs.

Not sure what directories you are talking about.

---

### Post by lemonsCC on 2006-08-11
not sure what backup i am using, i don't think i ever touched that.

The files in etc/cron.weekly are:
> 0anacron
man-db
ntp-server
popularity-contest
sysklogd

EDIT automatix did intall a backup program

---

### Post by gmarton on 2006-08-11
ok i thing your problem is that your upgrade did not go well and the weekly software update tries to do it again weekly backing up your system.

---

### Post by lemonsCC on 2006-08-11
is there a way to fix this?

praying for a "yes, its quite easy"  :-k

---

### Post by gmarton on 2006-08-11
i would backup everything that is dear to you in /home
then remove 
/var/backup/2006-08-03_00.00.03.507977.ubuntu.ful/files.tgz
/var/backup/2006-07-26_00.00.01.983558.ubuntu.ful/files.tgz

they are older ones

(if you dont remove them you wont have enough room to upgrade)

then try to upgrade again
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

I did that at first but things did not go well so I just backed up my home directory on a different machine and did a clean install.

I dont know of an easier way... but you have to fix it one way or the other because next week you will run out of room...

---

### Post by lemonsCC on 2006-08-11
sounds like a fun and exciting adventure awaites me...

time to open the FTP again

---

### Post by lemonsCC on 2006-08-11
gmarton,

first of all thanks for all the help.  Secondly, can i copy the users entire home folder and sort out access later under root?  such as copy, compress and FTP the folders nicole and pam?

---

### Post by gmarton on 2006-08-11
I would not compress
if you have another linux box you can use rsync to backup those home directories. be sure you have enough room on the other machine tho...

---

