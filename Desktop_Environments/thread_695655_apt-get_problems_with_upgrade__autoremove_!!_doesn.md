---
title: "apt-get problems with upgrade / autoremove !! doesn't work anymore"
date: 2008-02-13
forum: Desktop Environments
---

### Post by gobba71 on 2008-02-13
Hi!

Yesterday I installed and removed some programms and I did the "cleanlinks" command.

Today I have problems with apt-get.


**~$ sudo apt-get upgrade **
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.5MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate IO/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 106538 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.51 (using .../linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Can't locate Cwd.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


Same problem with apt-get autoremove!

What can I do - do you need more information?

Ubuntu 7.10

---

### Post by jan quark on 2008-02-13
try these commands


```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by gobba71 on 2008-02-13
> **jan quark said:**
> try these commands


```
sudo apt-get -f install
```

```
$ sudo apt-get -f install 
[sudo] password for daminator:
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++2.10-glibc2.2 libstdc++2.10-dev g++-2.95
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.22-14-generic
Suggested packages:
  linux-doc-2.6.22 linux-source-2.6.22
The following packages will be upgraded:
  linux-image-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.5MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: Perl may be unconfigured (Can't locate IO/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 106538 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.51 (using .../linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Can't locate Cwd.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


```
sudo dpkg --configure -a
```

Doesn't help.


I don't understand why my "perl" is suddenly not working?

---

### Post by PmDematagoda on 2008-02-13
Remove the file causing the problem using:-
```
sudo rm /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb
```

And then execute:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```

---

### Post by gobba71 on 2008-02-13
Hi!

It didn't help, still get the problem. I really think it's a Perl issue


```
debconf: Perl may be unconfigured (Can't locate IO/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting

```

Is there any way I can reset / reinstall / fix perl now?

---

### Post by PmDematagoda on 2008-02-13
Try doing:-
```
sudo apt-get install --reinstall perl
```

---

### Post by gobba71 on 2008-02-13
> **PmDematagoda said:**
> Try doing:-
```
sudo apt-get install --reinstall perl
```

Hi!

Even here I get the same error!

I am still able to install software (even if getting this error)

mh Maybe somebody has an idea?

---

### Post by YaroMan86 on 2008-02-13
Looks to me from your error messages like an apt-get critical dependency is gone. Doing a forced install won't help if apt-get doesn't have its own needs. Try finding a way to reinstall dkpg, apt-get, et al.

---

### Post by gobba71 on 2008-02-13
> **YaroMan86 said:**
> Looks to me from your error messages like an apt-get critical dependency is gone. Doing a forced install won't help if apt-get doesn't have its own needs. Try finding a way to reinstall dkpg, apt-get, et al.

Maybe some symlink is gone because of cleanlinks command?

---

### Post by YaroMan86 on 2008-02-13
That might just be it. I've looked at the man page for that command, but I do not see a way to undo it. I am not sure how you'd be able to recover any lost symlinks, perhaps compiling apt-get and its friends from source might be the only way. Or you could do a fresh install, though I usually don't recommend that.

---

