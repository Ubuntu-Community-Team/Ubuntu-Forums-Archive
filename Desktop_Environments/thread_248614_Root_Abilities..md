---
title: "Root Abilities."
date: 2006-09-01
forum: Desktop Environments
---

### Post by Titan_Prometheus on 2006-09-01
Ok, I know the advise I hear from everyone is to never run as root, but I have that power complex that I have to, the only problem is when I do in GNOME and such is that I don't have almost any rights. I was informaed that this was because of sudo and I was wondering what to do so that Root was the ultimate user and he can see and do anything, without having to rely on sudo.

---

### Post by celloandy on 2006-09-01
First, a disclaimer: generally, when I'm working on an administration task (configuring Apache, say), I get really irritated at having to type sudo before every command, so I feel your pain, and I enable the root user and work as root for brief spells.  However, whoever it was that told you not to run as root all the time was absolutely right.  Don't do it!  To be frank, it's just really stupid.  The fact that so many major, OS-compromising security vulnerabilities are exploitable on Windows is due, at least in part, to the fact that so many processes run with full privileges (why, for instance, would there ever be any justification for giving a browser the right to rewrite system libraries?).  So just don't do that.  It's bad.

That said... to enable the root user, run (from the shell):
```
sudo passwd
```
This will allow you to escalate to root using "su," which is what I would recommend, or to login as root from the console.  GDM, however, still won't let you log in as root.  If you wanted to do this (but again, don't), there's some GDM setting (under "Login Window" in the Administration menu) that allows you to turn on root login from GDM.

Andrew

---

### Post by ciscosurfer on 2006-09-01
celloandy,
Well said!  Although, I believe the correct syntax is as follows (from [https://help.ubuntu.com/community/RootSudo):]("https://help.ubuntu.com/community/RootSudo%29:")
[B]
Enabling the root account[/B]

  To enable the root account (i.e. set a password) use:```
sudo passwd root
``` Enter your existing password
 Enter password for root
 Confirm password for root

**Disabling the root account**  If you have enabled a root password and wish to disable it again. To disable the root account after you have enabled it use:```
sudo passwd -l root
```This locks the root account.
 
 !! This will also prevent you starting the computer in recovery mode on versions of Ubuntu before Ubuntu 6.06 (Dapper Drake)[LIST]
[*] This is because the password value for root in /etc/shadow is not automatically returned to the single * character required for passwordless recovery log in as root. (You will be asked for a password, as one still exists, but will not be able to log in as it is locked.) You will need to edit /etc/shadow to prevent this problem after enabling and then locking the root account. This has been fixed for Ubuntu 6.06 (Dapper Drake) (Flight 3 onwards), locked password and null (*) password are now treated as the same when recovery mode is started.[/LIST]

---

### Post by aysiu on 2006-09-01
Just create a *gksudo nautilus* launcher.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by doobit on 2006-09-01
Or type ```
 sudo su
password:[password] 
``` in a terminal and run all of the rest of your commands for that session from that terminal.

---

### Post by ciscosurfer on 2006-09-01
> **doobit said:**
> Or type ```
 sudo su
password:[password] 
``` in a terminal and run all of the rest of your commands for that session from that terminal.

[COLOR=DarkRed]sudo -i[/COLOR] will accomplish the same task as well.

From the [COLOR=DarkRed]man sudo[/COLOR] page:

The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a - to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user’s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.

---

