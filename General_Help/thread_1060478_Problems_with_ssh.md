---
title: "Problems with ssh"
date: 2009-02-04
forum: General Help
---

### Post by Isilion on 2009-02-04
hi. im havingtrouble connecting my machine via ssh. i will copy directly the terminal outpost with some tryes.

isilion@izilion:~$ ssh -p 1720 isilion@izilion
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
97:a6:1c:8d:e2:95:c1:ef:f8:2e:11:d3:88:09:3a:c3.
Please contact your system administrator.
Add correct host key in /home/isilion/.ssh/known_hosts to get rid of this message.
Offending key in /home/isilion/.ssh/known_hosts:7
RSA host key for [izilion]:1720 has changed and you have requested strict checking.
Host key verification failed.

silion@izilion:~$ ssh -p 1720 isilion@89.x.172.x
ssh_exchange_identification: Connection closed by remote host
isilion@izilion:~$ ssh -vv -p 1720 isilion@89.7.172.18
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 89.x.172.x [89.x.172.x] port 1720.
debug1: Connection established.
debug1: identity file /home/isilion/.ssh/identity type -1
debug1: identity file /home/isilion/.ssh/id_rsa type -1
debug1: identity file /home/isilion/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

isilion@izilion:~$ sudo su                                       
root@izilion:/home/isilion# ssh -vv -p 1720 isilion@izilion
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007  
debug1: Reading configuration data /etc/ssh/ssh_config     
debug1: Applying options for *                             
debug2: ssh_connect: needpriv 0                            
debug1: Connecting to izilion [127.0.1.1] port 1720.       
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
debug2: dh_gen_key: priv key bits set: 135/256                                  
debug2: bits set: 511/1024                                                      
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent                                           
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY                                     
debug1: checking without port identifier                                        
debug1: Host 'izilion' is known and matches the RSA host key.                   
debug1: Found key in /root/.ssh/known_hosts:1                                   
debug1: found matching key w/out port                                           
debug2: bits set: 541/1024                                                      
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
debug1: Authentications that can continue: publickey,password                   
debug1: Next authentication method: publickey                                   
debug1: Trying private key: /root/.ssh/identity                                 
debug1: Trying private key: /root/.ssh/id_rsa                                   
debug1: Trying private key: /root/.ssh/id_dsa                                   
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
isilion@izilion's password:
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: Sending env LANG = es_ES.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Linux izilion 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Thu Feb  5 01:53:56 2009 from izilion
isilion@izilion:~$
 

(LOGIN OK, but this is only with my computer name. i want to gain access to my comp through internet just by writing ssh -p1720 isilion@89.x.172.x
If i try this last as root, this is what i have:)


root@izilion:/home/isilion# ssh -vv -p 1720 isilion@89.x.172.x
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 89.x.172.x [89.x.172.x] port 1720.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
root@izilion:/home/isilion#

and, this is my sshd_config file:

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 1720
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2,1
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
LoginGraceTime 45
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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

UsePAM yes

--------------------------------------------






please help. thanx

---

### Post by spiderbatdad on 2009-02-04
just delete the authorized_keys file on your client machine and log in again.

---

### Post by Isilion on 2009-02-04
where is it located? please

---

