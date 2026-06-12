---
title: "Update Manager recommendations"
date: 2009-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kryos on 2009-08-15
Unsure of what should and should not be updated based upon description recommendations of individual updates, etc.  Typical description:

"This package contains the Linux kernel image for version 2.6.24 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

This last paragraph has always confused me.  Any thoughts?

Inspiron 530N
8.04 LTS

---

### Post by slakkie on 2009-08-15
First please do this:

```

sudo aptitude update

```

Could you tell me what the output is of the following command:

```

sudo aptitude -s safe-upgrade

```

Basicly, if you already have linux-image-generic, you will upgrade the package which actually contains the kernel, eg linux-image-x.y.z-generic.

You can see this by looking at the dependency of the meta package:

```

aptitude -D show linux-image-generic
# or
apt-cache depends linux-image-generic

```

If linux-image-x.y.z-generic will be upgraded the z part will be upgraded if you will.
linux-image-1.2.3-generic will be upgraded to 1.2.4, you will stay in the 1.2 branch of the kernel. 

If you don't like it you can go back to booting the older kernel via grub.

---

### Post by kryos on 2009-08-18
Thanks for the input.  Bit the bullet and installed all pertinent updates.

---

