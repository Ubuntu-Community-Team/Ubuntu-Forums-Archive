---
title: "Can't start Compiz on Nvidia Card"
date: 2006-08-30
forum: Desktop Environments
---

### Post by bsander on 2006-08-30
Hey all,

I've tried the better part of this day to get XGL/Compiz working on my Kubuntu installation, using various HOWTOs on this forum. XGL was no problem, but Compiz won't start. I get this problem:
> compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0

Many people in those threads also have this problem, and the solution as I understand it has something to do with the nvidia driver overwriting some mesa lib (libGL.so.1.2) that should be placed back. I tried all variants of solutions from those threads (since I restarted my X server many times today I haven't really kept track of all the threads I visited) but none worked for me.. :(

I was hoping someone could help me get through this so that I too may enjoy the XGL/compiz goodness :D

(I have a Nvidia GeForce Go 7600 card with 128MB, so that shouldn't be the problem :) )

---

### Post by hanzomon4 on 2006-08-30
You need to LD_PRELOAD libGL.so.1.2. This guide should help [How I fixed GLXFBConfig problem]("http://www.compiz.net/topic-1066-how-fixed-glxfbconfig-problem")

---

### Post by bsander on 2006-08-31
While I hadn't seen that thread yet, it also didn't solve my problem.. I tried the reinstalling again and ldd points to libGL.so.1:

```
sander@Sander-VAIO:~$ ldd /usr/bin/compiz.real | grep libGL.so.1
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ebf000)
sander@Sander-VAIO:~$ ldd /usr/bin/glxinfo | grep libGL.so.1
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ed9000)

```

So I tried:
```
sander@Sander-VAIO:~$ LD_PRELOAD=/opt/mesa/libGL.so.1 compiz --replace gconf &
```

(after copying the original libgGL.so.1 and .so.1.2 to /opt/mesa) but it still gives me the same error as above.. The same happens when I try reloading the .so.1.2 :(

---

### Post by hanzomon4 on 2006-08-31
Run this command. Then LD_PRELOAD the lib it finds.
> locate libGL.so.1.2.xlibmesa

---

