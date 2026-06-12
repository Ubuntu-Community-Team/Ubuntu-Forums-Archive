---
title: "Terminal logs"
date: 2009-04-08
forum: General Help
---

### Post by Romala on 2009-04-08
Trying to compile a driver, there were a lot messages in terminal. Is there a full syslog  (text file) of terminal messages? There're Ubuntu 2.6.24-19-386 and 8.10 (Server).
Thank you,
Russian Ubuntu newbie

---

### Post by The Cog on 2009-04-08
No. You can pass the output to a text file for later viewing like this:
**cc myprog.c > compile-log.txt 2>&1**
or 
**make > compile.log 2>&1**
depending on how you make the compile happen.
Or you can just pipe it to less and scroll through the output (use 'Q' to quit):
[B]cc myprog.c | less 2>&1
make | less 2>&1[/B]

---

### Post by Romala on 2009-04-08
Thank you! But i don't find a description of
 **make > compile.log 2>&1**
in **man make**.
Here 
[Terminal logs]("http://ubuntuforums.org/showthread.php?t=392427")
is about **bash**. Maybe, someone could describe, how to use it?
With respect

---

### Post by mali2297 on 2009-04-08
> **Romala said:**
> Thank you! But i don't find a description of
 **make > compile.log 2>&1**
in **man make**.
Here 
[Terminal logs]("http://ubuntuforums.org/showthread.php?t=392427")
is about **bash**. Maybe, someone could describe, how to use it?
With respect

