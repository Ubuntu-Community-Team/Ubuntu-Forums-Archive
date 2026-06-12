---
title: "No ssh on startup"
date: 2009-01-04
forum: General Help
---

### Post by poompt on 2009-01-04
I've installed openssh-server to my ubuntu 8.10 desktop edition box with default setting, and I can successfully connect with putty from other devices, but only if I have already logged into my account on the desktop. Is there something I can do so that I can connect to the ssh server without physically logging in (ie after a remote reboot)? I assume it's a matter of reconfiguring startup services but I haven't been able to determine how I would accomplish that. I know using an automatic login will circumvent this problem but I'm hoping to avoid that.

---

### Post by Peter09 on 2009-01-04
It should work.
From your client try

```
ssh -vX <user>@<machine> xterm
```

---

### Post by poompt on 2009-01-04
> **Peter09 said:**
> ```
ssh -vX <user>@<machine> xterm
```
I'm not sure what you're expecting from that. When I use it on the machine (that I'm currently trying to reconfigure) running ubuntu, it connects but prints a bunch of debug lines, am I supposed to post those to aid in diagnosis? I've mentioned that the problem occurs when I try to connect with other devices when the server pc is on but not logged on, is there some terminal mode I'm missing in putty that will allow me to use this command or do I need a second unix-like machine to do this test?

---

### Post by Peter09 on 2009-01-04
What command are you using to connect? Are you putting the -X option into your command line. 

ssh by default does not need an open session on the server. 

RDP and VNC do need an open session.

I was hoping to see some sort of debug from your client so that we could understand why it is not connecting.

---

### Post by poompt on 2009-01-04
The only method I currently have for testing the connection without creating a user session (which resolves the problem temporarily) is the Putty windows ssh client, which makes it hard to get the same information I can get from the linux version. I can tell you that the x11 forwarding option is off, which is the equivalent of not having the -X option. When I try to connect when the machine is on but not logged in I get the same error message as when it is off. I should note that the reason I assume this is possible at all is because a year ago I was able to do it with a Fedora install with no configuration and the same settings on the putty client, which leads me to assume that the problem is configuration of the server machine.

---

### Post by Peter09 on 2009-01-04
Have a look in /var/log/auth.log or syslog and see if there is any messages there.

You can use the utility

System->Admin->System Log

---

### Post by bodhi.zazen on 2009-01-04
You should not need to be logged in the server to connect via ssh.

I see you are running windows and using putty, which is fine

You also say you are getting an error message, perhaps it would help if you posted the error message.

---

### Post by Slim Odds on 2009-01-04
Is sshd running on the server?

---

### Post by poompt on 2009-01-04
Here is the section of the auth.log file for a reboot, (failed) attempt at accessing ssh before logging in, login and successful ssh attempt after. PC name has been changed to "*server-pc*" and the user to "*user*."
```
Jan  4 14:03:09 *server-pc* gdm[5555]: pam_unix(gdm:session): session closed for user *user*
Jan  4 14:04:10 *server-pc* sshd[5022]: Server listening on :: port 22.
Jan  4 14:04:10 *server-pc* sshd[5022]: Server listening on 0.0.0.0 port 22.
Jan  4 14:05:22 *server-pc* gdm[5549]: pam_unix(gdm:session): session opened for user *user* by (uid=0)
Jan  4 14:05:22 *server-pc* gdm[5549]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  4 14:05:22 *server-pc* gdm[5549]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan  4 14:05:23 *server-pc* gdm[5549]: Autolaunch error: X11 initialization failed.
Jan  4 14:05:23 *server-pc* gdm[5549]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan  4 14:05:23 *server-pc* gdm[5549]: Autolaunch error: X11 initialization failed.
Jan  4 14:05:23 *server-pc* gdm[5549]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan  4 14:05:23 *server-pc* gdm[5549]: Autolaunch error: X11 initialization failed.
Jan  4 14:05:23 *server-pc* gdm[5549]: )
Jan  4 14:07:45 *server-pc* sshd[6236]: Accepted password for *user* from 192.168.1.1 port 2397 ssh2
Jan  4 14:07:45 *server-pc* sshd[6236]: pam_unix(sshd:session): session opened for user *user* by (uid=0)
```
The error message on PuTTY is:
[INDENT]PuTTY Fatal Error
Network error: Connection timed out[/INDENT]
This error occurs both when the server is off and when it is not logged in.

---

### Post by bodhi.zazen on 2009-01-04
I see two things ...

1. What port are you using for ssh ? I see attempts on both port 22 and 2397 .

2. It appears you are trying to ssh in as root ("uid=0")

Try connecting on the correct port and with a non-root user.

---

### Post by poompt on 2009-01-04
I've never used any port except 22, I don't know why it would list any other port but it only lists the second port number when I successfully connected after logging in. I haven't been trying to login using a root user but just in case I made a second standard desktop user "poompt" to troubleshoot:
```
Jan  4 16:07:08 *server-pc* sshd[6377]: Accepted password for poompt from 192.168.1.1 port 2426 ssh2
Jan  4 16:07:08 *server-pc* sshd[6377]: pam_unix(sshd:session): session opened for user poompt by (uid=0)
```
Is the log from when I logged in via ssh after opening a session on the server. I assume the "by (uid=0)" means that the session was created by the root for "poompt" not by poompt. The 2426 port number is odd since I connect exclusively through port 22. I was still unable to login with the new account before opening a session on the server. 
I'm going to note here that the command equivalent of what I'm trying to do is probably "ssh [email]poompt@*my.ip.here[/email]*," I'm trying to go through the internet, not the local network.

---

### Post by Slim Odds on 2009-01-04
Every TCP connection has two endpoints and hence two ports.

Port 22 on the server end and port ???? on the client end.

---

### Post by bodhi.zazen on 2009-01-04
> **Slim Odds said:**
> Every TCP connection has two endpoints and hence two ports.

Port 22 on the server end and port ???? on the client end.

Thanks, I mis-read his logs, my mistake.

---

