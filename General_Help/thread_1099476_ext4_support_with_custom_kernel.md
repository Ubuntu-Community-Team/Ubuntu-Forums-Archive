---
title: "ext4 support with custom kernel"
date: 2009-03-18
forum: General Help
---

### Post by absolutezero1287 on 2009-03-18
Hi, I was thinking about compiling the Linux kernel with my own specifications. I've done this before in archlinux and my first step was always zcat /proc/config.gz but it seems that I can't access the defualt configs in this manner.

```

sudo zcat /proc/config.gz
gzip: /proc/config.gz: No such file or directory

```

---

### Post by sanderj on 2009-03-18
ext4 is built in in Jaunty Alpha 6 ([http://www.ubuntu.com/testing/jaunty/alpha6#Ext4%20filesystem%20support](http://www.ubuntu.com/testing/jaunty/alpha6#Ext4%20filesystem%20support)).

So the most easy way is to use Jaunty and select ext4 during install. 

Download from [http://cdimage.ubuntu.com/releases/jaunty/alpha-6/](http://cdimage.ubuntu.com/releases/jaunty/alpha-6/)

---

### Post by skymera on 2009-03-18
I think the config is located in the /boot/ directory.

I did find a great guide a while back on compiling kernels. It's a shame none of mine worked.

---

### Post by regala on 2009-03-18
> **absolutezero1287 said:**
> Hi, I was thinking about compiling the Linux kernel with my own specifications. I've done this before in archlinux and my first step was always zcat /proc/config.gz but it seems that I can't access the defualt configs in this manner.

```

sudo zcat /proc/config.gz
gzip: /proc/config.gz: No such file or directory

```

you need to insmod the right kernel module
```

# modprobe configs

```

at this point, the "file" /proc/config.gz exists.

---

### Post by absolutezero1287 on 2009-03-18
> **regala said:**
> you need to insmod the right kernel module
```

# modprobe configs

```

at this point, the "file" /proc/config.gz exists.

```

sudo modprobe configs
FATAL: Module configs not found.

```

Also, I can't update due to later versions of Ubuntu having problems with Compiz. Apparently, someone decided it would be great to blacklist my graphics card.

---

### Post by sdennie on 2009-03-18
Being able to access the current kernel config via proc is itself a kernel option.  On Ubuntu, this isn't really an issue because the currently running Ubuntu config is always, /boot/config-`uname -r`.  However, the kernel is smart these days and, with no configuration specified/added, "make menuconfig" uses the currently running kernels config as the basis.  You can also use "make oldconfig" to get a configuration process that only presents you with config options that don't exist in your old kernel config but do exist in this one.

---

