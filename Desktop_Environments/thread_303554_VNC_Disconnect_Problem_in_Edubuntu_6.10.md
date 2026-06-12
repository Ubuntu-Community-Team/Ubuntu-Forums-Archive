---
title: "VNC Disconnect Problem in Edubuntu 6.10"
date: 2006-11-20
forum: Desktop Environments
---

### Post by cquick01 on 2006-11-20
I am currently using Edubuntu 6.10 and have successfully setup VNC to work. I have VNC starting at the same time as the gdm session manager, so I can log directly into my workstation and then log in as a particular user. However, I type the username and password for any user and then I am disconnected. If I wait a few minutes, I can reconnect to the session as the logged in user.

I had the same setup working great under Kubuntu 5.10. What changed?

Here's how I installed the software:
Using the Synaptic Package manager, located an installed x11vnc

Modified /etc/X11/gdm/Init/Default file to include before exit:
/usr/bin/x11vnc -o /var/log/x11vnc.log -forever -bg

Opened up the appropriate ports on my router.

Any ideas? I'm fairly new to the Linux world, but would like to learn more.

---

### Post by DaveM753 on 2006-12-10
I'm using Ubuntu 6.10 and experiencing a similar issue.  x11vnc works fine at the login screen, but once past the login screen, the process dies.  I list running processes, and x11vnc is not there.  To install x11vnc, I followed the instructions at [http://www.odrakir.com/blog/?p=201](http://www.odrakir.com/blog/?p=201).  Once at my desktop, if I manually start x11vnc from a terminal window, it works fine.  I tried putting this line into my Sessions|Startup Programs, but x11vnc never starts from there.

Anyone know how to fix this?

Here's the line in /etc/X11/gdm/Init/Default:
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -shared -bg -rfbport 5900

x11vnc version is 0.8.2-1.

Here's the last part of the x11vnc log file (with "xxxxxxxx" where my hostname was):

...

10/12/2006 18:13:30 Listening for VNC connections on TCP port 5900
10/12/2006 18:13:31 fb read rate: 7 MB/sec
10/12/2006 18:13:31 screen setup finished.
10/12/2006 18:13:31 
The VNC desktop is:      xxxxxxxx:0
10/12/2006 18:13:57 Got connection from client 192.168.1.103
10/12/2006 18:13:57   other clients:
10/12/2006 18:13:57 Disabled X server key autorepeat.
10/12/2006 18:13:57   to force back on run: 'xset r on' (3 times)
10/12/2006 18:13:57 created xdamage object: 0x40002c
caught X11 error:
10/12/2006 18:13:57 deleted 40 tile_row polling images.
10/12/2006 18:13:57 Restored X server key autorepeat to: 1
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (MIT-SHM)
  Minor opcode of failed request:  4 (X_ShmGetImage)
  Serial number of failed request:  120
  Current serial number in output stream:  122

...


> **cquick01 said:**
> I am currently using Edubuntu 6.10 and have successfully setup VNC to work. I have VNC starting at the same time as the gdm session manager, so I can log directly into my workstation and then log in as a particular user. However, I type the username and password for any user and then I am disconnected. If I wait a few minutes, I can reconnect to the session as the logged in user.

I had the same setup working great under Kubuntu 5.10. What changed?

Here's how I installed the software:
Using the Synaptic Package manager, located an installed x11vnc

Modified /etc/X11/gdm/Init/Default file to include before exit:
/usr/bin/x11vnc -o /var/log/x11vnc.log -forever -bg

Opened up the appropriate ports on my router.

Any ideas? I'm fairly new to the Linux world, but would like to learn more.

---

### Post by krunge on 2006-12-12
Have a look at the "gdm" discussion here:

     [http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

you may need to add a "KillInitClients=false" entry in the [daemon] section
of gdm.conf.

---

