---
title: "Having an issue with ppa.launchpad.net"
date: 2009-01-28
forum: General Help
---

### Post by psmaster on 2009-01-28
When ever I update I get an error:
```

W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60487016493B3065

```

Can someone help me out with this?

---

### Post by Partyboi2 on 2009-01-28
Open a terminal and
```
gpg --keyserver keyserver.ubuntu.com --recv 493b3065
```
then
```
gpg --export --armor 493b3065 | sudo apt-key add -
```

---

### Post by psmaster on 2009-01-29
the keyserver has timed out:
```

psmaster@conquest:~$ gpg --keyserver keyserver.ubuntu.com --recv 493b3065
gpg: requesting key 493B3065 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```
which means that the other command would not work either:
```

psmaster@conquest:~$ gpg --export --armor 493b3065 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

```

---

### Post by Partyboi2 on 2009-01-29
Wait for awhile and try again.

---

### Post by jms1989 on 2009-01-29
I tried it and had no problems. You could be having a dns issue.

---

### Post by psmaster on 2009-01-29
> **jms1989 said:**
> I tried it and had no problems. You could be having a dns issue.

That is probably it. I have Insight and I am on a wireless home network with 6 other people :P

---

### Post by psmaster on 2009-01-29
Thanks everybody. Got it working now :D

---

### Post by bootdoc on 2009-01-30
i have tried several times to get the gpg key and i keep getting server timed out.

---

### Post by psmaster on 2009-01-30
> **bootdoc said:**
> i have tried several times to get the gpg key and i keep getting server timed out.

If you have a wireless connection, try what I did, connect to someone elses network :D

---

### Post by bootdoc on 2009-01-30
I have wireless card in my desktop.  too far from modem for wired connection.  I tried the same command on laptop with a wired connection and got same error.

---

