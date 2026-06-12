---
title: "Desktop and Server: Regenerate Keys after Install"
date: 2013-01-15
forum: Desktop Environments
---

### Post by noloader on 2013-01-15
Hi All,

This question is for a server, but it applies to my desktop installations too.

I recently installer Ubuntu Server 12.04 with OpenSSH, LAMP, and Samba. After installation and during first boot, I believe at least one set of [machine] keys is generated.

I have an [Entropy Key]("http://www.entropykey.co.uk/"), and I would like to re-generate all keys with a RNG/PRNG that I know is in good working order.

I believe the SSH server can be fixed up with:

```
ssh-keygen -f /etc/ssh/ssh_host_rsa_key -b 2048 -N '' -t rsa
ssh-keygen -f /etc/ssh/ssh_host_dsa_key -b 1024 -N '' -t dsa
ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -b 256 -N '' -t ecdsa
```Can anyone confirm that's all I need for SSH?

Can anyone point out where else  I need to look for other components, such as Apache or Samba?

Jeff

---

