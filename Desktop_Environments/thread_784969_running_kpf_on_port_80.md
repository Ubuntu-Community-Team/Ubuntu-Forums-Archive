---
title: "running kpf on port 80"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Swords on 2008-05-07
Evening all. I realize that this question has more to do with the GNU/Linux OS than KDE itself, but I thought it would be most relevant here since I'm running kpf as an applet in the KDE panel.

Basically, I'm trying to run my little webserver on port 80 for simplicity's sake, since it's the standard port used for http. I understand that this is within the range of the "Reserved Ports" and so there will have to be some manipulation of permissions for it to work as desired. However, the more I look into it, the more confused I become, and I feel like I'm nowhere near accomplishing this on my own.

I'm not asking for a step by step, but could someone at least point me in the right direction? All help is appreciated.

---

### Post by dandart on 2008-07-10
Basically, you need to be root to listen to ports < 1024. So the webserver on port 80 will not work unless you run it as root, or choose a higher port.

---

