---
title: "Poweroff without root permision."
date: 2009-03-24
forum: General Help
---

### Post by dragos240 on 2009-03-24
Is it possible to tell poweroff, halt, and reboot to execute without root permissions? My brother usually neglects to turn off the computer when he leaves and i want to put a shell script on each of our desktops so that mom can shutdown the computer without calling me up and asking what to do. Is this possible, to tell those commands to execute without root?

---

### Post by sdennie on 2009-03-24
It's possible, yes.  You just need to give the user in question sudo access to /sbin/halt or whatever you use to turn off the machine.  If you google for visudo and halt, you will probably find the solution to your problem.

---

### Post by dragos240 on 2009-03-24
Thats the issue, my mom uses windows, i just had to reinstall the piece of crud today, after she messed it up (again).  I want a simple shell script that doesn't require sudo. Is it possible to chmod it?

---

### Post by mb_webguy on 2009-03-24
On my machine, shutdown and reboot (which is what poweroff and halt point to) are executable by all users...  But they don't actually work when used without superuser privileges, which is odd.

EDIT:  It has to be possible, because otherwise the Logout and User Switcher applets wouldn't work.

---

### Post by dragos240 on 2009-03-24
Not exactly true, gdm uses sudo if you want to execute it manually, this enables the shutdown functions.

---

### Post by louieb on 2009-03-24
The only time you need sudo access to shutdown is when there a multiple users logged on. (you and your brother). The easy way is to tell your mom to select **Log Out.**  The when she gets to the log on screen she can select **Shutdown** from the **options menu **in the lower left corner. 

You can do it with a shell script too. As sdennie pointed out you will have to setup rules using visudo to allow  running shutdown with out a password. Haven't done it in a while.

---

### Post by kuja on 2009-03-24
Well, you could set it up as a cron job that runs as root to eliminate the need for a script. A line like ```
 0 0 * * * shutdown -h now
``` should shut off the computer every midnight.

Editing sudoers to contain a line like ```
%admin ALL=NOPASSWD: /sbin/shutdown
``` Should allow the shutdown command to be run with sudo and not require a password, and the script would run "shutdown -h now" 

Anyhoo, have fun.

---

