---
title: "Question about configuring xorg"
date: 2006-10-01
forum: Desktop Environments
---

### Post by ardchoille on 2006-10-01
On a new Ubuntu install, I always do 'sudo dpkg-reconfigure xserver-xorg' to customise some things. However, I see other people using this command:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and I am wondering what the "-phigh" is for. I looked in man dpkg-reconfigure and I didn't see some of those options. What exactly does adding -phigh do? Should I be adding this to my dpkg-reconfigure xserver-xorg commands from now on? It seems to work fine without it.

Any ideas?

---

### Post by jd65pl on 2006-10-01
By adding "-phigh" only the option to change the resolution is available in the set-up process. I suppose it avoids some confusion for those who are not familiar with their display settings and provides easier access to this commonly used function of
```
sudo dpkg-reconfigure xserver-xorg
```

J

---

### Post by ardchoille on 2006-10-01
> **jd65pl said:**
> By adding "-phigh" only the option to change the resolution is available in the set-up process. I suppose it avoids some confusion for those who are not familiar with their display settings and provides easier access to this commonly used function of
```
sudo dpkg-reconfigure xserver-xorg
```

J

Ah, ok, that makes sense. I can see where that full setup can be confusing to some.. it was confusing to me the first time I ran the full setup.

Thank you for the info :)

---

