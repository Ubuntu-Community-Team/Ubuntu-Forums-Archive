---
title: "I want to uninstall kde 4"
date: 2008-05-01
forum: Desktop Environments
---

### Post by nihilion on 2008-05-01
Hello, 
I'm new to linux and recently installed Kubuntu 8.0.4 with the KDE4 desktop. I've found the KDE 4 desktop buggy and annoying, and much prefer KDE3.5.9.  

I installed KDE3.5.9 and am happy with it, but I can't seem to get rid of KDE4. I want it off my system completely. I tried using the package manager, but that didn't seem to do anything except make it angry.  Currently, KDE4 is my default windows manager, and I would like to at least change the default to KDe3, but I can't even do that. Please help me!

Thanks for your time.

Nick

---

### Post by nihilion on 2008-05-01
no takers?

---

### Post by Xiong Chiamiov on 2008-05-01
Pretty much everybody hates KDE4, except app writers who love what they did backend.

I had much the same reaction as you, but I ran into some rather odd problems when I uninstalled 4 (perhaps due to the screwy things I'm always doing to this poor computer).  Since then, I've actually reinstalled it for the libraries (so I can get updated versions of many programs) and the updated versions of a few of the KDE apps.

To uninstall KDE4, try
```

sudo apt-get remove kde4-core

```

To just make KDE3 your default window manager, run
```

sudo dpkg-reconfigure kdm

```
and choose kdm.

---

