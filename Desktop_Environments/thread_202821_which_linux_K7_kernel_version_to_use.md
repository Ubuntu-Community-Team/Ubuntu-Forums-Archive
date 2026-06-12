---
title: "which linux K7 kernel version to use?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by dronepower on 2006-06-24
I have an AMD 3000+ and I just installed the K7 kernel. 
The linux K7 kernel is version 2.16.15.23.
The image and header I got are both in version 2.16.15.23 and 2.16.15.25
Version 2.16.15.25 is for K7 SMP/UP, multicore synaptic says. 

Should I boot with version 2.16.15.23 now, cause my processor doesn't have a multicore?

---

### Post by Jucato on 2006-06-24
Just use the plain k7. Btw, there's also an updated kernel for k7 (2.6.15-25-k7)

---

### Post by dronepower on 2006-06-24
haven't seen the new version been updated by synaptic yet.

---

### Post by Jucato on 2006-06-24
Check if your repositories has the dapper-security lines enabled.

Although I couldn't exactly recommend upgrading to this new kernel if the current one (2.6.15-23-k7) is working perfectly for you. Some people, including me, have the unlucky experience of things going awry after the upgrade.

But you might be one of the lucky ones. Just remember not to remove the older kernel if you ever upgrade, so that you could have something to fall back on if things go wrong.

---

### Post by dronepower on 2006-06-24
[QUOTE=Fenyx]Check if your repositories has the dapper-security lines enabled.

Although I couldn't exactly recommend upgrading to this new kernel if the current one (2.6.15-23-k7) is working perfectly for you. Some people, including me, have the unlucky experience of things going awry after the upgrade.

But you might be one of the lucky ones. Just remember not to remove the older kernel if you ever upgrade, so that you could have something to fall back on if things go wrong.[/QUOTE]

well, I think I stick with this one then. so far I haven't experienced any perfomance boost with the 386 kernel en the K7 one.

awry <- learned a new english word today! :cool:

---

