---
title: "enable high mem support"
date: 2009-02-21
forum: General Help
---

### Post by canistel on 2009-02-21
I tried out debian for a while a few months ago, and they had a kernel called "high-mem" or something like that in their repository, which would basically enable more then 3GB of ram, while still keeping the "desktop" optimizations. I'm aware of the ubuntu server kernel which has support for more then 3GB, but it never ran well for me; nvidia blob hated it too.

So short of recompiling the kernel, is there any way to get the 4GB+ ram that I have on my system enabled, while using the desktop kernel?

Thanks...

---

### Post by cariboo on 2009-02-21
The easy way to get support for more tha 3.2Gb is to install the server kernel. Search synaptic for Linux-image-2.6.X-X-server. Where 2.6.X-X is the kernel you are running. IFyou aren't sure of what kernel you are running open an Apllictions-->Accessories-->Terminal and type:

```
uname -a
```

the result should look something like this:

```
Linux jack 2.6.28-8-generic #24-Ubuntu SMP Wed Feb 18 20:36:18 UTC 2009 x86_64 GNU/Linux
```

Note from the above output I run the 64bit kernel.

Installing a 64bit distribution is an other way of getting high memory support.

Jim

---

