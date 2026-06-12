---
title: "installing madwifi drivers on lenny"
date: 2008-07-20
forum: Debian
---

### Post by UniverseA7X on 2008-07-20
Hi. I installed Debian lenny on my macbook just last night, and i need the atheros driversfrom madwifi to get wireless, however when i downloaded the source and tried to compile the code with make, it gave me this error, which i don't know what to do with. I understand it, but I don't know what to do to alleviate it.

```
macbook:/usr/src/modules/madwifi# make
/bin/sh: line 0: cd: /lib/modules/2.6.24-1-686/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.24-1-686/build is missing, please set KERNELPATH.  Stop.

```

help is appreciated. I'm learning more and more everyday by doing this kind of stuff. :)

---

### Post by Bachstelze on 2008-07-21
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by benuski on 2008-07-21
Or install module-assistant from the repositories, and then do "m-a prepare" and then "m-a a-i madwifi".  That should download all of the dependencies and then automatically do the configure make and make install.

That might not be the correct auto-install command, but it should be something close to that.

---

### Post by UniverseA7X on 2008-07-23
> **HymnToLife said:**
> ```
sudo apt-get install linux-headers-`uname -r`
```

Thank you. :)

> **benuski said:**
> Or install module-assistant from the repositories, and then do "m-a prepare" and then "m-a a-i madwifi".  That should download all of the dependencies and then automatically do the configure make and make install.

That might not be the correct auto-install command, but it should be something close to that.

I think you're right, those are the commands from the Madwifi howto. Thanks :) I'll let you know if it works or not.

---

### Post by UniverseA7X on 2008-07-23
I ended up going into synaptic and getting a newer kernel with it's headers. 2.6.25.

then downloaded madwifi, followed the instructions, and with a reboot, wireless!

Thanks for your help. :)

---

