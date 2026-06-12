---
title: "Could not access GDM configuration file."
date: 2007-02-14
forum: Desktop Environments
---

### Post by ittiam on 2007-02-14
I updated to edgy from dapper recently and after that gdm never comes up...i am logging into the gui using kdm and btw i have been having both kde and gnome for a long time

when i try to run gdmsetup i get the following output

> Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry

  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.


Also now when i click on the quit button i dont see shutdown and restart options.

???

---

### Post by CrazyGenie on 2007-02-14
One quick solution is to remove gdm (I guess some gdm related file corruption could have happened during upgrade) and reinstall using the following set of commands

apt-get remove --purge gdm
dpkg --configure -a
apt-get install gdm

Then, stop the kdm/any login manager you are using, by going to shell (Using Ctrl+Alt+F2, for example) and typing...
/etc/init.d/kdm stop

Then do,
dpkg-reconfigure gdm
(select gdm as the default login manager in the dialog that apprears)

Then, restart login manager using...
/etc/init.d/gdm restart

Hope this works!!!

---

### Post by jonti on 2007-02-20
Thanks CrazyGenie. I have exactly the issue described inpost #1 and your method sorted it. I was able to run gdmsetup and make the change I wanted to make. So far, so good.

But, amazingly enough, when I rebooted my machine the problem returned :confused:

---

### Post by CrazyGenie on 2007-03-10
> **jonti said:**
> But, amazingly enough, when I rebooted my machine the problem returned :confused:

Hope you are using gdm as your default login manager. If not, you can do that in a shell by using the command

/etc/init.d/kdm stop (If kdm is running)
/etc/init.d/gdm stop
dpkg-reconfigure gdm

If that is not the case, you may look at the log file /var/log/gdm/:0.log for any clue:(

---

