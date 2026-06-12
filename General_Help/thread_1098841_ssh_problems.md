---
title: "ssh problems"
date: 2009-03-17
forum: General Help
---

### Post by craeside on 2009-03-17
I am using latest ubuntu and generate my keys using 

ssh-keygen -t rsa -b 1024 

I than do the following which outputs to screen a Windows usable key 

ssh-keygen -e -f id_rsa.pub     

I than copy the screen output to file and name it id_rsa.pub  I than transfer this file to the windows server and place it in the user directory. 

I am using tectia for the ssh server on windows so any tip there for Public key authentication configuration would be helpful as well 

but than I get this out put from ubuntu; 

[B]OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.6 [192.168.1.6] port 22.
debug1: Connection established.
debug1: identity file /home/username/.ssh/identity type -1
debug1: identity file /home/username/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
debug1: identity file /home/craeside/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version 6.0.8.52 SSH Tectia Server
debug1: no match: 6.0.8.52 SSH Tectia Server
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client 3des-cbc hmac-sha1 none
debug1: kex: client->server 3des-cbc hmac-sha1 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host '192.168.1.6' is known and matches the RSA host key.
debug1: Found key in /home/username/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
Welcomedebug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/username/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Offering public key: Public Key
debug1: Authentications that can continue: publickey
debug1: Offering public key: id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/username/.ssh/identity
debug1: Trying private key: /home/username/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).


The output on te tectia server is this; 

[Mar 17 13:13:07] 2556 username@(null)
[Mar 17 13:13:07] 2556 buffer length = 30
[Mar 17 13:13:07] 2556 WARNING[2556]: LsaLogonUser() failed, status = 0xC000006D, sub_status = 0x00000000, err = 1326 
[Mar 17 13:13:07] 2556 WARNING[2556]: ssh_lsa_logon_user() failed, status = 0x00000000
[Mar 17 13:13:07] 428 SSHDAP DEBUG: LsaApLogonUser called
[Mar 17 13:13:07] 2304 debug[2556]: WARNING[2556]: ssh_lsa_logon_user() failed, status = 0x00000000
[Mar 17 13:13:07] 428 SSHDAP DEBUG: Verifying authentication information
[Mar 17 13:13:07] 428 SSHDAP DEBUG: Authentication information seems to be ok
[Mar 17 13:13:07] 428 SSHDAP DEBUG: Creating account name `username'
[Mar 17 13:13:07] 428 SSHDAP DEBUG: No domain name given, using workstation name as authentication authority.
[Mar 17 13:13:07] 428 SSHDAP DEBUG: authentication authority = SSHSERV.
[Mar 17 13:13:07] 428 SSHDAP DEBUG: login attempt by username@RSSHSERV
[Mar 17 13:13:07] 428 SSHDAP DEBUG: domain controller `(null)'
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Checking that account exists
[Mar 17 13:13:08] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Allocating logon session LUID
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Allocating logon session
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Creating token information
[Mar 17 13:13:08] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Failed to get SID size info, win err 1332
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Failed to get user SID
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Failed to create token information.
[Mar 17 13:13:08] 428 SSHDAP DEBUG: An error occurred, status 0xc0000225, win err 1168
[Mar 17 13:13:08] 428 SSHDAP DEBUG: Deleting logon session
[Mar 17 13:13:08] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:13:08] 2304 debug[2556]: WARNING[2556]: LsaLogonUser() failed, status = 0xC0000225, sub_status = 0x019BF6D4, err = 1168 
[Mar 17 13:13:08] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:13:08] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:13:08] 2556 WARNING[2556]: ssh_lsa_logon_user() failed, status = 0x019BF6D4
[Mar 17 13:13:08] 2556 WARNING[2556]: Failed to get user access token
[Mar 17 13:13:08] 2556 WARNING[2556]: Access token generating failure
[Mar 17 13:13:08] 2304 debug[2556]: WARNING[2556]: Access token generating failure
[Mar 17 13:13:19] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:13:28] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:13:30] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:14:05] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:14:09] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:14:10] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:14:29] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:14:39] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:14:40] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:15:15] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:15:28] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:15:39] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:15:50] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:16:25] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:16:29] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:17:00] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:17:12] 2304 debug[2564]: token source name = SSHSrv
[Mar 17 13:17:12] 2564 username@(null)
[Mar 17 13:17:12] 2564 buffer length = 30
[Mar 17 13:17:13] 2304 debug[2564]: WARNING[2564]: LsaLogonUser() failed, status = 0xC000006D, sub_status = 0x00000000, err = 1326 
[Mar 17 13:17:13] 428 SSHDAP DEBUG: LsaApLogonUser called
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Verifying authentication information
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Authentication information seems to be ok
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Creating account name `username'
[Mar 17 13:17:13] 428 SSHDAP DEBUG: No domain name given, using workstation name as authentication authority.
[Mar 17 13:17:13] 428 SSHDAP DEBUG: authentication authority = SSHSERV.
[Mar 17 13:17:13] 428 SSHDAP DEBUG: login attempt by username@SSHSERV
[Mar 17 13:17:13] 428 SSHDAP DEBUG: domain controller `(null)'
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Account exists
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Allocating logon session LUID
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Allocating logon session
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Getting token info for account RAESERV\craeside
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Failed to get SID size info, win err 1332
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Failed to get user SID
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Failed to create token information.
[Mar 17 13:17:13] 428 SSHDAP DEBUG: An error occurred, status 0xc0000225, win err 1168
[Mar 17 13:17:13] 428 SSHDAP DEBUG: Deleting logon session
[Mar 17 13:17:13] 428 SSHDAP DEBUG: LsaApLogonTerminated called
[Mar 17 13:17:13] 2304 debug[2564]: WARNING[2564]: LsaLogonUser() failed, status = 0xC0000225, sub_status = 0x015BF6D4, err = 1168 
[Mar 17 13:17:13] 2304 debug[2564]: WARNING[2564]: ssh_lsa_logon_user() failed, status = 0x015BF6D4
[Mar 17 13:17:13] 2304 debug[2564]: WARNING[2564]: Failed to get user access token
[Mar 17 13:17:13] 2304 debug[2564]: WARNING[2564]: Access token generating failure





So anyone help any ideas what I am doing wrong if you need my tectia server config say so as I have no problems posting as it is a sandboxed  test bed anyway.

---

### Post by Dr Small on 2009-03-17
It looks like it was looking for the id_dsa private file:
> debug1: Trying private key: /home/username/.ssh/id_dsa
debug1: No more authentication methods to try.

But you made a RSA key.

---

### Post by craeside on 2009-03-17
hmm why would it be looking for DSA key when its all rsa keys..... 

And why would the server  oh I See yah it tried the RSA key first but it failed and then it tried DSA 

Ughh lol this is frustrating me lol

---

