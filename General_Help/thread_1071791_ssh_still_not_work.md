---
title: "ssh still not work"
date: 2009-02-16
forum: General Help
---

### Post by Isilion on 2009-02-16
when i use this command i get this output:

isilion@izilion:~$ ssh -p 1720 isilion@89.x.x.x -vv
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 89.x.x.x [89.x.x.x] port 1720.
debug1: Connection established.
debug1: identity file /home/isilion/.ssh/identity type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/isilion/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/isilion/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
ssh_exchange_identification: Connection closed by remote host

however, access is granted using

$ ssh -p 1720 isilion@izilion (which is server's name)

---

### Post by bodhi.zazen on 2009-02-16
Not sure, try a google search ...

[http://edoceo.com/notabene/ssh-exchange-identification](http://edoceo.com/notabene/ssh-exchange-identification)

[http://www.snailbook.com/faq/libwrap-oops.auto.html](http://www.snailbook.com/faq/libwrap-oops.auto.html)

You should check the log on the server to see if there are any further clues.

---

### Post by Isilion on 2009-02-16
> **bodhi.zazen said:**
> Not sure, try a google search ...

[http://edoceo.com/notabene/ssh-exchange-identification](http://edoceo.com/notabene/ssh-exchange-identification)

[http://www.snailbook.com/faq/libwrap-oops.auto.html](http://www.snailbook.com/faq/libwrap-oops.auto.html)

You should check the log on the server to see if there are any further clues.

sorry im new user. could you specify what log and his path, please?

---

### Post by bodhi.zazen on 2009-02-16
I believe

/var/log/auth.log

---

### Post by Isilion on 2009-02-16
> **bodhi.zazen said:**
> I believe

/var/log/auth.log

Feb 17 01:36:10 izilion sshd[10336]: pam_unix(sshd:session): session closed for user isilion
Feb 17 02:15:59 izilion sudo:  isilion : TTY=pts/0 ; PWD=/home/isilion/.ssh ; USER=root ; COMMAND=/bin/su
Feb 17 02:16:00 izilion su[4597]: Successful su for root by root
Feb 17 02:16:00 izilion su[4597]: + pts/0 root:root
Feb 17 02:16:00 izilion su[4597]: pam_unix(su:session): session opened for user root by (uid=0)
Feb 17 02:17:01 izilion CRON[5542]: pam_unix(cron:session): session opened foruser root by (uid=0)
Feb 17 02:17:01 izilion CRON[5542]: pam_unix(cron:session): session closed foruser root
Feb 17 02:20:21 izilion sshd[7872]: error: Bind to port 1720 on :: failed: Address already in use.
Feb 17 02:20:21 izilion sshd[7872]: error: Bind to port 1720 on 0.0.0.0 failed: Address already in use.
Feb 17 02:20:21 izilion sshd[7872]: fatal: Cannot bind any address.
Feb 17 02:20:39 izilion sshd[8080]: error: Bind to port 1720 on :: failed: Address already in use.
Feb 17 02:20:39 izilion sshd[8080]: error: Bind to port 1720 on 0.0.0.0 failed: Address already in use.
Feb 17 02:20:39 izilion sshd[8080]: fatal: Cannot bind any address.


there it is, i dont understand it. :s

---

### Post by bodhi.zazen on 2009-02-16
Can you post the output of :

```
sudo lsof -i tcp
```

And the contents of your /etc/ssh/sshd_config ?

---

### Post by Isilion on 2009-02-16
> **bodhi.zazen said:**
> Can you post the output of :

```
sudo lsof -i tcp
```

And the contents of your /etc/ssh/sshd_config ?

isilion@izilion:~$ sudo lsof -i tcp
[sudo] password for isilion:
COMMAND  PID    USER   FD   TYPE DEVICE SIZE NODE NAME
sshd    4821    root    3u  IPv6  14905       TCP *:1720 (LISTEN)
sshd    4821    root    4u  IPv4  14908       TCP *:1720 (LISTEN)
cupsd   4867    root    2u  IPv4  14998       TCP localhost:ipp (LISTEN)
hddtemp 5094    root    0u  IPv4  15207       TCP localhost:7634 (LISTEN)
firefox 6137 isilion   40u  IPv4  71650       TCP izilion.local:55866->mu-in-f127.google.com:www (ESTABLISHED)
firefox 6137 isilion   56u  IPv4  76040       TCP izilion.local:45666->feijoa.canonical.com:www (CLOSE_WAIT)
wish8.5 6225 isilion    7u  IPv4  20058       TCP localhost:61740 (LISTEN)
wish8.5 6225 isilion    8u  IPv4  21000       TCP izilion.local:43724->by1msg3245808.phx.gbl:msnp (ESTABLISHED)
isilion@izilion:~$


# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 1720
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 1,2
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
LogLevel VERBOSE

# Authentication:
LoginGraceTime 45
PermitRootLogin no
StrictModes yes

RSAAuthentication no
PubkeyAuthentication no
AuthorizedKeysFile	%h/.ssh/authorized_keys

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

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

