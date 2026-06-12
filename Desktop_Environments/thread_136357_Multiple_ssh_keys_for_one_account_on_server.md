---
title: "Multiple ssh keys for one account on server"
date: 2006-02-25
forum: Desktop Environments
---

### Post by markymarknz on 2006-02-25
Hi everyone,

Just been having a frustrating time trying to get my ssh server to accept multiple ssh keys for the same user.
I have previously been logging onto my server using putty and the ssh key generated with that. That has been working fine, but I decided I wanted to use my Ubuntu partition so I can ssh from that as well.
I added the ssh key to the authorized_keys file on the server, new line, no lines between and it doesn't seem to accept the ssh key for ubuntu.
I got it to print out the following information which seems to show that it is just rejecting the public key, but I don't know if I have set something up wrong or not. The ssh -v ... has the following info:

OpenSSH_4.1p1 Debian-7ubuntu4.1, OpenSSL 0.9.7g 11 Apr 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to bridie [192.168.1.254] port 22.
debug1: Connection established.
debug1: identity file /home/mark/.ssh/identity type -1
debug1: identity file /home/mark/.ssh/id_rsa type 1
debug1: identity file /home/mark/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.8.1p1 Deb ian-8.sarge.4
debug1: match: OpenSSH_3.8.1p1 Debian-8.sarge.4 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'bridie' is known and matches the RSA host key.
debug1: Found key in /home/mark/.ssh/known_hosts:6
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/mark/.ssh/id_rsa
Connection closed by 192.168.1.254

Any help would be appreciated.

Mark

---

### Post by markymarknz on 2006-02-26
Yeah so are there any ssh gurus out there ???

Thanks

---

### Post by gctaylor1 on 2006-02-26
I'm not an ssh guru but since no one else is responding...

The debug log seems to be okay.  The log doesn't directly point to the keys being bad.  I can see that you've got three keys that apparently are being read okay although I don't know what -1 is at the end of the line.   It would appear that you've got password authentication turned off or else the next authentication method after the keys fail would display password.  

You could trying increasing the verbosity on the client by adding more v's like -vvv .  I think about three is the most you'd want.  

Are you able to get a debug log from the server?  For that you could shut down the daemon and then start it with something like "/usr/sbin/sshd -ddd"   .  It might give you another clue.  If you have to leave the port 22 daemon running for other users you could start a new daemon on another port and use the debug option on the new daemon.  

Would it be worth your while to rename the authorized_keys file on the server and start with ssh-keygen again to create a new key and just use one key?

Any chance the permissions are messed up on either the authorized_keys file or the private keys?

---

### Post by markymarknz on 2006-02-27
Thanks gctaylor1 for your reply
I think you might be a bit modest, you do seem to know a fair bit about ssh :)
Anyway I actually worked out what was going wrong.

I backed up my authorized_keys file and tried just putting in my ubuntu ssh key and then log in, which worked !!
I then tried adding my putty ssh key to it and it also worked.
I then added the 3rd key and it didn't work again. So it came down to the 3rd key being broken. Originally it was placed in second place in the authorized_keys file so I guess it got to that one and had a problem then didn't get to the third one (ubuntu key).

So yeah thanks for that advice, good to see it working with multiple ssh keys for the same account.

Thanks again gctaylor1 for the advice.

---

