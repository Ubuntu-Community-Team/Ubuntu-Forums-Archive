---
title: "Core dumps cripple inspiron 1420"
date: 2008-01-31
forum: Dell  Ubuntu Support
---

### Post by PaperPilot on 2008-01-31
I bought a 1420 loaded with Ubuntu 7.04, and everything was fine until I started playing around with D.  I got a hat full of segmentation faults and resulting core dumps.  Now Gnome works intermittently and the display freezes.  I don't know where the dumps are stored or where to put the ```
ulimit -c 0
``` command or even if it will help.

What am I to do?

---

### Post by neptho on 2008-02-01
What is 'D'?  Have you attempted to create a new user account, and log into that?

What software have you installed?  Have you added any custom non-Ubuntu repositories?  Have you run any commands you've found on people's blogs?

---

### Post by PaperPilot on 2008-02-01
D is a follow on language to C++, created by Walter Bright of Digital Mars.  I am programming it in a terminal window using the command line.  I ran a script I found on  a web site for eliminating core dumps which helped the situation a little bit.

On UNIX systems I would run fsck, but when I enter that command on Linux, I get a message that I should not run fsck on an attached drive.  So I am in a quandary.

Joel

---

### Post by PaperPilot on 2008-02-01
[QUOTE=neptho]Have you attempted to create a new user account, and log into that?[/QUOTE]

I booted into the single user mode and created a new user, but couldn't login to that account--it wouldn't take the password.  I have a second user account on the machine.  When I logged on using that account, I had the same problems.  Also I can't access the options menu on the login splash screen.

Thanks

---

### Post by neptho on 2008-02-02
If you want to try to fsck the drive, you should enable the root console login. (sudo passwd root as your semi-broken user), then reboot the machine.  At the menu countdown, press 'esc', then choose 'recovery mode' .  

Login as the root user with your new password, then do an 'fsck -y'; which will (dangerously) attempt to repair all allocation issues, but at this point, you're not going to be missing a heck of a lot.

After that completes, I'd exit from the shell and let it load normally.  If things are still broken, make a tar backup of your homedir (tar cvpf - /home/{yourlogin} | gzip -9 > /home/myname.tar.gz)

Copy this file somewhere, or do not reformat the /home partition when you reinstall.  If you opt to not reformat /home, make sure you rename your old login to something such as 'lasthome_broken'.

It's difficult to say what may be damaged; at this point, I'd try fscking in single mode, then reinstalling, recovering my data that I needed back from the tarball created above.  Core dumps can be tricky, and are certainly beyond the scope of a thorough gdb tutorial here.

Good luck!

---

### Post by PaperPilot on 2008-02-04
neptho, thanks for your help.  I did a  fsck and was surprised at the number of memory blocks which were assigned to more than one inode.   Now I cannot boot as a regular user.  When I boot up, I get a message:

```
can't access tty; job control turned off
```

It then transitions to something called busybox which runs on a ram fs.  Can I make the backup tarball or is everything lost?

I wish I had made that tarball before I started playing with D.  Would programming D in a dedicated partition have prevented this problem from ruining my install?

Joel

---

