---
title: "sudo won't work"
date: 2006-01-03
forum: General Help
---

### Post by skjantzen on 2006-01-03
I've messed up my system and sudo seems to be broken. I can't access any of the tools under System-->Administration. For example if I go to System-->Administration-->Users & Groups it asks for the password (sudo). I enter my user password and then nothing happens...Users & Groups refuses to load. Same thing if I enter sudo commands through the command line. It asks for the password and then...nothing. Any idea how to fix this? I did follow the instructions **"Q: How to set/change/enable root user password?"**at [www.ubuntuguide.org]("http://www.ubuntuguide.org/#setchangeenablerootpassword"). Maybe that messed it up. Any help would be appreciated.

Scott

---

### Post by ape on 2006-01-03
Can you log in as root (try using `su - root` and entering in the password that you have given the root account)  If this is successful, take a look at the /etc/sudoers file and make sure that it at least contains the following lines:

[FONT="Courier New"]# Defaults

Defaults        !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
<your user account here> ALL=(ALL) ALL
[/FONT]

If you are unable to log in as root, you should be able to boot off of the LiveCD, mount your partition that contains the /etc directory and manually modify the passwd and shadow files to set the root account to have an empty password.  You should then be able to reboot, log in as root (with no password) and reset it to allow you to log in as root normally.

---

### Post by skjantzen on 2006-01-04
Thanks so much. For some reason the last line was deleted. I added it back in and all works again.

# Added by Ubuntu installer
<your user account here> ALL=(ALL) ALL

Scott

---

