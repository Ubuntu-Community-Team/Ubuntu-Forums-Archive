---
title: "evdev ???? in Jaunty"
date: 2009-05-01
forum: General Help
---

### Post by Chriis on 2009-05-01
Why in Jaunty " sudo modprobe evdev " return FATAL: Module evdev not found.

is it normal?? even if evdev is installed?? i see it installed in synaptic.


chriis

---

### Post by Chriis on 2009-05-01
bump!

---

### Post by Chriis on 2009-05-01
bump!

no one can help on that?

---

### Post by Chriis on 2009-05-01
bump! 


sorry but i realy need this answer

---

### Post by Chriis on 2009-05-01
bump!

---

### Post by Yellow Pasque on 2009-05-02
evdev isn't a kernel module. What are you trying to do?
[http://en.wikipedia.org/wiki/Evdev](http://en.wikipedia.org/wiki/Evdev)

---

### Post by Chriis on 2009-05-02
tryin to install piece of hardware, nostromo n50

[http://ubuntuforums.org/showthread.php?t=538319&highlight=nostromo]("http://ubuntuforums.org/showthread.php?t=538319&highlight=nostromo")

simple procedure, i' ve done it on gutsy, and now on junty (fresh install)
i can not re-do this installation,

Thanks for your help :)

chriis

---

### Post by unutbu on 2009-05-02
evdev.ko (the kernel module) is provided by linux-image-2.6.28-6-386: See [http://packages.ubuntu.com/search?searchon=contents&keywords=evdev.ko&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=evdev.ko&mode=exactfilename&suite=jaunty&arch=any)

---

### Post by Chriis on 2009-05-02
[http://packages.ubuntu.com/search?mode=exactfilename&suite=jaunty&section=all&arch=amd64&searchon=contents&keywords=evdev.ko]("http://packages.ubuntu.com/search?mode=exactfilename&suite=jaunty&section=all&arch=amd64&searchon=contents&keywords=evdev.ko")

Sorry forget to mention my arch is amd64

---

### Post by unutbu on 2009-05-02
Right. So it looks like you either have to compile a custom kernel, or install the 32-bit version of Jaunty. :(

---

### Post by cmcx_linux on 2009-05-04
Hey, I checked out the default config in the kernel source and it seems that evdev is built in the kernel and not as a module. That's why you can't find it when you try modeprobe. Hope it helps.

---

### Post by Chriis on 2009-05-07
yep, this help, any help is welcome,.. 

still can't get this controler to work, but i continu to 
search and read,..

I'll post my results as soon as it work,

Thanks,

Chriis

---

### Post by jespdj on 2009-05-07
If the driver is already built into the kernel as cmcx_linux says, then you don't need to install the driver. Have you tried to use the device (whatever it is...) without installing the driver?

---

### Post by Chriis on 2009-05-09
Yes i tried,

it returned:
 
```

nostromo_daemon[25745]: Found 050d:0805 at dev 4
nostromo_daemon[25745]: Starting reader_thread with fd=9 
nostromo_daemon[25745]: segfault at ffffffffbf7fe9e0 ip 00007f04c9b0eba8 sp 00007fffd4b7e290 error 4 in libpthread-2.9.so[7f04c9b07000+17000]
```

the deamon try to start but failed to

Thanks :)

---

