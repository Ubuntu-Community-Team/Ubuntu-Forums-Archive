---
title: "creating a starter which requires super user priveleges"
date: 2014-09-05
forum: Desktop Environments
---

### Post by IAMTubby on 2014-09-05
Hello,
 I've created this desktop starter in gnome for an application which is invoked using a script which requires super user privileges at the time of running.
I notice that it runs only when I check the option, "Run in Terminal" and enter my password. If I don't select the option to run from the terminal, it just does nothing, probably waiting for password. Is there any way to configure the desktop icon along with my password, so that I can get it to run just by clicking the icon or something like "Run as administrator"?

Thanks.

---

### Post by TheFu on 2014-09-05
You don't want to do it that way.

However - you can modify the sudoers file to allow that exact command with the exact options you want to be run from your userid without prompting for a password.  **man sudoers** to learn how.  It is one of the best manpages made.  Be certain to use **sudo visudoers** to edit it.

[http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password) explains too.

---

