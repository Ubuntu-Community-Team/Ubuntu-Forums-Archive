---
title: "cant connect to the port designet to ssh"
date: 2008-12-29
forum: General Help
---

### Post by Isilion on 2008-12-29
hi. i tryed uninstalling all ssh related packages and deleting /etc/ssh/ files. then i reinstalled. i can conect normally to port 22, but my desire is change it to, lets say, 666.

this is my sshd_config file:

# Package generated configuration file
# See the sshd(8) manpage for details


# What ports, IPs and protocols we listen for
Port 666

MaxAuthTries 2
MaxStartups 2


#Only v2 SSH Protocol
Protocol 2
# rhosts authentication should not be used
#RhostsAuthentication no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

#AFSTokenPassing no

# Kerberos TGT Passing only works with the AFS kaserver
#KerberosTgtPassing no

# Set this to 'yes' to enable PAM keyboard-interactive authentication
# Warning: enabling this may bypass the setting of 'PasswordAuthentication'
#PAMAuthenticationViaKbdInt yes

#Allow X display forwarding
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#KeepAlive yes
#UseLogin no
UsePrivilegeSeparation yes
#Compression yes

#MaxStartups 10
# no default banner path
#Banner /some/path
#VerifyReverseMapping no

# override default of no subsystems
Subsystem sftp /usr/lib/ssh/sftp-server

#Do not allow root login
PermitRootLogin no


------------------------------------------------------------------------
when i try to connect in the terminal like:
$ ssh -p 666 isilion

i got this:
ssh_exchange_identification: Connection closed by remote host

what im doing wrong? yesterday it worked peercectly u.u please help

---

