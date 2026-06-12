---
title: "Bastille tells me linux is unstable"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Sin@Sin-Sacrifice on 2007-10-28
So I've been playing around with the security of my Ubuntu box and just hadn't gotten around to Bastille until today. Well... I get to it finally and it tells me this:

sin@Sin-Sacrifice:~$ sudo bastille
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.

NOTE:    Valid display found; defaulting to Tk (X) interface.
NOTE:    Using Tk user interface module.
NOTE:    Only displaying questions relevant to the current configuration.
NOTE:    Bastille is scanning the system configuration...

NOTE:    Existing config file found.  Populating answers...
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
NOTE:    Bastille is scanning the system configuration...

/bin/touch: cannot touch `/var/lock/bastille/bastille-lock': No such file or directory
Bastille is now locking down your system in accordance with your
answers in the "config" file.  Please be patient as some modules
may take a number of minutes, depending on the speed of your machine.

Executing Firewall Specific Configuration
An override for "/etc/init.d/bastille-firewall" already exists, but --force specified so will be ignored.
An override for "/sbin/bastille-ipchains" already exists, but --force specified so will be ignored.
An override for "/sbin/bastille-netfilter" already exists, but --force specified so will be ignored.
An override for "/etc/Bastille/bastille-firewall.cfg" already exists, but --force specified so will be ignored.
An override for "/etc/Bastille/bastille-firewall-early.sh" already exists, but --force specified so will be ignored.
Executing File Permissions Specific Configuration
Executing Account Security Specific Configuration
Executing Boot Security Specific Configuration
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   Unable to open /etc/inittab as the
         swap file /etc/inittab.bastille
         already exists.  Rename the swap file to allow Bastille
         to make desired file modifications.
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   open /etc/inittab.bastille failed...
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   open /etc/inittab failed.
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
# Couldn't prepend line to /etc/inittab, since open failed.Executing Inetd Specific Configuration
Executing User Tool Specific Configuration
Executing PAM Specific Configuration
Executing Logging Specific Configuration
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   Unable to open /etc/logrotate.d/syslog as the
         swap file /etc/logrotate.d/syslog.bastille
         already exists.  Rename the swap file to allow Bastille
         to make desired file modifications.
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   open /etc/logrotate.d/syslog.bastille failed...
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   open /etc/logrotate.d/syslog failed.
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
# Couldn't append line to /etc/logrotate.d/syslog, since open failed.Executing Printing Specific Configuration
Executing Temporary Directory Specific Configuration
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   Unable to delete Bastille lock file: /var/lock/bastille/bastille-lock
########################################################
Errors have occurred in the configuration.
Please view the following file for more details:
        /var/log/Bastille/error-log
########################################################

I'm thinking it could be from a reinstallation of Ubuntu recently but it would seem that everything is running smoothly and even better still since the Gutsy Gibbon upgrade. I can't seem to figure out why it's telling me the errors on the top about my debian being unstable nor the bottom where it says it can't open some files even though I can only run it as su. Anyone out there know what could be going on with either error?

---

### Post by TeaSwigger on 2007-10-29
Well ubuntu isn't Debian Stable if that's what it's moaning about. Beyond that I've no inkling tbh.

---

### Post by FredB on 2007-10-29
Yes, this should be the answer here.

As ubuntu is based on debian sid, bastille doesn't like that ! :)

---

### Post by Sin@Sin-Sacrifice on 2007-10-29
Thanks for the darn fast reply.... but I'm still wondering about the errors involving the files it couldn't access. It takes me through the normal selection menu and It would see that I'm setting it up the same way I did before (turning my computer into its own firewall) yet nothing seems to be working like it use to. Last time I set up bastille I wouldn't get a single hit on firestarter. It seemed like they couldn't even get that close. I tested it and the only reason I got that close from my grandfather's windows system is because I know the PC and the passwords. Now, even after bastille, I get nothing but the stupid lightning bolt on firestarter. I think it has something to do with the fact that it can't access those files and some of them do not exist. Any ideas? This section is mostly what I'm talking about: 

ERROR: Unable to open /etc/logrotate.d/syslog as the
swap file /etc/logrotate.d/syslog.bastille
already exists. Rename the swap file to allow Bastille
to make desired file modifications.
ERROR: System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR: open /etc/logrotate.d/syslog.bastille failed...
ERROR: System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR: open /etc/logrotate.d/syslog failed.
ERROR: System is not running a stable Debian GNU/Linux version. Setting to 3.0.
# Couldn't append line to /etc/logrotate.d/syslog, since open failed.Executing Printing Specific Configuration
Executing Temporary Directory Specific Configuration
ERROR: System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR: Unable to delete Bastille lock file: /var/lock/bastille/bastille-lock

I never got that on the initial installation of Feisty.... and nothing could get close to my hard drive from the outside.... that I knew of.

---

