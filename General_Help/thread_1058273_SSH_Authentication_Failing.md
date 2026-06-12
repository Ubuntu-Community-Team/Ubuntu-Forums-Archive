---
title: "SSH Authentication Failing"
date: 2009-02-02
forum: General Help
---

### Post by crokett on 2009-02-02
Not sure where to put this so...

I generated the keypair and put the public key into my keys file, then made the appropriate edits to /etc/ssh/sshd_config then restarted sshd.  I went to the client, imported they keys tried to start a session and it failed.  I see this in the syslog (username is edited out):

```

Feb  2 17:14:24 hawking smbd[14299]: pam_sm_authenticate: Called 
Feb  2 17:14:24 hawking smbd[14299]: pam_sm_authenticate: username = [greendm] 
Feb  2 17:14:24 hawking smbd[14299]: Error attempting to parse .ecryptfsrc file; rc = [-5]
Feb  2 17:14:24 hawking smbd[14299]: Unable to read salt value from user's .ecryptfsrc file; using default 
Feb  2 17:14:25 hawking smbd[14300]: Error attempting to open [/home/xxxxx/.ecryptfs/wrapped-passphrase] for reading 
Feb  2 17:14:25 hawking smbd[14300]: Error attempting to unwrap passphrase from file [/home/xxxx/.ecryptfs/wrapped-passphrase]; rc = [-5] 

```

I looked through the sshd config file and don't see any entries regarding ecryptfs .  I also don't have a .ecryptfs directory in my home directory.

Here is the sshd_config file.  Vanilla except for the authorized keys entry. And the port number, also edited out.  Yes I am a bit paranoid. ;)

Thanks for any help.  Google didn't have much.

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port xxxxxx
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
#UsePrivilegeSeparation yes
UsePrivilegeSeparation no

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
#SyslogFacility AUTH
SyslogFacility AUTHPRIV
LogLevel INFO

# Authentication:
LoginGraceTime 120
#PermitRootLogin yes
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile %h/.ssh/authorized_keys

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
PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
GSSAPIAuthentication yes
#GSSAPICleanupCredentials yes
GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by spiderbatdad on 2009-02-02
So presently you have password login enabled. I do this breifly to upload an id to ssh with the following command:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub <user@ip_address>
```Where <user@ip_address> depends on whether I am inside the LAN, and is the admin user account on the ssh server@ the ip address of the server.

The file /.ssh/id_rsa.pub must be on the local machine.
I also noticed your sshd_config doesn't specify users allowed...for the "paranoid" this is a good practice. At the bottom of sshd_config:
```
AllowUsers Somebody Somebody_else
AllowGroups sshlogin

```
And make users "Somebody and Sombody_else" members of the ssh login group:
```
sudo adduser username sshlogin

```

But the error looks like you are trying to host the key from an encrypted file and it isnt pasing to the server.

---

### Post by crokett on 2009-02-02
I have some more research to do.  I came home and tried using the same client to connect to a spare laptop I have Ubuntu on.  I did the same things I thought I did at work  to configure sssh and everything worked just fine.  So I will go back to work tomorrow and try to figure out what went wrong.

---

### Post by crokett on 2009-02-03
I figured it out.  I made the changes regarding the allowed users, then disabled PAM since the failed encryption errors in syslog referenced PAM.  After I did that the connections were still failing but I was not recording anything in syslog.  I did some checking and discovered that auth.log is the file I should have been looking at.  I found this entry:

Feb  3 10:41:39 hawking sshd[4341]: Authentication refused: bad ownership or modes for directory /home/xxxxxxx

A quick 'sudo chmod' on my home directory fixed the problem.

---

### Post by spiderbatdad on 2009-02-03
nice work

---

