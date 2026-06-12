---
title: "ssh X11 forwarding (ssh -x) doesn't work ?"
date: 2005-11-17
forum: Desktop Environments
---

### Post by ivar on 2005-11-17
I'm kinda stuck trying to get X11 forwarding working over ssh.

I know that ssh -x used to work (as in I could start gui apps in the background from the remote shell and they'd appear on my local machine) but for some reason connecting from my laptop (breezy i386) to my server (breezy amd64) X11 forwarding doesn't work. 

The /etc/ssh/sshd_config  on the server has :
X11Forwarding yes
X11DisplayOffset 10

locally, /etc/ssh/ssh has :
ForwardX11 yes
ForwardX11Trusted yes

I'm also using xauth which could be messing things  up
what could I be missing ?  ssh -xv output below (if it helps)

I'd really like to get this going. so any help greatly appreciated.

$ ssh -xv happylion
OpenSSH_4.1p1 Debian-7ubuntu4, OpenSSL 0.9.7g 11 Apr 2005
debug1: Reading configuration data /home/ivar/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to happylion [xx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/ivar/.ssh/identity type -1
debug1: identity file /home/ivar/.ssh/id_rsa type -1
debug1: identity file /home/ivar/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.1p1 Debia n-7ubuntu4
debug1: match: OpenSSH_4.1p1 Debian-7ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'happylion' is known and matches the RSA host key.
debug1: Found key in /home/ivar/.ssh/known_hosts:16
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ivar/.ssh/identity
debug1: Trying private key: /home/ivar/.ssh/id_rsa
debug1: Offering public key: /home/ivar/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 433
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/ivar/.ssh/id_dsa':
<<valid passphrased entered>>
debug1: read PEM private key done: type DSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_CA
Linux happylion 2.6.12-9-amd64-k8 #1 Mon Oct 10 13:13:36 BST 2005 x86_64 GNU/Linux
bonjour@happylion !

---

### Post by timfrost on 2005-11-17
Hmm. When I do ssh -v, I get a line in the debug:
debug1: Requesting X11 forwarding with authentication spoofing.


But if I use 'ssh -xv', that line doesn't appear.  Which isn't surprising, as the option "-x' (lower case) DISABLES X11 forwarding, while '-X' UPPER CASE) enables X11 forwarding

---

### Post by ivar on 2005-11-17
[QUOTE=timfrost]Hmm. When I do ssh -v, I get a line in the debug:
debug1: Requesting X11 forwarding with authentication spoofing.


But if I use 'ssh -xv', that line doesn't appear.  Which isn't surprising, as the option "-x' (lower case) DISABLES X11 forwarding, while '-X' UPPER CASE) enables X11 forwarding[/QUOTE]

oh man. slaps forehead. ug. 

thanks for your help. :)

---

