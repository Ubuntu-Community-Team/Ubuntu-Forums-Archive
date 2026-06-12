---
title: "Complete Computer Crashes"
date: 2012-03-13
forum: Desktop Environments
---

### Post by Brando753 on 2012-03-13
Alright so I have been using linux for close to 5 years now. I shifted from ubuntu to xubuntu after being forced to either choose Unity or Gnome3. I got my computer set up very nicely however my laptop crashes at least once to twice a day. The mouse will still move, however nothing else will respond, I am unable to even go into a terminal (Ctrl+Alt+F1). I have tried using both the opensource and Proprietary drivers for my graphics card Mobility Radeon HD 5400 Series. I never had this issue on this laptop when I was running gnome2 however I cannot confirm if this issues is related solely to Xfce or if its related to the 11.10 release of ubuntu. If anyone has advice or needs to know more please let me know as this has gone far beyond unstable.

Thanks,

Brando753

---

### Post by wkrekik on 2012-03-13
Hi
When you have shifted from ubuntu to xubuntu, have you formated your ubuntu partition ? And, is your /home located in the system partition or in a separate, dedicaced partition ?

---

### Post by 2F4U on 2012-03-13
Did you look into the system log files. The messages are preserved even after the machine has been rebooted.

---

### Post by Brando753 on 2012-03-13
When I moved from ubuntu to xubuntu I re-partitioned the / (root) directory and preserved my /home directory. When I first booted the system would not let me login, it kept taking me back to the login screen so I figured it was a configuration file issue so I logged into the terminal and moved all hidden files in my home directory to another folder. The system logged in. 

TL;DR I reformatted the root but not the home directory. Yes /home is a separate partition.

As for the logs I looked through them (skimmed) and did not see any {Warning} or {Fatal} or even {Fail} notices and they just went on and on. If there is a specific log I should be looking at please point me in the direction.

Thanks,

Brando753

---

### Post by Brando753 on 2012-03-14
Sorry to bump but this is a very serious issue.

---

### Post by Rodney9 on 2012-03-14
I had the same problem early in Xubuntu 11.10 and I could not get any help.
I moved to Lubuntu 11.10, still happened a few times but but then seemed to go away , I presume due to updates. 

I have just gone back to Xubuntu 11.10 and of course there were a couple of hundred updates and so far, only a week , no crashes.


> View log files in Ubuntu Linux
by VIVEK GITE on AUGUST 2, 2007 

Q. Can you explain me log files in Ubuntu Linux and how do I view logs?

A. All logs are stored in /var/log directory under Ubuntu (and other Linux distro).

Linux Log files and usage

=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file

To view log files at shell prompt

Use tail, more, less and grep command.
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot

---

