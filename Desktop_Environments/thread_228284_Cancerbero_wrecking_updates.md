---
title: "Cancerbero wrecking updates"
date: 2006-08-02
forum: Desktop Environments
---

### Post by jflash on 2006-08-02
I read about [Cancerbero]("http://cancerbero.sourceforge.net") in the  June 2006 issue of [Linux Magazine]("http://www.linux-magazine.com). I followed the instructions found on the Cancerbero site to the letter. However, I remember that something went wrong during installation, and I aborted, thinking that would be the end of it. Shortly thereafter, I went on vacation and forgot about the whole thing.

So, I come back from vacation and see I have updates. (I am running Ubuntu 6.06, for what it's worth.) So, I click the updates icon, it checks my system, seems like it will work, and then:

```

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

As per the instructions, I run sudo apt-get install -f, and get this:

```
jflash@johnsroom:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  cancerbero
0 upgraded, 0 newly installed, 1 to remove and 41 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 262kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 160120 files and directories currently installed.)
Removing cancerbero ...
dpkg: error processing cancerbero (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 cancerbero
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have tried everything I can think of, including checking for any running Cancerbero process or file in /etc/init.d, running sudo dpkg -r cancerbero, apt-get -r cancerbero, checking my /etc/apt/sources.list file, and all my other normal routes of troubleshooting, but I still get the error. Any ideas as to what might be wrong?

---

### Post by jflash on 2006-08-10
*bump - I'm too lazy to retype this*

---

