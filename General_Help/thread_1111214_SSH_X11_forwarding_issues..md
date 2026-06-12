---
title: "SSH X11 forwarding issues."
date: 2009-03-30
forum: General Help
---

### Post by Tralce on 2009-03-30
I know there are a number of threads on this subject but none seem to have remedied the situation. 

I have an Ubuntu Intrepid box which I often do not have physical access to, so I began relying heavily on X11 over SSH. For the first few days, it worked wonderfully. ssh -X tralce@ubuntu would work on my macbook, calling the X11.app on OS X and nearly any app I tried worked. 

However, now, every time I try to run a program over X11 over SSH, I receive a number of messages, such as:

```
tralce@ubuntu:~$ soffice 
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Failed to open display
```

```
tralce@ubuntu:~$ X11 connection rejected because of wrong authentication.
/usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: localhost:2.0
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)
```

I cannot for the life of me figure out what I did to break X11 forwarding on this computer. Any suggestions? 

Also, sorry if this isn't in the correct subforum but I wasn't entirely sure what one it belonged in.

---

### Post by bettlebrox on 2009-03-30
Does the /etc/ssh/sshd_config file on the system your trying to connect to have the following lines?

[INDENT]X11Forwarding yes
X11DisplayOffset 10[/INDENT]

Also, when you ssh to the other system what's your DISPLAY variable set to? To show it type the following:
```
echo $DISPLAY
```

---

### Post by Tralce on 2009-03-31
```
tralce@ubuntu:~$ cat /etc/ssh/sshd_config |grep X11Forwarding
X11Forwarding yes
tralce@ubuntu:~$ cat /etc/ssh/sshd_config |grep X11Display
X11DisplayOffset 10
tralce@ubuntu:~$ echo $DISPLAY
localhost:10.0
```

Everything appears as normal, but...
```

tralce@ubuntu:~$ gedit
X11 connection rejected because of wrong authentication.

(gedit:9800): Gtk-WARNING **: cannot open display: localhost:10.0
tralce@ubuntu:~$ 
```

---

### Post by bettlebrox on 2009-04-01
Have a look at the logs on the server, maybe it'll give a clue as to what's going on. I'd look in the following:
```
/var/log/auth.log
/var/log/daemon.log
/var/log/messages
```

Also, try running ssh (from the client) in verbose mode, using the -v flag like so:

```
ssh -X -v tralce@ubuntu 
```

---

