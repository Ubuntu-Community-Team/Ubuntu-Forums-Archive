---
title: "spicify listen address for vino-server (remote desktop)"
date: 2006-10-07
forum: Desktop Environments
---

### Post by zakhooi on 2006-10-07
Hi,

Can anyone explain to me where to define the listen address for vino-server (remote desktop)?
By default it listens on 5900 on alle IP's.
My server has more than one network card and I'd like to make it listen on only one of them.
(I know I can block traffic on 5900 using ip tables on the interface I don't want to use, but I'd like to get this done the proper way).
I couldn't find any config file for vino-server.


Thanks in advance

---

### Post by zakhooi on 2006-11-05
bump...

---

### Post by jBilbo on 2006-11-15
You can't.

[http://www.ubuntuforums.org/showthread.php?t=8742](http://www.ubuntuforums.org/showthread.php?t=8742)

---

### Post by zakhooi on 2006-11-15
As a workaround for this I made shorewall blocking traffic on port 5900 on all interfaces except the one I want to use.

---

