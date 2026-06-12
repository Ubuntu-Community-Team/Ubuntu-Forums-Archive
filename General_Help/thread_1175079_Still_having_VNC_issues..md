---
title: "Still having VNC issues."
date: 2009-05-31
forum: General Help
---

### Post by warnox on 2009-05-31
Hey!

I am hoping someone will be able to shed some light on why I cannot get VNC to work on my Ubuntu installation.

I've followed this guide:
[http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome](http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome)

and multiple other ones, on 3 different installations of Linux (Debian 5.0.1, Ubuntu 9.04 and Ubuntu 8.04) but I always get to the same problem.

I run vncviewer (from windows) and input "_192.168.1.4:1_" but get the error '_failed to connect: Connection refused (10061)_' every single time.

From the actual Linux machine running "_vncviewer localhost:1_" I get the '_Connection reset by peer (104)_' error.

I know the computer is listening on port 5901 as I can telnet to it and "_netstat -ab_" shows that it's listening on that port.

There is no rules set on '_iptables_' at all but something is blocking the connection.

If I manually input '_vncserver_' and start the service that way I can connect to the machine fine :S

Hope you can help as I've spent hours and hours on this and am not getting anywhere.

Thank you,




Gregor

---

### Post by HermanAB on 2009-05-31
Well, not getting VNC to work is a blessing really.  Install OpenSSH Server instead.  SSH is secure, does everything VNC does, only much better and is easier to get to work.

---

### Post by warnox on 2009-05-31
The security is not really vital as I'll only be accessing the machine from within the LAN. But if OpenSSH is easier to set up I'll try that.

Is there a Windows Client for OpenSSH, and does it allow a graphical interface rather than just a terminal?

---

This VNC issue is my kryptonite, I really want to know why it isn't working. I know there are other ways around it but I've spent so much time on it now that I have to know why it won't just work!!!

---