### Post by Tralce on 2009-04-01
```
tralce@ubuntu:~$ cat /var/log/auth.log|tail -n 35
Apr  1 13:35:31 ubuntu sshd[11146]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.117.193.110  user=root
Apr  1 13:35:33 ubuntu sshd[11146]: Failed password for root from 201.117.193.110 port 57671 ssh2
Apr  1 13:39:01 ubuntu CRON[11538]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  1 13:39:01 ubuntu CRON[11538]: pam_unix(cron:session): session closed for user root
Apr  1 13:43:24 ubuntu sshd[12121]: Disabling protocol version 1. Could not load host key
Apr  1 13:43:26 ubuntu sshd[12121]: Address 201.117.193.110 maps to sauron.ipicyt.edu.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr  1 13:43:26 ubuntu sshd[12121]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.117.193.110  user=root
Apr  1 13:43:28 ubuntu sshd[12121]: Failed password for root from 201.117.193.110 port 34847 ssh2
Apr  1 13:51:20 ubuntu sshd[12996]: Disabling protocol version 1. Could not load host key
Apr  1 13:51:21 ubuntu sshd[12996]: Address 201.117.193.110 maps to sauron.ipicyt.edu.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr  1 13:51:21 ubuntu sshd[12996]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.117.193.110  user=root
Apr  1 13:51:23 ubuntu sshd[12996]: Failed password for root from 201.117.193.110 port 40256 ssh2
Apr  1 13:59:11 ubuntu sshd[13864]: Disabling protocol version 1. Could not load host key
Apr  1 13:59:13 ubuntu sshd[13864]: Address 201.117.193.110 maps to sauron.ipicyt.edu.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr  1 13:59:13 ubuntu sshd[13864]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.117.193.110  user=root
Apr  1 13:59:15 ubuntu sshd[13864]: Failed password for root from 201.117.193.110 port 45676 ssh2
Apr  1 14:07:10 ubuntu sshd[14745]: Disabling protocol version 1. Could not load host key
Apr  1 14:07:11 ubuntu sshd[14745]: Address 201.117.193.110 maps to sauron.ipicyt.edu.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr  1 14:07:11 ubuntu sshd[14745]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.117.193.110  user=root
Apr  1 14:07:13 ubuntu sshd[14745]: Failed password for root from 201.117.193.110 port 51127 ssh2
Apr  1 14:09:01 ubuntu CRON[14952]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  1 14:09:01 ubuntu CRON[14952]: pam_unix(cron:session): session closed for user root
Apr  1 14:13:50 ubuntu sshd[15580]: Disabling protocol version 1. Could not load host key
Apr  1 14:13:51 ubuntu sshd[15580]: Accepted publickey for tralce from 169.244.180.190 port 48672 ssh2
Apr  1 14:13:51 ubuntu sshd[15580]: pam_unix(sshd:session): session opened for user tralce by (uid=0)
Apr  1 14:15:07 ubuntu sshd[15762]: Disabling protocol version 1. Could not load host key
Apr  1 14:15:08 ubuntu sshd[15762]: Address 201.117.193.110 maps to sauron.ipicyt.edu.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr  1 14:15:08 ubuntu sshd[15762]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.117.193.110  user=root
Apr  1 14:15:11 ubuntu sshd[15762]: Failed password for root from 201.117.193.110 port 56599 ssh2
Apr  1 14:17:01 ubuntu CRON[15972]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  1 14:17:01 ubuntu CRON[15972]: pam_unix(cron:session): session closed for user root
Apr  1 14:22:56 ubuntu sshd[16718]: Disabling protocol version 1. Could not load host key
Apr  1 14:22:58 ubuntu sshd[16718]: Address 201.117.193.110 maps to sauron.ipicyt.edu.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr  1 14:22:58 ubuntu sshd[16718]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.117.193.110  user=root
Apr  1 14:23:00 ubuntu sshd[16718]: Failed password for root from 201.117.193.110 port 33792 ssh2
```
Oh dear... looks like some bot is trying to access my root account... However, no info that I can see about X11...

/var/log/daemon.log contains nothing about X11, only four lines about my synergy server. 

```
tralce@ubuntu:~$ cat /var/log/messages|tail -n 35
Apr  1 08:14:21 ubuntu syslogd 1.5.0#2ubuntu6: restart.
Apr  1 08:32:20 ubuntu -- MARK --
Apr  1 08:52:20 ubuntu -- MARK --
Apr  1 09:12:20 ubuntu -- MARK --
Apr  1 09:32:20 ubuntu -- MARK --
Apr  1 09:52:20 ubuntu -- MARK --
Apr  1 10:12:20 ubuntu -- MARK --
Apr  1 10:32:20 ubuntu -- MARK --
Apr  1 10:52:20 ubuntu -- MARK --
Apr  1 11:12:20 ubuntu -- MARK --
Apr  1 11:32:20 ubuntu -- MARK --
Apr  1 11:52:20 ubuntu -- MARK --
Apr  1 12:12:20 ubuntu -- MARK --
Apr  1 12:32:20 ubuntu -- MARK --
Apr  1 12:52:20 ubuntu -- MARK --
Apr  1 13:12:20 ubuntu -- MARK --
Apr  1 13:32:20 ubuntu -- MARK --
Apr  1 13:52:20 ubuntu -- MARK --
Apr  1 14:12:20 ubuntu -- MARK --
```

```
blackzone:~ tralce$ ssh -X -v tralce@ubuntu
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connection established.
debug1: identity file /Users/tralce/.ssh/identity type -1
debug1: identity file /Users/tralce/.ssh/id_rsa type 1
debug1: identity file /Users/tralce/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'xxxxxxx' is known and matches the RSA host key.
debug1: Found key in /Users/tralce/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/tralce/.ssh/identity
debug1: Offering public key: /Users/tralce/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Wed Apr  1 14:32:51 2009 from xxxxxxx
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
/usr/bin/xauth:  error in locking authority file /home/tralce/.Xauthority
tralce@ubuntu:~$
```

```
tralce@ubuntu:~$ gedit
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 49142
debug1: channel 1: new [x11]
debug1: confirm x11
X11 connection rejected because of wrong authentication.
debug1: channel 1: free: x11, nchannels 2

(gedit:18385): Gtk-WARNING **: cannot open display: localhost:10.0
tralce@ubuntu:~$ 
```

