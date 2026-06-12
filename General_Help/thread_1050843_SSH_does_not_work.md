---
title: "SSH does not work"
date: 2009-01-26
forum: General Help
---

### Post by Isilion on 2009-01-26
Hi, i get this output trying to connect my machine from my machine.

```
root@izilion:/home/isilion# ssh -v izilion
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to izilion [127.0.0.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
root@izilion:/home/isilion#
```


could anyone tell me that happens and what to do to solve it ? thx :)

---

### Post by bgerlich on 2009-01-26
Try to add the following line to hosts.allow:
```
ssh: 0.0.0.0/0.0.0.0
```

If that doesn't work try starting ssh in full verbose mode (-vvv) and post the output.

---

### Post by geirha on 2009-01-26
Also check what the log file says. /var/log/auth.log

---

### Post by zipperback on 2009-01-26
Provide me the output of:

```

ssh localhost

```

- zipperback
:popcorn:

---

### Post by Isilion on 2009-01-26
> **bgerlich said:**
> Try to add the following line to hosts.allow:
```
ssh: 0.0.0.0/0.0.0.0
```

If that doesn't work try starting ssh in full verbose mode (-vvv) and post the output.

Done. Still not work

---

### Post by Joeb454 on 2009-01-26
Have you configured ssh server to allow root logins?

I noticed you're running that command as root, so ssh would also try to connect as root.

---

### Post by Isilion on 2009-01-26
Well, it fixed something anyway. when i type this, i get this output:

$ ssh -vv isilion@izilion (return)
isilion's password: (OK, Connect)

but if i type:

```
$ssh -vv -p 1800 isilion@izilion (1800 is designed port in sshd_config)

root@izilion:/etc# ssh -p 1800 -vv isilion@izilion
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug2: ssh_connect: needpriv 0                          
debug1: Connecting to izilion [127.0.0.1] port 1800.     
debug1: Connection established.                          
debug1: permanently_set_uid: 0/0                         
debug1: identity file /root/.ssh/identity type -1        
debug1: identity file /root/.ssh/id_rsa type -1          
debug1: identity file /root/.ssh/id_dsa type -1          
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1                                                                      
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*                       
debug1: Enabling compatibility mode for protocol 2.0                            
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1              
debug2: fd 3 setting O_NONBLOCK                                                 
debug1: SSH2_MSG_KEXINIT sent                                                   
debug1: SSH2_MSG_KEXINIT received                                               
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                           
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                           
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit: first_kex_follows 0                                  
debug2: kex_parse_kexinit: reserved 0                                           
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: none,zlib@openssh.com                                
debug2: kex_parse_kexinit: none,zlib@openssh.com                                
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 127/256
debug2: bits set: 500/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[izilion]:1720' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:5
debug2: bits set: 517/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /root/.ssh/identity ((nil))
debug2: key: /root/.ssh/id_rsa ((nil))
debug2: key: /root/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```

Also i get similar error trying "# ssh -vv -p 1800 isilion@89.x.x.x (my external ip address)"

---

### Post by Isilion on 2009-01-26
> **Joeb454 said:**
> Have you configured ssh server to allow root logins?

I noticed you're running that command as root, so ssh would also try to connect as root.

Im using the  root account since im editing hosts files etcetera. dont know if its allowed, in sshd_config i set an option to "no".

---

### Post by bgerlich on 2009-01-26
Either turn off PubkeyAuthentication or add your priate key to your host's keychain

---

### Post by Joeb454 on 2009-01-26
Can you post the output of /etc/ssh/sshd_config please? :) I have a sneaking suspicion you've disabled root logins, and naturally, running the command as root will try to log in, as root ;)


Also I've edited your previous posts to contain the output in [noparse]```

```[/noparse] tags, it makes it a little easier to read :)

---

### Post by Isilion on 2009-01-26
> **Joeb454 said:**
> Can you post the output of /etc/ssh/sshd_config please? :) I have a sneaking suspicion you've disabled root logins, and naturally, running the command as root will try to log in, as root ;)


Also I've edited your previous posts to contain the output in [noparse]```

```[/noparse] tags, it makes it a little easier to read :)


```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 1800
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::

