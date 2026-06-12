---
title: "Serious problem with sshd on edgy beta desktop"
date: 2006-10-05
forum: Desktop Environments
---

### Post by benanzo on 2006-10-05
Hi.

I am having some serious problems with open-sshd on edgy beta desktop 2.6.17-10-generic.  I have 5 machines.  3 are headless running edgy beta server, 1 is a laptop running dapper and this one is my desktop running edgy beta desktop.  I have set up open-ssh on all 5 and can ssh to every machine BUT the edgy desktop, this one.  I can ssh from this machine to all the other machines and from and to all others except to this one.  I have literally copied and pasted the ssh_config and sshd_config as well as the authorized_keys and id_dsa with chmod 600 on all.  I am using the same user on each machine.  I have thoroughly checked the id_dsa and authorized_keys files for descrepencies, but they are ALL identical...still, when I ssh to another machine, I have to probs, but when I try to ssh back to this one...denied.

here's my output:

ben@server:~$ ssh -v desktop
OpenSSH_4.3p2 Debian-4ubuntu1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to desktop [10.0.0.2] port 22.
debug1: Connection established.
debug1: identity file /home/ben/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-4ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'desktop' is known and matches the RSA host key.
debug1: Found key in /home/ben/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ben/.ssh/id_dsa
debug1: read PEM private key done: type DSA
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey).
ben@server:~$



I have no idea why the id_dsa authorized_keys sshd_config and ssh_config files will work identically on all other machines EXCEPT edgy desktop beta.  I am seriously disturbed.  anyway..any help or direction would be great.  Thanks.

---

