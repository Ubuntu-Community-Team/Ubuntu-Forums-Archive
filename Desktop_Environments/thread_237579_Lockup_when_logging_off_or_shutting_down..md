---
title: "Lockup when logging off or shutting down."
date: 2006-08-16
forum: Desktop Environments
---

### Post by artinla on 2006-08-16
I replied with a problem to the following thread, but I think it really belongs here.  Could someone take a look and maybe offer some suggestions?  My Dapper hangs up when shutting down, with the exit music just looping over and over, like da da da da da etc..  I have to force power off to get the system to respond again.

I just want to know if there is a log to find out what is going on at the time that the lockup occurs.  I/E what services are shutting down, etc.  I am not really well versed in which logs are which.  I am reasonably certain that this is due to some of the stuff automatix installed.  Hoary works fine, as does the Dapper LiveCD.

I am not running dual monitors.

Thanks,

Art

[http://ubuntuforums.org/showthread.php?t=153958](http://ubuntuforums.org/showthread.php?t=153958)

---

### Post by bernied on 2006-08-16
Look in the /var/log/ directory, you probably want the dmesg log, this is the kernel's log file. Also maybe check the messages file.

These things are usually hardware drivers, and most often video drivers - have you got an nvidia or ati card? If so, search the forum, and generally on google, for your card and driver.

---

### Post by artinla on 2006-08-22
I do have an NVidia graphics board, running the standard ubuntu driver.  This is a clean install, with all of the automatix stuff added.  I haven't added anything else, nor have I altered any config files.

I see that this is a known problem when using an ATI with the fglrx driver.  I don't have an ATI.  The SBLive and the NVidia board are the only cards present in my system.

I will look at the Dmesg log.  Is it not reinitialized when I reboot?  Like I said before, when it locks up I can't do anything except force power off.

I sure would like to find out what is causing this.

---

### Post by bernied on 2006-08-23
Log files I've found that might be useful for you

/var/log/messages
/var/log/dmesg     # but you're right, this is only the current boot
/var/log/kern.log  # this looks like older kernel (dmesg) logs
/var/log/syslog    # lots of system messages

/var/log/aptitude    # aptitude history - what has been installed?
/var/log/aptitude.1.gz    # gzipped older history
(use zcat to look at gzipped files)

/var/log/acpid     # power management?

---