It is a feature of bash, not make. To learn more, see
[http://linuxcommand.org/lts0060.php](http://linuxcommand.org/lts0060.php)

---

### Post by Romala on 2009-04-16
Thank you, Martin.
It is difficult to find a good manual on **bash**, anybody could help?
With respect

---

### Post by Bachstelze on 2009-04-16
**Don't** use Bash redirections here. There is a much better tool for this called [font="monospace"]script[/font]. Example:

```
firas@iori ~ % script aptlog.txt
Script started, file is aptlog.txt
firas@iori ~ % sudo apt-get update
[sudo] password for firas:
Get: 1 http://ftp.fr.debian.org sid Release.gpg [197B]
Ign http://ftp.fr.debian.org sid/main Translation-en_GB
Ign http://ftp.fr.debian.org sid/contrib Translation-en_GB
Ign http://ftp.fr.debian.org sid/non-free Translation-en_GB
Get: 2 http://ftp.fr.debian.org sid Release [93.9kB]
Get: 3 http://ftp.fr.debian.org sid/main Packages/DiffIndex [2038B]
Hit http://ftp.fr.debian.org sid/contrib Packages/DiffIndex
Hit http://ftp.fr.debian.org sid/non-free Packages/DiffIndex
Get: 4 http://ftp.fr.debian.org sid/main Sources/DiffIndex [2038B]
Hit http://ftp.fr.debian.org sid/contrib Sources/DiffIndex
Hit http://ftp.fr.debian.org sid/non-free Sources/DiffIndex
Get: 5 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [16.5kB]
Get: 6 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [4416B]
Get: 7 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [16.5kB]
Get: 8 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [16.5kB]
Get: 9 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [4416B]
Get: 10 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [4416B]
Fetched 119kB in 11s (10.4kB/s)
Reading package lists... Done
firas@iori ~ % sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  apt apt-utils
The following packages will be upgraded:
  login passwd python-elementtree
3 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 1746kB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get: 1 http://ftp.fr.debian.org sid/main login 1:4.1.3.1-1 [688kB]
Get: 2 http://ftp.fr.debian.org sid/main passwd 1:4.1.3.1-1 [1029kB]
Get: 3 http://ftp.fr.debian.org sid/main python-elementtree 1.2.6-14 [29.0kB]
Fetched 1746kB in 0s (6750kB/s)
(Reading database ... 76671 files and directories currently installed.)
Preparing to replace login 1:4.1.3-1 (using .../login_1%3a4.1.3.1-1_amd64.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
Setting up login (1:4.1.3.1-1) ...
(Reading database ... 76671 files and directories currently installed.)
Preparing to replace passwd 1:4.1.3-1 (using .../passwd_1%3a4.1.3.1-1_amd64.deb) ...
Unpacking replacement passwd ...
Processing triggers for man-db ...
Setting up passwd (1:4.1.3.1-1) ...
(Reading database ... 76671 files and directories currently installed.)
Preparing to replace python-elementtree 1.2.6-13 (using .../python-elementtree_1.2.6-14_all.deb) ...
Unpacking replacement python-elementtree ...
Setting up python-elementtree (1.2.6-14) ...
firas@iori ~ % exit
Script done, file is aptlog.txt
firas@iori ~ % cat aptlog.txt
Script started on Thu 16 Apr 2009 20:10:28 CEST
firas@iori ~ % sudo apt-get update
[sudo] password for firas:
Get: 1 http://ftp.fr.debian.org sid Release.gpg [197B]
Ign http://ftp.fr.debian.org sid/main Translation-en_GB
Ign http://ftp.fr.debian.org sid/contrib Translation-en_GB
Ign http://ftp.fr.debian.org sid/non-free Translation-en_GB
Get: 2 http://ftp.fr.debian.org sid Release [93.9kB]
Get: 3 http://ftp.fr.debian.org sid/main Packages/DiffIndex [2038B]
Hit http://ftp.fr.debian.org sid/contrib Packages/DiffIndex
Hit http://ftp.fr.debian.org sid/non-free Packages/DiffIndex
Get: 4 http://ftp.fr.debian.org sid/main Sources/DiffIndex [2038B]
Hit http://ftp.fr.debian.org sid/contrib Sources/DiffIndex
Hit http://ftp.fr.debian.org sid/non-free Sources/DiffIndex
Get: 5 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [16.5kB]
Get: 6 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [4416B]
Get: 7 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [16.5kB]
Get: 8 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [16.5kB]
Get: 9 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [4416B]
Get: 10 http://ftp.fr.debian.org sid/main 2009-04-16-1445.52.pdiff [4416B]
Fetched 119kB in 11s (10.4kB/s)
Reading package lists... Done
firas@iori ~ % sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  apt apt-utils
The following packages will be upgraded:
  login passwd python-elementtree
3 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 1746kB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get: 1 http://ftp.fr.debian.org sid/main login 1:4.1.3.1-1 [688kB]
Get: 2 http://ftp.fr.debian.org sid/main passwd 1:4.1.3.1-1 [1029kB]
Get: 3 http://ftp.fr.debian.org sid/main python-elementtree 1.2.6-14 [29.0kB]
Fetched 1746kB in 0s (6750kB/s)
(Reading database ... 76671 files and directories currently installed.)
Preparing to replace login 1:4.1.3-1 (using .../login_1%3a4.1.3.1-1_amd64.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
Setting up login (1:4.1.3.1-1) ...
(Reading database ... 76671 files and directories currently installed.)
Preparing to replace passwd 1:4.1.3-1 (using .../passwd_1%3a4.1.3.1-1_amd64.deb) ...
Unpacking replacement passwd ...
Processing triggers for man-db ...
Setting up passwd (1:4.1.3.1-1) ...
(Reading database ... 76671 files and directories currently installed.)
Preparing to replace python-elementtree 1.2.6-13 (using .../python-elementtree_1.2.6-14_all.deb) ...
Unpacking replacement python-elementtree ...
Setting up python-elementtree (1.2.6-14) ...
firas@iori ~ % exit

Script done on Thu 16 Apr 2009 20:12:06 CEST

```

So basically just do [font="monospace"]script whatever.txt[/font] then do your stuff and do [font="monospace"]exit[/font] when you're done, then paste the file. ;)

---

