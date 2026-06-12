---
title: "ssh - what private key"
date: 2017-02-24
forum: Desktop Environments
---

### Post by Geoff_Lane on 2017-02-24
Folks,

I access three machines remotely (Two Raspberry Pi and one Ubuntu 14:04) using shared ssh key.

When originally setting this up I mistakenly thought I needed a key per remote device and created three keys (each with different names).

Now, all is working fine and I don't want to break any connections (particularly as one machine is in US and accessed from UK) but I'd like to tidy the files up a wee bit so is there any way of knowing which keys are used when negotiating a connection?

Geoff

---

### Post by TheFu on 2017-02-24
log files?
ssh -vvv ...

---

### Post by Geoff_Lane on 2017-02-24
> **TheFu said:**
> log files?
ssh -vvv ...

Thanks, that worked fine, now I know which key is being used but as I am accessing three different machines using the shared key method should I have three different key pairs on my client or can the key pair be used on three different servers?

As mentioned, [COLOR=#000080]**it is all logging in fine**[/COLOR], I have passwords disabled on remote machines and an extra user password is requested on my machine to unlock my key file but not 100% sure if I've done it correctly or am I just [COLOR=#ff0000]**LUCKY.**[/COLOR]

Geffers

---