It looks like ssh -v might have some more useful information...

---

### Post by bettlebrox on 2009-04-01
What's the ownership and permissions on ~/.Xauthority on both systems? If it's owned a user other than you, then that can cause problems:

```
ls -l ~/.Xauthority
```

Also, make sure that there are no full disks or partitions on both the server and the client:
```
df -h
```
For example, if /tmp, /var, /home, or / are full, then this could cause problems.

If it's not either of those then we can change the logging output of sshd on the server to see if it can provide some more clues. Make a backup copy of the /etc/ssh/sshd_config file before you make any changes, change  LogLevel to debug:
```
LogLevel DEBUG
```

Save the file, and restart sshd on the server:
```
sudo /etc/init.d/sshd restart
```

Here's an excerpt from the the sshd_config man-page below that shows the various logging levels if DEBUG doesn't provide enough info.

[INDENT]LogLevel
             Gives the verbosity level that is used when logging messages from sshd(8).  The possible values are: SILENT, QUIET, FATAL, ERROR, INFO, VERBOSE, DEBUG, DEBUG1, DEBUG2, and DEBUG3.  The default is INFO.  DEBUG and DEBUG1 are equivalent.  DEBUG2 and DEBUG3 each specify higher levels of debugging output.  Logging with a DEBUG level violates the privacy of users and is not recommended.[/INDENT]

Relogin and look at the log files again! :)

Luck

---

### Post by Tralce on 2009-04-01
```
tralce@ubuntu:~$ ls -l .Xauthority
-rw--w--w- 1 root root 169 2009-03-18 10:03 .Xauthority
tralce@ubuntu:~$ sudo chown tralce .Xauthority
tralce@ubuntu:~$ sudo chgrp tralce .Xauthority
tralce@ubuntu:~$ ls -l .Xauthority
-rw--w--w- 1 tralce tralce 169 2009-03-18 10:03 .Xauthority
tralce@ubuntu:~$ chmod 755 .Xauthority
```
After running the above commands I tried again and it worked fine! I'm not sure how the ownerships, groups and permissions got borked, but resetting all three fixed it. Thank you sir!

---

### Post by bettlebrox on 2009-04-02
> **Tralce said:**
> ```
tralce@ubuntu:~$ ls -l .Xauthority
-rw--w--w- 1 root root 169 2009-03-18 10:03 .Xauthority
tralce@ubuntu:~$ sudo chown tralce .Xauthority
tralce@ubuntu:~$ sudo chgrp tralce .Xauthority
tralce@ubuntu:~$ ls -l .Xauthority
-rw--w--w- 1 tralce tralce 169 2009-03-18 10:03 .Xauthority
tralce@ubuntu:~$ chmod 755 .Xauthority
```
After running the above commands I tried again and it worked fine! I'm not sure how the ownerships, groups and permissions got borked, but resetting all three fixed it. Thank you sir!
Great! Glad you got it working! :)

I'd guess the ownership probably got changed at some time when you used to sudo to run an X program or maybe if you used sudo to run ssh?

---

### Post by Tralce on 2009-04-02
I don't remember... Maybe...

Anyways, thanks. I hope future Ubuntu users can benefit from my issue.

---

### Post by jockie on 2009-11-09
Another issue might be a rc file on the SSH server named either ~/.ssh/rc or /etc/ssh/sshrc. If one of these files is present, it has to handle (given) xauth parameters as well, since sshd won’t execute xauth by itself anymore.

---

### Post by jogeba on 2010-04-28
> **jockie said:**
> Another issue might be a rc file on the SSH server named either ~/.ssh/rc or /etc/ssh/sshrc. If one of these files is present, it has to handle (given) xauth parameters as well, since sshd won’t execute xauth by itself anymore.

You made my day! I've been trying *hard* to find this answer.

Thanks

Josef

---

### Post by akikumar on 2010-05-22
I am trying to work on  the college server getting following  error 

X11 connection rejected because of wrong authentication.
Connection lost to X server `localhost:16.0'

here is my sshd_config file

[HTML] # Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
 [/HTML]


also i tried 

[HTML]
rm -f .Xauthorty  
[/HTML]

Nothing worked this was working last night before sleeping i just downloaded qt, open GL, Anjuta IDE for programming

Help help

---

