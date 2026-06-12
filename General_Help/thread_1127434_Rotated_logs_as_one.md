---
title: "Rotated logs as one?"
date: 2009-04-16
forum: General Help
---

### Post by fhsm on 2009-04-16
Ubuntu is rotating my logs automatically.  I haven't changed anything about the setup.  Now I want to go back through all of my dpkg.log files.  In /var/log I've got dpkg.log, dpkg.log.1, dpkg.log.2.gz ... 

I'm trying to run: ```
 cat /var/log/dpkg.log | grep 'install ' 
``` I want to see all the things I've installed on Hardy.  Obviously that command only works for dpkg.log, which only covers April.  Is it possible to do something to get the system to automatically run that command over all the rotated logs for dpkg, as if it was just one big log file?

I know I can just copy all the log files together by hand and then use that, but surely someone more knowledgeable can suggest an elegant solution to the problem.

---

### Post by cariboo on 2009-04-16
If you are running a desktop system, you can open Synaptic and go to Edit-->History, to see a listing of the packages that have been installed.

Jim

---

### Post by ncmncm on 2009-04-16
I assume you want to first cat the  dpkg* files _and_ ignore the .gz files that the  syslog creates.

> cat `ls /var/log/ | grep dpkg  | grep -v gz`

The above command just cats the dpkg files and ignores (grep -v) the gz files. Append the above wiht ' | grep install'

---

### Post by fhsm on 2009-04-16
> **cariboo907 said:**
> If you are running a desktop system, you can open Synaptic and go to Edit-->History, to see a listing of the packages that have been installed.

Jim

Will this show me everything I've installed regardless of how I installed  it (apt-get / aptitude) or just apps I've installed with synaptic?  It's just the sort of info I'm looking for but it doesn't show all that many installs, I don't think it's showing the command line installs.

---

