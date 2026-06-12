---
title: "Kernel compilation error"
date: 2009-04-05
forum: General Help
---

### Post by beno1990 on 2009-04-05
Okay, I'm trying to compile the new 2.6.29 kernel for my servers but whenever I run

```
cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
```

I get the following error:

```

orcaria:/usr/src/linux# cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
  HOSTCC  scripts/basic/fixdep
/bin/sh: scripts/basic/fixdep: Permission denied
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

```

I've checked the permissions on the file ./scripts/basic/fixdep and tried chmodding and chgrping it but then when I try to run the command above I get the same error and find the file has been chmodded and chgrped back to root.

Thanks, everyone.

---

### Post by geraldm on 2009-04-05
I suggest breaking down the single line commands into 2 or three separate
commands and go from that.  The last command would be make oldconfig.
I do not see using an automated response answer  to any questions posed.
There are usually very few new questions that need to be asked.

regards
Gerald

---

