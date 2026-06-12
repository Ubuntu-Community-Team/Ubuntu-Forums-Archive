---
title: "The volume &quot;filesystem root&quot; has only 307.5 MB disk space remaining"
date: 2015-09-30
forum: Desktop Environments
---

### Post by khurtsiya on 2015-09-30
And when I click Examine it shows also:

Could not scan folder "/" or some of the folders it contains.

Permission denied.

---

### Post by dino99 on 2015-09-30
check how many kernels are installed or not fully uninstalled (synaptic can help a lot in such a case)

---

### Post by khurtsiya on 2015-09-30
How can I do this in terminal?

---

### Post by Bashing-om on 2015-09-30
khurtsiya; Hello;

In response:
> 
How can I do this in terminal?

Termial command:
```

dpkg -l | grep linux-

```
is one way.

To remove the old kernel images:
```

sudo apt-get autoremove

```
Should prove effective.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-01
```
$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.15                                            all          Firmware for Linux kernel drivers
iU  linux-generic                                         3.13.0.65.71                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.105                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.105                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.65.71                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.105                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-65-generic                   3.13.0-65.105                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.65.71                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-65.105                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

So I need from time to time do 

sudo apt-get autoremove

to free that space? A bit annoying as for me...

---

### Post by khurtsiya on 2015-10-01
After autoremove (no changes?!):

```
$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.15                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.65.71                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.105                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.105                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.65.71                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.105                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.105                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.65.71                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-65.105                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by flocculant on 2015-10-01
>  After autoremove (no changes?!):

Remove the old ones manually then - either with apt-get or try using synaptic and searching for them in there.

---

### Post by Bashing-om on 2015-10-01
khurtsiya; Morning ...

This indicates the problem:
> 
iU  linux-generic

in dpkg's 2nd output. Now I do not know the why fore of the change in status ..
The first field shows the "status" of the package. 'ii' is desired=installed and the 2nd 'i' is i=installed.
now we have 'iU" where the 1st 'i' is desired=installed and the 'U' is Uninstalled. We must change that status to installed.
Try:
```

sudo apt-get install --reinstall linux-generic

```

Then we see what it will take to remove those old kernels and clean up those marked 'rc' ( (R)emoved but (C)onfig files remain).

