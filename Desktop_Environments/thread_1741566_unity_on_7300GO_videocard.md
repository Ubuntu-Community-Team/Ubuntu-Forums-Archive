---
title: "unity on 7300GO videocard"
date: 2011-04-28
forum: Desktop Environments
---

### Post by Crimson1988 on 2011-04-28
hello

i have a laptop with nvidia 7300GO graphics card. in beta 2 i had no problems running unity 3d and nvidia graphics driver, but now after latest updates unity stopped working and jockey shows that my graphics driver is activated but not in use... what's up with that?

i'm using ubuntu x64 btw

now gonna try to download final iso from official webpage instead of upgrading from beta, maybe it will change something...

sorry for my english

---

### Post by mikewhatever on 2011-04-28
Nvidia 7300/7400 go cards had been blacklisted because of problems people had with them. You can override the blacklisting by adding UNITY_FORCE_START=1 to /etc/environment. For more info, see the bug report:
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745)

---

### Post by Crimson1988 on 2011-04-28
thank you

---

