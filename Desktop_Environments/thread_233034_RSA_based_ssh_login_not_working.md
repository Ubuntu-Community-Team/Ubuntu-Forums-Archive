---
title: "RSA based ssh login not working"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Tauceti38 on 2006-08-09
I've been trying to get certificate based logins working for ssh, but haven't had any lasting success.

  For starters, I can login in just fine using password based authentication, but I need certificate based authentication for a certain program I'm running. The one odd thing about what I need working is that I need to be able to log into **localhost **using certificates. I.e. ssh username@localhost

  I've followed the steps laid out at [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto") and at [https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH"), but have not had any lasting success. I did have certificate based authentication working for two users for about 15 minutes, but somehow broke it trying to get the third user working.
Here's what I've been doing, as best as I can remember.

My sshd_config is as follows:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port ####
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
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys
PasswordAuthentication no

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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

# Added parameters
# AllowUsers restricts logins to the listed users
AllowUsers ####### ######
```
Note: I've tried commenting out the line: RhostsRSAAuthentication no, but it didn't have any effect.

1. Log into the user I want to have certificates working with and type:```
ssh-keygen -t rsa
``` I use the standard directory, ~/.ssh, and overwrite any previous keys, then enter a passphrase.

2. I then type in:```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@fileserver
``` where username is the user I'm trying to get working, and fileserver is where I need to log into using certificates, which is also the machine I'm working from.

3. If the previous step doesn't work, I use the command: ```
cat id_rsa.pub >> authorized_keys
``` to create the authorized_keys file. I cd to the ~/.ssh directory before using that command. I've checked the authorized_keys file and it appears to have a key added to it.

4. I then try ```
ssh username@localhost
``` and either recieve a request for a password, if password authention is on, or a flat out denial if its off, with the error message: Permission denied (publickey). So ssh knows to look for a public key, but it doesn't see the one I set up.

Any suggestions on where to go from here? This is driving me nuts. ](*,)

---

