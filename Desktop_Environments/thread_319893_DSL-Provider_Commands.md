---
title: "DSL-Provider Commands"
date: 2006-12-16
forum: Desktop Environments
---

### Post by Guns90 on 2006-12-16
Good Morning.  I am using Dapper.  I can turn my internet access on and off while in a session by using 'sudo pon (or poff) dsl-provider', but when the computer is shut down and started, it turns dsl-provider back on in the boot-up.  How can I have the dsl-provider turned off during boot-up so that it may only be turned on through the terminal?  Thanks.

Gary

---

### Post by Guns90 on 2006-12-17
Anyone?  Please??

---

### Post by Juan_VCS on 2006-12-25
Run pppoeconf again and when it asks you if you want it to start it up on boot, say no.

---

