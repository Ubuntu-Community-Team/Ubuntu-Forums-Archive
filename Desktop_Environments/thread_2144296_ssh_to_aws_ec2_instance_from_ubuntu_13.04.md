---
title: "ssh to aws ec2 instance from ubuntu 13.04"
date: 2013-05-11
forum: Desktop Environments
---

### Post by khoshalar on 2013-05-11
Hi .

I just installed ubuntu 13.04 saucy desktop and its really amazing,its just the way I was hoping it to be.The user interface cant be any better from my experince with previous versions.,superb.

but I have one problem which is connecting to ec2 instance from terminal., I have downloaded the .pem file and have set that to permission chmod 600.and what i have been getting is Permission denied (publickey).

I have pasted below the output of ssh -v , please help me with this issue to connect me to ec2 instance from ubuntu terminal


[EMAIL="khoshal@khoshal-Aspire-4736Z:~/.ssh"]khoshal@khoshal-Aspire-4736Z:~/.ssh[/EMAIL]$ ssh -v -i khoshal.pem [EMAIL="ubuntu@ec2-54-215-7-14.us-west-1.compute.amazonaws.com"]ubuntu@ec2-54-215-7-14.us-west-1.compute.amazonaws.com[/EMAIL]
OpenSSH_6.2p1 Debian-2, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to ec2-54-215-7-14.us-west-1.compute.amazonaws.com [54.215.7.14] port 22.
debug1: Connection established.
debug1: identity file khoshal.pem type -1
debug1: identity file khoshal.pem-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p1 Debian-2
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH_5*
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 5b:c2:5d:05:f8:23:ff:99:1f:10:32:04:fe:4e:04:58
debug1: Host 'ec2-54-215-7-14.us-west-1.compute.amazonaws.com' is known and matches the ECDSA host key.
debug1: Found key in /home/khoshal/.ssh/known_hosts:2
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: khoshal.pem
debug1: Authentications that can continue: publickey
debug1: Offering RSA public key: khoshal@khoshal-Aspire-4736Z
debug1: Authentications that can continue: publickey
debug1: Offering DSA public key: khoshal@khoshal-Aspire-4736Z
debug1: Authentications that can continue: publickey
debug1: Trying private key: khoshal.pem
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

Please help me fix this issue.

Thanks in advance.

---

### Post by khoshalar on 2013-05-15
> **khoshalar said:**
> Hi .

I just installed ubuntu 13.04 saucy desktop and its really amazing,its just the way I was hoping it to be.The user interface cant be any better from my experince with previous versions.,superb.

but I have one problem which is connecting to ec2 instance from terminal., I have downloaded the .pem file and have set that to permission chmod 600.and what i have been getting is Permission denied (publickey).

I have pasted below the output of ssh -v , please help me with this issue to connect me to ec2 instance from ubuntu terminal


[EMAIL="khoshal@khoshal-Aspire-4736Z:~/.ssh"]khoshal@khoshal-Aspire-4736Z:~/.ssh[/EMAIL]$ ssh -v -i khoshal.pem [EMAIL="ubuntu@ec2-54-215-7-14.us-west-1.compute.amazonaws.com"]ubuntu@ec2-54-215-7-14.us-west-1.compute.amazonaws.com[/EMAIL]
OpenSSH_6.2p1 Debian-2, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to ec2-54-215-7-14.us-west-1.compute.amazonaws.com [54.215.7.14] port 22.
debug1: Connection established.
debug1: identity file khoshal.pem type -1
debug1: identity file khoshal.pem-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2p1 Debian-2
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH_5*
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 5b:c2:5d:05:f8:23:ff:99:1f:10:32:04:fe:4e:04:58
debug1: Host 'ec2-54-215-7-14.us-west-1.compute.amazonaws.com' is known and matches the ECDSA host key.
debug1: Found key in /home/khoshal/.ssh/known_hosts:2
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: khoshal.pem
debug1: Authentications that can continue: publickey
debug1: Offering RSA public key: khoshal@khoshal-Aspire-4736Z
debug1: Authentications that can continue: publickey
debug1: Offering DSA public key: khoshal@khoshal-Aspire-4736Z
debug1: Authentications that can continue: publickey
debug1: Trying private key: khoshal.pem
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

Please help me fix this issue.

Thanks in advance.

Hi ,Please suggest me as to what ,school-boy error i am doing in the above mentioned.

many  thanks,

---

