---
title: "sshd unable to bind port"
date: 2009-02-05
forum: General Help
---

### Post by otkaz on 2009-02-05
I have sshd installed on a remote ubuntu 8.10 box. Every time it boots the auth.log has
sshd:error: Bind to port 2222 on 192.168.1.10 failed: Cannot assign requested address.
sshd:fatal: Cannot bind any address.

when I run "sudo lsof -i | grep 2222" nothing is using that port.
If I run "sudo /etc/init.d/ssh restart" it works fine. I can connect remotely with no errors in auth.log, but as soon as I reboot it I can no longer connect...
I googled the crap out of this to no avail, so this was my next place to turn
any help is greatly appreciated

---

### Post by capscrew on 2009-02-05
Curious -- ssh should be on TCP 22 not as you say 2222.  Did you mess with any configs?

---

### Post by otkaz on 2009-02-05
yes I switched the port to from 22 to 2222 it works fine on that port after I sudo /etc/init.d/shh restart, but will not work until I do that....

---

### Post by Slim Odds on 2009-02-05
> **otkaz said:**
> 
when I run "sudo lsof -i | grep 2222" nothing is using that port.


lsof  lists open files

you want "netstat -l" to look for listening ports

---

### Post by capscrew on 2009-02-05
> you want "netstat -l" to look for listening ports

More specifically you should use:```
sudo netstat -plntu
```

I would also go back to the default TCP port (22) to confirm that your use of 2222 isn't causing some problems.

---

### Post by otkaz on 2009-02-05
> **Slim Odds said:**
> lsof  lists open files

you want "netstat -l" to look for listening ports

after I restart sshd and use lsof it gives me
sshd 5677 root 3u IPv4 20153 TCP d-desktop.local:2222 (LISTEN)

> **capscrew said:**
> More specifically you should use:```
sudo netstat -plntu
```

I would also go back to the default TCP port (22) to confirm that your use of 2222 isn't causing some problems.

sudo netstat -plntu does not show anything using port 2222 until I restart sshd
putting sshd on port 22 does nothing different I still get sshd error bind port 22 in my auth.log and I have to restart sshd manually before I can connect
here is my sshd_config
> # Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 2222

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 192.168.1.10:2222
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
SyslogFacility AUTHPRIV
LogLevel INFO
MaxAuthTries 4

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes
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
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
Allowusers otkaz
Ciphers blowfish-cbc,aes128-cbc,3des-cbc
#GSSAPIAuthentication yes
#GSSAPICleanupCredentials yes
UseDNS yes
Compression yes
UsePAM yes

---

### Post by capscrew on 2009-02-05
Well, I'm certainly no SSH expert.  Now that I have that out of the way, I will say that you have several items that are different from my sshd_config.  My install works, but it is "just as installed".

I'd start with something basic and make changes one at a time (until it breaks).  Do you still have the original sshd_config file?  I would revert to that if at all possible.

---

### Post by otkaz on 2009-02-05
> **capscrew said:**
> Well, I'm certainly no SSH expert.  Now that I have that out of the way, I will say that you have several items that are different from my sshd_config.  My install works, but it is "just as installed".

I'd start with something basic and make changes one at a time (until it breaks).  Do you still have the original sshd_config file?  I would revert to that if at all possible.

well since I can restart the sshd after boot and it works fine until I reboot I don't think anything in the sshd_config could be the problem. It seems like something is preventing the service from launching possibly iptables which I really don't know too much about. I haven't modified iptables config at all. Anyone have a suggestion on anything to try?

---

### Post by Slim Odds on 2009-02-05
```
# What ports, IPs and protocols we listen for
Port 2222

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 192.168.1.10:2222
```

No need to specify the port twice.....

Just make your ListenAddress 192.168.1.10

---

### Post by otkaz on 2009-02-05
> **Slim Odds said:**
> ```
# What ports, IPs and protocols we listen for
Port 2222

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 192.168.1.10:2222
```

No need to specify the port twice.....

Just make your ListenAddress 192.168.1.10

ok I changed that in my sshd_config and it changed nothing still not working after a reboot until I manually launch it

---

### Post by otkaz on 2009-02-06
still can't get this to work right I just installed sshd on another box, and I'm having the same problem. Can anyone offer me some insight? I had it working fine on fedora with the same setup..

---

### Post by stkrzysiak on 2009-05-20
I am experiencing the same issue, although use the default port of 22.  Whenever I restart ssh, i get this in auth.log: 
-error: Bind to port 22 on w.x.y.z failed: Cannot assign requested address.
-fatal: Cannot bind any address.

there must be something we are overlooking, something obvious....

---

### Post by otkaz on 2009-05-20
> **stkrzysiak said:**
> I am experiencing the same issue, although use the default port of 22.  Whenever I restart ssh, i get this in auth.log: 
-error: Bind to port 22 on w.x.y.z failed: Cannot assign requested address.
-fatal: Cannot bind any address.

there must be something we are overlooking, something obvious....

I fixed this issue on mine, but I forget what I changed in my config. post your config file and it will probably jog my memory...

---

### Post by albinootje on 2009-05-20
> **otkaz said:**
> ok I changed that in my sshd_config and it changed nothing still not working after a reboot until I manually launch it

Why did you put a "ListenAddress" ? Was that really needed ? 
Does your machine really have 192.168.1.10 or not ?

Are you using Network Manager on the desktop or is this a server ? It could be possible that ssh starts before your machine has an ip address.

Can you comment the ListenAddress line and reboot ?

If it fails again, can you try this :
```

     -d      Debug mode.  The server sends verbose debug output to the system log, and does not put itself in the background.  The server also will not
             fork and will only process one connection.  This option is only intended for debugging for the server.  Multiple -d options increase the
             debugging level.  Maximum is 3.

```

---

### Post by otkaz on 2009-05-20
> **otkaz said:**
> I fixed this issue on mine, but I forget what I changed in my config. post your config file and it will probably jog my memory...

nevermind albinootje just jogged my memory thats what fixed it I commented out the listenaddress line

---

### Post by stkrzysiak on 2009-05-20
Ah yes, this makes sense.  I was misinterpreting what the ListenAddress parameter designates.  I thought it was a way to control what ips ssh connections would be accepted from, but in reality it is the ip address ssh would bind too, in the case you have two nics or interfaces.  

Thanks guys :o

---