#ListenAddress ALL

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
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts no
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
UsePAM yes
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
```

---

### Post by Joeb454 on 2009-01-26
Ok you have ```
PermitRootLogin no
``` Which means ssh server isn't allowing root logins.

From your normal account try running ssh localhost and see if that works. If not then the problem is elsewhere :)

---

### Post by Isilion on 2009-01-26
Wrong. i can run "ssh -vv isilion@izilion" both as root an as isilion, using port 23 or 22.

if i use "ssh -vv -p 1800 isilion@izilion" i get this output:

isilion@izilion:/etc$ ssh -vv -p 1800 isilion@izilion
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug2: ssh_connect: needpriv 0                          
debug1: Connecting to izilion [127.0.0.1] port 1800.     
debug1: Connection established.                          
debug1: identity file /home/isilion/.ssh/identity type -1
debug1: identity file /home/isilion/.ssh/id_rsa type -1  
debug1: identity file /home/isilion/.ssh/id_dsa type -1  
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1                                                                      
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*                       
debug1: Enabling compatibility mode for protocol 2.0                            
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1              
debug2: fd 3 setting O_NONBLOCK                                                 
debug1: SSH2_MSG_KEXINIT sent                                                   
debug1: SSH2_MSG_KEXINIT received                                               
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                           
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                           
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit: first_kex_follows 0                                  
debug2: kex_parse_kexinit: reserved 0                                           
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: none,zlib@openssh.com                                
debug2: kex_parse_kexinit: none,zlib@openssh.com                                
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 119/256
debug2: bits set: 513/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[izilion]:1720' is known and matches the RSA host key.
debug1: Found key in /home/isilion/.ssh/known_hosts:7
debug2: bits set: 509/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/isilion/.ssh/identity ((nil))
debug2: key: /home/isilion/.ssh/id_rsa ((nil))
debug2: key: /home/isilion/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/isilion/.ssh/identity
debug1: Trying private key: /home/isilion/.ssh/id_rsa
debug1: Trying private key: /home/isilion/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
isilion@izilion:/etc$

and i get a similar output if i substitute "izilion" for my external ip.

---

### Post by bgerlich on 2009-01-26
I'll repeat once more: Either turn off PubkeyAuthentication or add your priate key to your host's keychain.

---

### Post by Isilion on 2009-01-26
> **bgerlich said:**
> I'll repeat once more: Either turn off PubkeyAuthentication or add your priate key to your host's keychain.

Pubkey turned off, still getting thesame issue. (Connect on internal ip/standard port Ok, connect by ip on desired port fails)

---

### Post by bgerlich on 2009-01-26
Post the vvv output with public key turned off.

---

### Post by Isilion on 2009-01-26
isilion@izilion:/etc$ ssh -vv -p 1800 isilion@izilion
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug2: ssh_connect: needpriv 0                          
debug1: Connecting to izilion [127.0.0.1] port 1800.     
debug1: Connection established.                          
debug1: identity file /home/isilion/.ssh/identity type -1
debug1: identity file /home/isilion/.ssh/id_rsa type -1  
debug1: identity file /home/isilion/.ssh/id_dsa type -1  
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1                                                                      
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*                       
debug1: Enabling compatibility mode for protocol 2.0                            
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1              
debug2: fd 3 setting O_NONBLOCK                                                 
debug1: SSH2_MSG_KEXINIT sent                                                   
debug1: SSH2_MSG_KEXINIT received                                               
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                           
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                           
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit: first_kex_follows 0                                  
debug2: kex_parse_kexinit: reserved 0                                           
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                            
debug2: kex_parse_kexinit: none,zlib@openssh.com                                
debug2: kex_parse_kexinit: none,zlib@openssh.com                                
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit:                                                      
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 128/256
debug2: bits set: 523/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[izilion]:1720' is known and matches the RSA host key.
debug1: Found key in /home/isilion/.ssh/known_hosts:7
debug2: bits set: 520/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/isilion/.ssh/identity ((nil))
debug2: key: /home/isilion/.ssh/id_rsa ((nil))
debug2: key: /home/isilion/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/isilion/.ssh/identity
debug1: Trying private key: /home/isilion/.ssh/id_rsa
debug1: Trying private key: /home/isilion/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
isilion@izilion:/etc$

---

### Post by bgerlich on 2009-01-26
Have you restarted the ssh server after making those changes?

---

### Post by Isilion on 2009-01-26
I restarted the server and tryed to connect this way:

isilion@izilion:~$ ssh -vv -p 1800 isilion@izilion
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug2: ssh_connect: needpriv 0                          
debug1: Connecting to izilion [127.0.0.1] port 1800.     
debug1: Connection established.                          
debug1: identity file /home/isilion/.ssh/identity type -1
debug1: identity file /home/isilion/.ssh/id_rsa type -1  
debug1: identity file /home/isilion/.ssh/id_dsa type -1  
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1                                      
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*       
debug1: Enabling compatibility mode for protocol 2.0            
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1                                                              
debug2: fd 3 setting O_NONBLOCK                                 
debug1: SSH2_MSG_KEXINIT sent                                   
debug1: SSH2_MSG_KEXINIT received                               
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                                       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                            
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib           
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib           
debug2: kex_parse_kexinit:                                      
debug2: kex_parse_kexinit:                                      
debug2: kex_parse_kexinit: first_kex_follows 0                  
debug2: kex_parse_kexinit: reserved 0                           
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                                       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                      
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr        
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                            
debug2: kex_parse_kexinit: none,zlib@openssh.com                
debug2: kex_parse_kexinit: none,zlib@openssh.com                
debug2: kex_parse_kexinit:                                      
debug2: kex_parse_kexinit:                                      
debug2: kex_parse_kexinit: first_kex_follows 0                  
debug2: kex_parse_kexinit: reserved 0                           
debug2: mac_setup: found hmac-md5                               
debug1: kex: server->client aes128-cbc hmac-md5 none            
debug2: mac_setup: found hmac-md5                               
debug1: kex: client->server aes128-cbc hmac-md5 none            
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent        
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP                     
debug2: dh_gen_key: priv key bits set: 142/256                  
debug2: bits set: 544/1024                                      
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent                           
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY                     
debug1: Host '[izilion]:1720' is known and matches the RSA host key.                                                            
debug1: Found key in /home/isilion/.ssh/known_hosts:7           
debug2: bits set: 486/1024                                      
debug1: ssh_rsa_verify: signature correct                       
debug2: kex_derive_keys                                         
debug2: set_newkeys: mode 1                                     
debug1: SSH2_MSG_NEWKEYS sent                                   
debug1: expecting SSH2_MSG_NEWKEYS                              
debug2: set_newkeys: mode 0                                     
debug1: SSH2_MSG_NEWKEYS received                               
debug1: SSH2_MSG_SERVICE_REQUEST sent                           
debug2: service_accept: ssh-userauth                            
debug1: SSH2_MSG_SERVICE_ACCEPT received                        
debug2: key: /home/isilion/.ssh/identity ((nil))                
debug2: key: /home/isilion/.ssh/id_rsa ((nil))                  
debug2: key: /home/isilion/.ssh/id_dsa ((nil))                  
debug1: Authentications that can continue:                      
debug1: Next authentication method: gssapi-keyex                
debug1: No valid Key exchange context                           
debug2: we did not send a packet, disable method                
debug1: Next authentication method: gssapi-with-mic             
debug1: Unspecified GSS failure.  Minor code may provide more information                                                       
No credentials cache found                                      

debug1: Unspecified GSS failure.  Minor code may provide more information                                                       
No credentials cache found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug2: we did not send a packet, disable method
debug1: Next authentication method: gssapi
debug2: we did not send a packet, disable method
debug1: Next authentication method: publickey
debug1: Trying private key: /home/isilion/.ssh/identity
debug1: Trying private key: /home/isilion/.ssh/id_rsa
debug1: Trying private key: /home/isilion/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug1: Authentications that can continue:
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
isilion@izilion's password:

isilion@izilion:~$ ssh -vv -p 1800 isilion@89.x.x.x //(my external ip)
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 89.7.172.18 [89.7.172.18] port 1800.
debug1: Connection established.
debug1: identity file /home/isilion/.ssh/identity type -1
debug1: identity file /home/isilion/.ssh/id_rsa type -1
debug1: identity file /home/isilion/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
isilion@izilion:~$


why i cannot connet by writing my ip but i can just with computer name? (izilion)help plz thanks.

---

### Post by Isilion on 2009-01-26
anyone help?

---

### Post by bgerlich on 2009-01-26
Have you tried a fully qualified hostname, including the domain ?

izlilion.local most probably,

---

