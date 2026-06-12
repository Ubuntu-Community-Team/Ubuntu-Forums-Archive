---
title: "'Host'/SSH problems"
date: 2006-07-15
forum: Desktop Environments
---

### Post by immesys on 2006-07-15
I am unable to SSH into any systems without pinging them first. When I try, I get this:

```

root@Shodan:/home#ssh -vvv -l user766 shell.rucus.net
OpenSSH_4.2p1 Debian-7ubuntu3, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to shell.rucus.net [1.0.0.0] port 22.
debug1: connect to address 1.0.0.0 port 22: Connection timed out
ssh: connect to host shell.rucus.net port 22: Connection timed out

```

I think the problem might lie in the [1.0.0.0] :) 

All other internet apps seems to run okay. If I ping the pc I'm connecting to and directly afterwards SSH into it then it works.
Also if I use 'host' I get:
```

root@Shodan:/home# host shell.rucus.net
shell.rucus.net has address 146.231.115.33
;; Warning: Message parser reports malformed message packet.
;; connection timed out; no servers could be reached

```

I'm really new at linux and I'm kind of stumped with this problem. Can anybody give suggestions?

I'm running Kubuntu 6.06, I have a d-link DSL-g604t router. Thanks

---

