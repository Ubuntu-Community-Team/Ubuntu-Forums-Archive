---
title: "GOG Baldur's Gate 1 (.sh)"
date: 2015-12-17
forum: Gaming &amp; Leisure
---

### Post by ldc2357 on 2015-12-17
I am not new to linux, but I for the life of me cannot figure out how to run shell scripts. I downloaded BG1 from gog.com, after searching the internet for answers, I got this:

```

ldc@UbuntuBox:~/Games$ ./gogBaldursGateTheOriginalSaga2.0.0.9.sh 
Verifying archive integrity... All good.
Uncompressing Baldur's Gate: The Original Saga (GOG.com)  100%  
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
trying mojosetup in bin/linux/x86_64
USING en_US



PANIC
  Initial setup failed. Cannot continue.


Error: Couldn't run mojosetup

```

I have no clue what mojosetup is, all attempts to figure my way around this have failed. How do you guys run any scripts? I have build-essential. I was up to date when I tried this, I'm updating as I type this. I forgot to mention I'm running Ubuntu 15.10.

---

### Post by oldrocker99 on 2015-12-17
Here is how: ```
sudo sh nameofprogram.sh
```

You can also, if you want to keep it in your home folder:```
sh nameofprogram.sh
```

Post here if you still have the same problem. Good luck!

---

### Post by ldc2357 on 2015-12-17
```

ldc@UbuntuBox:~/Games$ sh gogBaldursGateTheOriginalSaga2.0.0.9.sh 
Verifying archive integrity... All good.
Uncompressing Baldur's Gate: The Original Saga (GOG.com)  100%  
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
trying mojosetup in bin/linux/x86_64
USING en_US



PANIC
  Initial setup failed. Cannot continue.


Error: Couldn't run mojosetup


```

I get the same error.

---

### Post by ldc2357 on 2015-12-17
For unrelated reasons i've decided to delete my gog account, so theres no need to bother with this issue anymore. Thanks for your help.

---

