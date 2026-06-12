---
title: "Ubuntu's HAL and USB"
date: 2008-03-19
forum: Desktop Environments
---

### Post by ody on 2008-03-19
I have an implementation of approximately 100 Ubuntu 7.10 machines authenticated via LDAP that are incapable of mounting USB storage via Gnome.  After much research I have tracked this down to a hal issue not being able to determine who is at the console.  Work arounds I have tried include - pam_group: Which does not work because hal is not able to obtain the group information from pam_group and so not believing that my logged in users are part of the plugdev group.  I can add users to the local group file and hal will believe this, but these are mostly computer lab boxes and so not realistic to add 1000s of users to each boxes local group file. Changing the line in '/etc/dbus-1/system.d/hal.conf' that is at_console="true" to "false", functions but also gives users logged in via VNC the ability to mount a console users USB drive.  Installing pam_console is not an option.  I have changed the group policy in hal.conf from plugdev to a group defined in our LDAP configuration and that makes mounting possible but still causes the same behavior as changing at_console to false. ConsoleKit is installed but no where can I find and configuration files for it nor does anything in the hal.conf reference it.  Any ideas?

--Thanks
Cody

---

### Post by chaos51 on 2008-04-16
I am running into the same problem, Did you ever find a solution?
 thanks,

---

