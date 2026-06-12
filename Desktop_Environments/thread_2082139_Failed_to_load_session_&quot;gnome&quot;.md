---
title: "Failed to load session &quot;gnome&quot;"
date: 2012-11-08
forum: Desktop Environments
---

### Post by David Herring on 2012-11-08
Same problem [as in thread [http://ubuntuforums.org/showthread.php?p=12343496]...upgrade](http://ubuntuforums.org/showthread.php?p=12343496]...upgrade) Ubuntu 12.04 to 12.10 and now cannot remote access the server....

Failed to load session "gnome"

I only installed the XFCE desktop prior to upgrade ...so maybe this is related. Have tried install gnome and re-installing XFCE...stillno joy.


root@vrbs4:/var/log# tail -f /var/log/xrdp-sesman.log 
[20121108-10:29:05] [INFO ] scp thread on sck 7 started successfully
[20121108-10:29:06] [INFO ] granted TS access to user msrbadmin
[20121108-10:29:06] [INFO ] starting Xvnc session...
[20121108-10:29:06] [INFO ] starting xrdp-sessvc - xpid=4351 - wmpid=4350
[20121108-10:29:09] [INFO ] session 4349 - user msrbadmin - terminated
^C


root@vrbs4:/var/log# tail -f /var/log/xrdp-sesman.log 
Nov  8 10:30:26 vrbs4 x-session-manager[4474]: WARNING: GSIdleMonitor: IDLETIME counter not found
Nov  8 10:30:26 vrbs4 x-session-manager[4474]: WARNING: Session 'gnome' runnable check failed: Child process exited with code 1
root@vrbs4:/home/msrbadmin# tail -f .xsession-errors




Xsession: X session started for  at Thu Nov  8 10:34:22 GMT 2012
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:msrbadmin being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Setting IM through im-switch for locale=en_GB.
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[4568]: WARNING: GSIdleMonitor: IDLETIME counter not found
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
x-session-manager[4568]: WARNING: Session 'gnome' runnable check failed: Child process exited with code 1


This may be related to Ubuntu Bug #1042423 .. have posted above in that bug report.

---

### Post by oldos2er on 2012-11-08
Post moved to its own thread.

---

### Post by Hagar Delest on 2012-11-17
If it can help, I've experienced the same problem yesterday. I used to launch Gnome 3 and suddenly I could not open my session anymore.

I just reinstalled gnome-shell (sudo apt-get install gnome-shell) in a TTY and rebooted, and my session was back.

Don't see what has messed up my system. I know that I had to kill Ubuntu software center when it was installing something. I thought it has stalled, perhaps there has been a problem and he was removing my Gnome! That's why I much prefer Synaptics: at least you know exactly what it will do to the system.

---

