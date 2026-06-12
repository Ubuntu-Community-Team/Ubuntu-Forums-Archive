---
title: "How can I find out my video driver filename?"
date: 2009-01-07
forum: General Help
---

### Post by jnewl on 2009-01-07
I need to supply a registry setting for Wine that requires the filename of my videocard driver. I know the driver version number, but I can't figure out how to find out the filename. Can someone tell me? Any help would be greatly appreciated.

EDIT: Here's my driver version no.: NVidia 177.80

---

### Post by jnewl on 2009-01-07
Is this a stupid question? Sometimes I fail to see the forest for the trees.

---

### Post by sdennie on 2009-01-07
What do you mean by "driver"?  The nvidia driver consists of a kernel module, various shared libraries, binaries other other things scattered across the system.  If you want to see exactly what the 177.80 driver installs, download the manual installation version from: [http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html) and then:

```

sh NVIDIA-Linux-x86-177.80-pkg1.run -x
cd NVIDIA-Linux-x86-177.80-pkg1

```

The contents of the "usr" directory should be approximately what is on your machine with the exception of the kernel module.  To find the kernel module try:

```

find /lib/modules/`uname -r` -name "nvidia.ko"

```

Having said all that, I'm not sure if this information will help.  The Windows registry isn't likely to understand any of the information you will get from these commands.

---

### Post by linux_tech on 2009-01-07
```
cat /var/log/Xorg.0.log
```

---

### Post by jnewl on 2009-01-08
> **sdennie said:**
> What do you mean by "driver"?  The nvidia driver consists of a kernel module, various shared libraries, binaries other other things scattered across the system.  If you want to see exactly what the 177.80 driver installs, download the manual installation version from: [http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html) and then:
<snip>
Having said all that, I'm not sure if this information will help.  The Windows registry isn't likely to understand any of the information you will get from these commands.

Ok, thank you. I'll try that. The example given for what I need to put in the registry was a .dll file, so I guess I'll look for the shared library files.

EDIT: Here's the specific key they're telling me to add to the Direct3D key in the registry: **VideoDriver = nv4_disp.dll** (example)

---

### Post by sdennie on 2009-01-08
> **jnewl said:**
> Ok, thank you. I'll try that. The example given for what I need to put in the registry was a .dll file, so I guess I'll look for the shared library files.

That's exactly why I don't think it's going to work.  You will find no .dll files in your linux driver installation.

---

### Post by jnewl on 2009-01-08
Ok. Thank you for the information. I don't know what's going on, because this guy insists the game wouldn't work for him until he supplied that key+info in the registry. He says I need to substitute my own info for what he put, but I guess I'll try to get by without it or see if putting the same thing he used works :)

Sorry to bother you with a red herring. I didn't know.

---

