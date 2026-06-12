---
title: "Command line version of Synaptic's &quot;Fix broken packages&quot;?"
date: 2006-05-01
forum: Desktop Environments
---

### Post by louis_nichols on 2006-05-01
Hi everybody!

Synaptic's option "Fix broken packages" sometimes comes in handy. I was wondering, though, what would be a CLI version of it, just in case something gets really broken.

Is it ```
sudo apt-get dist-upgrade
``` or is it something more subtile?

---

### Post by bluevoodoo1 on 2006-05-01
sudo apt-get install -f

---

### Post by MetalMusicAddict on 2006-05-01
**sudo apt-get install --fix-missing** works also.

---

### Post by louis_nichols on 2006-05-02
ok. thanks guys. it might come in handy if I'll ever be left with just the command line.

---

