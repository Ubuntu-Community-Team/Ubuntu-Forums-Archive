---
title: "Need Help wish establishing SSH Connection on Ubuntu 9.10 with OpenSSH Server"
date: 2010-01-31
forum: Desktop Environments
---

### Post by Carlo1973 on 2010-01-31
Hi there, I've been struggling for awhile to get my system to accept SSH connections. I've checked the forums here as well as other places on the net, but nothing i've tried seemed to work - and it got to the point where my connection got borked in the process. So I'm starting with a clean install.  I am using Ubuntu 9.10 64bit. I am behind a dlink dir-655 router - this computer is completly wireless. For the moment I'm only concerned with getting SSH to work internally within my network. I can do the port forwarding for external access later. 

I've installed openssh-server (sudo apt-get install openssh-server)
I've configured sshd_config with the following options:
         PermitRootLogin no
         AllowUsers nx limited


(* I added the nx user in advance as I plan on installing nxserver once I have SSH working both internal on my network and external. The limited user is just as it is called - limited access, but with enough rights for me to do what I need to do when i'm remote)

Everything else is default. The RSA/DSA key pairs were generated automatically apon installing OpenSSH-Server


When I try to use PuTTY from my wife's window's xp laptop to this box it times out and never establishes a connection. 

The end target for this is so that I can remote from my wife's computer to this box so that I can practice for a few exams while being in the same room with her while she watches tv (rather than walking up 2 flights of stairs and at the other end of the house).

The other reason for wanting to get SSH and hopefully NX working on this station is that I work in the IT department of a small company, and we need a connection outside of our network for basic network testing (from outside the company network -> in to the company network). I'm the new guy in our department and although I have some linux skill I'm still a novice. There is only one other Linux guy there - he's more advanced than I am. He tried to assist me but without him seeing my system he couldn't figure out why it wouldn't connect as easily it should have. 

Any and all help on this matter would be greatly appreciated. I can post the contents of my ssh_config and sshd_config (although I never touched ssh_config at all, and the only changes made to sshd_config are mentioned above)

Thanks!!

Carlo

---

### Post by denarced on 2010-01-31
firewall enabled ?
iptables status ?

---

### Post by Carlo1973 on 2010-01-31
> **denarced said:**
> firewall enabled ?
iptables status ?

From what I can tell - the firewall is disabled. This appears to be the default level in Ubuntu 9.10 as I never enabled nor disabled the firewall. The firewall is the default - ufw. result of $ sudo iptables -L -n reveals:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

Gufw show's the firewall as disabled.

The Windows firewall on my wife's laptop is set to allow trafic from/to PuTTY through port 22 (left as default for configuration purposes)

---

### Post by Carlo1973 on 2010-02-01
Okay figured out why SSH wasn't working internal...

turns out that I had enabled on the dlink dir-655, 2 options under advanced wireless settings: Wireless Partition and Extra Wireless Protection. These two options both cause issues with connecting internally through ssh when wireless. Disabling these both fixed that problem and I was able to ssh internally from my wife's laptop to my desktop upstairs.

Issue now is trying to get NX setup and working. I went to nomachine.com, downloaded and installed the client, node, and server (in that order). Installed nomachine client on my wife's laptop. Attempted to use NXClient from the windows laptop but it failed to connect. I double checked my settings on my server and both AllowUsers nx and AllowGroups nx are both there. 

Suggestions?

Carlo

---

### Post by Carlo1973 on 2010-02-01
I had a collegue of mine go through my sshd_conf file. Had one or two entries that were wrong. Fixed it. works now. I can now SSH and NX through to it. 
I will post my sshd_conf when I get home tonight.

---

### Post by Carlo1973 on 2010-02-03
```

# Package generated configuration file
# See the sshd(8) manpage for details

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
PermitRootLogin no
StrictModes yes

# Authorised Users
AllowUsers nx
AllowUsers user1 
AllowUsers user2
AllowUsers user3

# Authentication 
PubkeyAuthentication yes
# AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
# IgnoreUserKnownHosts yes

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

UsePAM yes

```

---

