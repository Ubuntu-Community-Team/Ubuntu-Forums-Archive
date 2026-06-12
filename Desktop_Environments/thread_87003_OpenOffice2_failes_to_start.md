---
title: "OpenOffice2 failes to start"
date: 2005-11-07
forum: Desktop Environments
---

### Post by Navyblue on 2005-11-07
Typing "ooffice2" at command prompt would give me this:

```

I18N: X Window System doesn't support locale "en_GB"
I18N: X Window System doesn't support locale "en_US"
I18N: X Window System doesn't support locale "C"
Qt: Locales not supported on X server
*** glibc detected *** free(): invalid next size (fast): 0x080defa0 ***
KCrash: Application 'soffice.bin.real' crashing...
/usr/lib/openoffice2/program/soffice: line 224: 10127 Alarm clock             "$sd_prog/$sd_binary" "$@"

```

I have used "dpkg-reconfigure locales" and en_GB and en_US are among those selected.

I am running the plain vanilla openoffice2 from the Ubuntu repository. I am not sure if it is the recent update that caused this.

---

### Post by Navyblue on 2005-11-07
Btw, this problem occur on my AMD64 box. The other 32bit box ran just fine.

---

### Post by Navyblue on 2005-11-07
I have uninstalled and reinstalled ooffice2, but no difference.

Help please.

---

### Post by Navyblue on 2005-11-07
I suddenly remembered something, prior to this I have used automatix to install midi support and fonts, I'm not sure if it is related.

---

### Post by Navyblue on 2005-11-08
I have again reinstalled oofice2, this time I get a different message:

```

/usr/lib/openoffice2/program/soffice: line 224: /usr/lib/openoffice2/program/soffice.bin: No such file or directory

```

Why does both errors occurs on line 224?

---

### Post by Navyblue on 2005-11-10
I have solved my problem.

For those who are interested to know.

For some reason I am missing a file /usr/lib/openoffice2/program/soffice.bin

The solution is to create it with the following content and make it executable.

```
#! /bin/sh

GTK_PATH=/usr/lib32/gtk-2.0 LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 exec "$0".real "$@"
```

---

### Post by Navyblue on 2005-11-10
Please do me a favour. If you are running Kubuntu (not Ubuntu), please post the content of your /usr/lib/openoffice2/program/soffice.bin

My ooffice2 now look so gnomish, I guess that file must be responsible for it. Yes I have my openoffice.org2-kde package installed and I even reinstalled it.

Thank you.

---

### Post by Navyblue on 2005-11-11
I found out that by installing the ia32-libs-gtk would give the error message in the first post, and removing that package would make /usr/lib/openoffice2/program/soffice.bin dissapear.

No one runs openoffice2 on Kubuntu? That's very weird. :confused:

---

### Post by maechler on 2005-11-16
I'm also using AMD-64 ubuntu breezy; and have had the exact same problem as you guys:  soffice.bin was just missing  even though it should be provided by
openoffice.org2-core  :

  root@deb2:~# dpkg -S /usr/lib/openoffice2/program/soffice.bin

  diversion by ia32-libs-gtk from: /usr/lib/openoffice2/program/soffice.bin
  diversion by ia32-libs-gtk to: /usr/lib/openoffice2/program/soffice.bin.real
  openoffice.org2-core: /usr/lib/openoffice2/program/soffice.bin

So yes, these 'diversions' have been the real problem and the script below indeed calls 'soffice.bin.real'.
Note however that for me, the LD_PRELOAD part actually just gives warnings:

ERROR: ld.so: object '/usr/lib32/libpangohack.so.0.0' from LD_PRELOAD cannot be preloaded: ignored.

so I left the LD_PRELOAD=.... off the exec line.

Well, it's nice that I found this thread quickly thanks to google. :smile: 
OTOH, it's my first small disappointment with ubuntu package :( 

QUOTE=Navyblue]I have solved my problem.

For those who are interested to know.

For some reason I am missing a file /usr/lib/openoffice2/program/soffice.bin

The solution is to create it with the following content and make it executable.

```
#! /bin/sh

GTK_PATH=/usr/lib32/gtk-2.0 LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 exec "$0".real "$@"
```[/QUOTE]

---

### Post by Navyblue on 2005-11-23
it is sad to say that, since I can't get any help on this, I have to reinstall the system to solve the problem.

On top of that Openoffice2 on AMD64 Kubuntu look gnomish, I have a another box with 32 bit system with Kubuntu's Openoffice2 looks right.

---

