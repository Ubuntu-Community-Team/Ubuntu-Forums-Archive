---
title: "Broken Desktop"
date: 2012-10-07
forum: Desktop Environments
---

### Post by TanHannah on 2012-10-07
Help! I upgraded my desktop to Ubuntu 12.04 while installing the electricity went off then when I opened the computer the user login won't open and Ubuntu kept on loading endlessly then i pressed the escape button it showed this:

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start( utility, e.g. start S90binfmt-support
* Starting NSM status monitor [OK]
* Starting Start this job to wait until portmap is started or fails to s[OK]
* Starting Start this job to wait until portmap is started or fails to s[OK]
* Starting NSM status monitor [OK]
* Starting NSM status monitor [fail]
* Stopping NSM status monitor [OK]
* Starting anac(h)ronistic cron [OK]
* Stopping anac(h)ronistic cron [OK]
* Checking battery state [OK]
* Stopping System V runlevel compatibility [OK]


What's the meaning of this and how to solve this??
Please answer. T__T

---

### Post by DeceptiveHornet on 2012-10-07
> **TanHannah said:**
> Help! I upgraded my desktop to Ubuntu 12.04 while installing the electricity went off then when I opened the computer the user login won't open and Ubuntu kept on loading endlessly then i pressed the escape button it showed this:

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start( utility, e.g. start S90binfmt-support
* Starting NSM status monitor [OK]
* Starting Start this job to wait until portmap is started or fails to s[OK]
* Starting Start this job to wait until portmap is started or fails to s[OK]
* Starting NSM status monitor [OK]
* Starting NSM status monitor [fail]
* Stopping NSM status monitor [OK]
* Starting anac(h)ronistic cron [OK]
* Stopping anac(h)ronistic cron [OK]
* Checking battery state [OK]
* Stopping System V runlevel compatibility [OK]


What's the meaning of this and how to solve this??
Please answer. T__T

In my experience, a linux upgrade that was interrupted is easiest to remedy by re-installating it as a fresh installation. Others may have tip on how to save your system though i'll pitch in and say: Download, burn to a DVD and reinstall it entirely.

---

### Post by TanHannah on 2012-10-07
> **DeceptiveHornet said:**
> In my experience, a linux upgrade that was interrupted is easiest to remedy by re-installating it as a fresh installation. Others may have tip on how to save your system though i'll pitch in and say: Download, burn to a DVD and reinstall it entirely.

My computer doesn't have a CD/DVD player.. Are there other ways??

---

### Post by emk2203 on 2012-10-07
Download an install CD and try the repair function. If that doesn't help, save /home to a backup and reinstall.

---

### Post by akoskm on 2012-10-07
> **TanHannah said:**
> My computer doesn't have a CD/DVD player.. Are there other ways??

Sure, you can burn the iso to an USB stick.

[Installation from USB Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

