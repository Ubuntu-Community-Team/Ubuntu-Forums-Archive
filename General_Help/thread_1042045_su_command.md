---
title: "su command"
date: 2009-01-17
forum: General Help
---

### Post by alex0705 on 2009-01-17
when i start up console, i dwnloaded already java files, 
i need to type in su
su command works, but i can't type in my pasword, i know it's blocked and stuff but i i type sudo <username>, i neither can't too
can someone help me plz?

---

### Post by sisco311 on 2009-01-17
```
sudo -i
```
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by alex0705 on 2009-01-17
Tyvm, ill test it out later :)

---

### Post by wd5gnr on 2009-01-17
Although sudo -s runs a shell, sudo - simulates logging in as root which may be more what you want.

From man:

       -i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a &#8216;-&#8217; to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user&#8217;s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.



       -s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).

Of course, this is a "controversial subject" from the link provided by Tyvm:

None of the methods below are suggested or supported by the designers of Ubuntu.

Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root.

To start a root shell (i.e. a command window where you can run root commands), starting root's environment and login scripts, use:

sudo -i     (equivalent to sudo su - , gives you roots environment configuration)

To start a root shell, but keep the current shell's environment, use:

sudo -s     (equivalent to sudo su)

###

Me personally, I don't find this to be such a problem but You Have Been Warned (tm). ;-)

---

### Post by alex0705 on 2009-01-18
thx guys

---

