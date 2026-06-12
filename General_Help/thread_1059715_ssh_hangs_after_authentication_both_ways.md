---
title: "ssh hangs after authentication both ways"
date: 2009-02-04
forum: General Help
---

### Post by pesqair on 2009-02-04
i am trying to ssh into a friend's ubuntu. hangs after authentication

```
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/pesqair/.ssh/identity type -1
debug1: identity file /home/pesqair/.ssh/id_rsa type -1
debug1: identity file /home/pesqair/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '98.14.119.111' is known and matches the RSA host key.
debug1: Found key in /home/pesqair/.ssh/known_hosts:7
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/pesqair/.ssh/identity
debug1: Trying private key: /home/pesqair/.ssh/id_rsa
debug1: Trying private key: /home/pesqair/.ssh/id_dsa
debug1: Next authentication method: password
pesqair@xxx.xxx.xxx.xxx's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8

```

i can ssh anywhere else and others can ssh in to me without any problems
he can't ssh into me either

---

### Post by pesqair on 2009-02-04
anyone?

---

### Post by pesqair on 2009-02-04
bump
if you need me to provide anything else i will.
thanks

---

### Post by whitegourd on 2009-02-04
See if this will help ...

[http://ubuntuforums.org/showthread.php?t=434444](http://ubuntuforums.org/showthread.php?t=434444)

---

