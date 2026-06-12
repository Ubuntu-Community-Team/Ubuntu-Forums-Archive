---
title: "How to run startup programs as root?"
date: 2009-02-24
forum: General Help
---

### Post by jnewl on 2009-02-24
I know how to get programs to run at startup, but how do I get them to run without asking me for my password every time? I guess I could always change their permissions, but is there a way to do it without resorting to that?

---

### Post by fuzzyk.k on 2009-02-24
For the permissions you could modify the sudoers file to allow running of certain programs or commands with root permissions check the sudoers man file
check out
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by mb_webguy on 2009-02-24
Um, I wouldn't mess with the sudoers file unless you're absolutely sure you need to, and know what you're doing.

If you want to have an application or script run as root at startup, do the following.

1) Create a file called /etc/init.d/local, using the command "sudo gedit /etc/init.d/local".  This is a shell script, so it should begin with:```
#! /bin/sh
```Add any commands or applications you want to run at startup in the script, then save and exit.

2) Make the script executable using the command "sudo chmod a+x /etc/init.d/local".

3) Add the script to Init using the command "sudo update-rc.d local defaults 80".

---

### Post by jnewl on 2009-02-24
I was previously adding startup programs via System -> Preferences -> Sessions. If I use your script method, I presume I'll need to remove the Sessions entries for those programs?

---

### Post by lillabibba on 2009-02-24
I just did what the intruction says (here> [https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point](https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point)), and now I cannot mount D partition at all. How do I reverse the process? :(

---

### Post by Slim Odds on 2009-02-24
> **mb_webguy said:**
> 
1) Create a file called /etc/init.d/local, using the command "sudo gedit /etc/init.d/local".  This is a shell script, so it should begin with:```
#! /bin/sh
```Add any commands or applications you want to run at startup in the script, then save and exit.

2) Make the script executable using the command "sudo chmod a+x /etc/init.d/local".

3) Add the script to Init using the command "sudo update-rc.d local defaults 80".

Why not just put it in rc.local?  That's what it's for.

---

### Post by mb_webguy on 2009-02-24
> **Slim Odds said:**
> Why not just put it in rc.local?  That's what it's for.

Well, rc.local is actually what I'm used to, but I've been reading in several places about [Upstart]("http://upstart.ubuntu.com/") and how it differs from the traditional sysvinit system.  The method I suggested is apparently the preferred method under Upstart based on what I've read, though rc.local will still work.

---