[INDENT][INDENT]gotta keep the package manager happy
[/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-01
No luck

> $ sudo apt-get install reinstall linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package reinstall


---

### Post by Bashing-om on 2015-10-01
khurtsiya; Oooppps

Slip of the mind on my part .. Beats me where my mind was.
Correct to be:
```

sudo apt-get install --reinstall linux-generic

```
that is two dashes before the operative "reinstall" .

[INDENT][INDENT]sorry bout that
[/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-01
Now it's ok I guess?

```
$ sudo apt-get install --reinstall linux-generic
[sudo] password for wht: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 0 B/1*786 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 291497 files and directories currently installed.)
Preparing to unpack .../linux-generic_3.13.0.65.71_amd64.deb ...
Unpacking linux-generic (3.13.0.65.71) over (3.13.0.65.71) ...
Setting up linux-generic (3.13.0.65.71) ...
$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.15                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.65.71                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.105                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.105                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.65.71                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.105                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.105                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.65.71                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-65.105                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by Bashing-om on 2015-10-01
khurtsiya; Yeah !

Some better, we still need to get of the older kernels.
Now what results:
```

sudo apt-get autoremove

```
If a failure we do it the manual way, and still pending is the 'rc' marked files.

[INDENT][INDENT]progress made
[INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-01
Output
```
~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

---

### Post by coffeecat on 2015-10-01
@khurtsiya, please use code tags, not quote tags, when posting terminal output. Code tags preserve formatting, which quote tags do not. See your posts #5, #6 and #11 where I've edited them (the first two yesterday!) to replace quote with code tags.

---

### Post by Bashing-om on 2015-10-01
khurtsiya; Hey ;

@ coffeecat; Appreciate that you have our back.

Not as I had anticipated. Let us roll our sleeves up and go to work on this.
Prep:
What release are we working with ? - seeking an explanation why "autoremove" is not effective
```

lsb_release -a
uname -r
hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status

```

And a new look at what kernels are presently installed :
```

dpkg -l | grep linux

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We are going to remove the old kernels manually -
Then: deal with the " 0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded " .
Then: deal with the 'rc' marked packages .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-02
My output:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

$ uname -r
3.13.0-63-generic

$ hwe-support-status --verbose
hwe-support-status: command not found

$ ls -al /usr/bin/hwe-support-status
ls: cannot access /usr/bin/hwe-support-status: No such file or directory

$ dpkg -l | grep linux
ii  libselinux1:amd64                                     2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                      2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                        1.0.1-1                                             amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                  1.0.1-1                                             amd64        Video4linux frame format conversion library
ii  linux-firmware                                        1.127.15                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.65.71                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.105                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.105                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.65.71                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.105                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.105                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.65.71                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-65.105                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  pptp-linux                                            1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                            2.20.1-5.1ubuntu20.7                                amd64        Miscellaneous system utilities
```

---

### Post by dino99 on 2015-10-02
use a friendly tool to manage the packages:
> sudo apt-get install synaptic
> sudo synaptic
on the left pane, select "status" then "installed" and type into "search" field: "linux-image"
this list the installed 'image': purge (right-click the selected package, for complete removal) them all except the two latest released ones
repeat for "linux-headers"

now you should only have the two latest kernels installed (2 headers + 2 images for each kernel) and get back lot of free space ):P

---

### Post by khurtsiya on 2015-10-02
I have other packages with these searches, should I delet all but underlined?

[IMG]http://i.imgur.com/RfQD2kQ.png[/IMG]

[IMG]http://imgur.com/QNJb7Q3.png[/IMG]

---

### Post by Bashing-om on 2015-10-02
khurtsiya; Morning;

Agreed, synaptic will be equally effective to remove the old kernels - images and headers !
Presently you are booting with the -63 kernel .. and you want to keep the latest , -63 and -65 , kernels.
The end goal here is to get you booting that latest -65 kernel.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-03
I'm sorry, my English is not perfect, I did not get what you say in last post. I ask another whay. In the search results there are also packets like this: libsane, alsa-base, linux-generic and so on - should I remove them also, or just that starts with "linux-image" and "linux-headers" (all except -65)?

---

### Post by Bashing-om on 2015-10-03
khurtsiya; 

"I'm sorry, my English is not perfect, " -> my communications skills are not the best, I will try harder.

In a way it is a modified yes:
> 
or just that starts with "linux-image" and "linux-headers" (all except -65)?


You are only going to remove linux-image-XXXX, linux-image-extra-XXX, linux-headers-xxxx, linux-headers-xxx-generic. That is all.
You must keep the kernel version that you are presently booting " 3.13.0-63-generic " that one will become the backup kernel, and as well the latest -65 version . 

Mark all installed kernels that you want to remove, for "complete removal". As you see each kernel version has four components - 2 image and 2 headers- for the installed packages; remove all of them. Press the Apply button in the panel.

Now reboot your computer. The Grub menu should be cleansed.

---------------------
As an aside, this operation would have been clearer and cleaner from the terminal. But that is just my opinion.
-------------------------------
[INDENT][INDENT]'tis linux
[INDENT][INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-04
OK, result is ~560 MB free

[IMG]http://i.imgur.com/R0VvFTH.jpg[/IMG]

[IMG]http://i.imgur.com/3Qbyf2y.jpg[/IMG]

But should I do this manually each time after upgrade?

---

### Post by Bashing-om on 2015-10-04
khurtsiya; Looks good.

As to :
> 
But should I do this manually each time after upgrade?

A bit of background information; The system will not decide for you if you want/need/have-a-use-for old kernels. It is up to how you use and manage your system to tell the system you do not want/need those old kernels. Removing those old kernels is a part of the very light house cleaning that is done in linux. And there is now a command that makes it easy - if the package manager is in a consistent state.
Housecleaning - and all I ever employ -
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get -f install
sudo dpkg -C

```
Where in release 14.04 the command 'autoremove' will also remove old kernels I do assume that you have release 14.04. Release 12.04 does not have this capability and one has to manually remove the old kernels .. either from synaptic or in terminal with 'apt' package management tools .

Have you rebooted the system, and now booting the -65 kernel ?

All good now ?

[INDENT][INDENT]house keeping
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by khurtsiya on 2015-10-04
Yes, I have 14.04

But why in my case autoremove did not work properly? I have this popup with "low space on hdd". So if system does not know what I need to do with old kernels it should at least delete the most old when no space left i guess.

I believe I am on -65:

```
$ uname -r
3.13.0-65-generic

```

THANK YOU!

---

### Post by Bashing-om on 2015-10-04
khurtsiya; Great !

As stated, 'autoremove' should work. At a future time, when the next kernel upgrade is installed and the system has been rebooted and verified booting with the new kernel - run terminal command:
```

sudo apt-get autoremove

```
And if the old kernel is not removed ( will keep the current kernel and a backup kernel ) we need to address that issue.
In that case open a new thread and we will find the reason the package manager does not comply to this standard.

[INDENT][INDENT]it is all good
[/INDENT][/INDENT]

---