### Post by spiderbatdad on 2009-02-04
in a hidden directory .ssh in your home folder. However, looking at the error message again, it appears the server also want the public key from the client...usually uploaded from the client with the command:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@ip.of.server
```Of course you will need a means of logging in to upload the key. Temporarily enabling password logins works.

---

### Post by Isilion on 2009-02-04
there is no file called authorized_keys in ~/.ssh

please answer.

---

### Post by Isilion on 2009-02-04
i tryed your command but...


[email]root@izilion:~/.ssh[/email]# ssh-copy-id -i ~/.ssh/id_rsa.pub isilion@izilion
/usr/bin/ssh-copy-id: ERROR: No identities found
[email]root@izilion:~/.ssh[/email]# ssh-copy-id -i ~/.ssh/id_rsa.pub isilion@89.x.172.x
/usr/bin/ssh-copy-id: ERROR: No identities found
[email]root@izilion:~/.ssh[/email]#

---

### Post by spiderbatdad on 2009-02-04
so it seems you have not generated any keys?
perhaps look in /etc/ssh

see this guide also:
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by Isilion on 2009-02-04
i ve read carefully that link and edited some options, generated the rsa key for isilion etc, but i get the same 3 problems:

1. it shays someone is doing something nasty... when i try to connect via ssh -p 1720 isilion@izilion

2. as root, i can access my pc via ssh -p 1720 isilion@izilion. this is ok but why as root i can and it says 1. as isilion?

3. as root, this is what i got with ssh -vv -p 1720 isilion@89.x.172.x

root@izilion:/home/isilion# ssh -vv -p 1720 isilion@89.x.172.x
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 89.x.172.x [89.x.172.x] port 1720.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /root/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /root/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
root@izilion:/home/isilion#

has changed, but still not connect. i dunno why please help mee!!

---

### Post by liquidpele on 2009-02-04
Okay, so lets look at some of the text ssh prints for you here:
====
The fingerprint for the RSA key sent by the remote host is
97:a6:1c:8d:e2:95:c1:ef:f8:2e:11:d3:88:09:3a:c3.
Please contact your system administrator.
Add correct host key in /home/isilion/.ssh/known_hosts to get rid of this message.
Offending key in /home/isilion/.ssh/known_hosts:7
====

notice the ~/.ssh/known_hosts file there?  
Delete that file, or just delete/update line #7 like it says, and then try it again.

---

### Post by Isilion on 2009-02-04
> **liquidpele said:**
> Okay, so lets look at some of the text ssh prints for you here:
====
The fingerprint for the RSA key sent by the remote host is
97:a6:1c:8d:e2:95:c1:ef:f8:2e:11:d3:88:09:3a:c3.
Please contact your system administrator.
Add correct host key in /home/isilion/.ssh/known_hosts to get rid of this message.
Offending key in /home/isilion/.ssh/known_hosts:7
====

notice the ~/.ssh/known_hosts file there?  
Delete that file, or just delete/update line #7 like it says, and then try it again.

Done all that, then..:

isilion@izilion:~$ ssh -p 1720 isilion@izilion
Bienvenido a Izilion.
Quis Custodiet Ipsos Custodes?
isilion@izilion's password:

isilion@izilion:~$ ssh -p 1720 isilion@89.x.172.x
ssh_exchange_identification: Connection closed by remote host
isilion@izilion:~$ ssh -vv -p 1720 isilion@89.x.172.x
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 89.x.172.x [89.x.172.x] port 1720.
debug1: Connection established.
debug1: identity file /home/isilion/.ssh/identity type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/isilion/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/isilion/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
isilion@izilion:~$

first login ok, but ip way still refusing.

---

### Post by Isilion on 2009-02-04
...
debug1: identity file /home/isilion/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/isilion/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
isilion@izilion:~$
...


i did this:

$ ssh-keygen -t dsa

generated a key and now i get this output:


isilion@izilion:~$ ssh -p 1720 isilion@89.x.172.x
ssh_exchange_identification: Connection closed by remote host
isilion@izilion:~$ ssh -vv -p 1720 isilion@89.x72.x
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 89.x172x [89x17x] port 1720.
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


im really stuckt now... :(

---

### Post by Francewhoa on 2009-06-26
Same here. I found a solution on this post: [http://ubuntuforums.org/showpost.php...9&postcount=10]("http://ubuntuforums.org/showpost.php?p=7521619&postcount=10")

---

### Post by smit0737 on 2009-07-21
> **liquidpele said:**
> Okay, so lets look at some of the text ssh prints for you here:
====
The fingerprint for the RSA key sent by the remote host is
97:a6:1c:8d:e2:95:c1:ef:f8:2e:11:d3:88:09:3a:c3.
Please contact your system administrator.
Add correct host key in /home/isilion/.ssh/known_hosts to get rid of this message.
Offending key in /home/isilion/.ssh/known_hosts:7
====

notice the ~/.ssh/known_hosts file there?  
Delete that file, or just delete/update line #7 like it says, and then try it again.

This worked for me.  Thanks liquidpele.

---

