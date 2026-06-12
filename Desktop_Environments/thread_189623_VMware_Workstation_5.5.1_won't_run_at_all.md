---
title: "VMware Workstation 5.5.1 won't run at all"
date: 2006-06-05
forum: Desktop Environments
---

### Post by pksings on 2006-06-05
New fresh install of 6.06. Tar.gz version of VMware.

Installs just fine, no problems whatsoever. Fails to run, the following is what it puts up..

pkelly@dell-pk:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized
vmware: pthread_mutex_lock.c:108: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/libbonobo-activation.so.4: undefined symbol: g_get_language_names
pkelly@dell-pk:~$

---

### Post by cbudden on 2006-06-05
I am getting the same error but with more!
```

cbudden@Ubuntu:~$ vmplayer
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:16449): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

```

---

### Post by codypumper on 2006-06-05
What do you have for hardware?

---

### Post by singularity on 2006-08-04
> **pksings said:**
> New fresh install of 6.06. Tar.gz version of VMware.

Installs just fine, no problems whatsoever. Fails to run, the following is what it puts up..

pkelly@dell-pk:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized
vmware: pthread_mutex_lock.c:108: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/libbonobo-activation.so.4: undefined symbol: g_get_language_names
pkelly@dell-pk:~$

I had the same problem.

I found that if I started VMware in an ssh session with X tunneling it ran with no problem. Try *ssh -X localhost vmware*

This lead me to think there must be an environment variable breaking things. I took a diff of both sets of environment variables and discovered that by unsetting the GTK_MODULES variable VMware was able to start without having to be tunneled.

Hence, in a console try
[INDENT]$ unset GTK_MODULES
$ vmware[/INDENT]

---

### Post by Atomic Dog on 2006-08-28
> **singularity said:**
> I had the same problem.

I found that if I started VMware in an ssh session with X tunneling it ran with no problem. Try *ssh -X localhost vmware*

This lead me to think there must be an environment variable breaking things. I took a diff of both sets of environment variables and discovered that by unsetting the GTK_MODULES variable VMware was able to start without having to be tunneled.

Hence, in a console try
[INDENT]$ unset GTK_MODULES
$ vmware[/INDENT]

Unsetting GTK_MODULES did the trick.  I have no idea what unset does, or what side effects it will have....but it worked!  Thanks.

---

### Post by jundalabee on 2006-08-28
Have you installed evrything you need such as GCC and services?

I remember I had similar errors when I installed it and I developed my own how to. I devolped the how to for workstation but it worked on Vmware server too.

Check my help doc. to see if you missed anything.

[http://ubuntuhelp.homelinux.org/vmware.html](http://ubuntuhelp.homelinux.org/vmware.html)

---

### Post by Atomic Dog on 2006-08-28
> **jundalabee said:**
> Have you installed evrything you need such as GCC and services?

I remember I had similar errors when I installed it and I developed my own how to. I devolped the how to for workstation but it worked on Vmware server too.

Check my help doc. to see if you missed anything.

[http://ubuntuhelp.homelinux.org/vmware.html](http://ubuntuhelp.homelinux.org/vmware.html)

Nice little write-up.  Short and sweet.  Yes, install is about the same for workstation.

My situation made no sense to me.  I had workstation running for a couple months.  One day I was running VM's...and the next, workstation in my case, would not start.  No updates or installs between the previous afternoon and next morning.  I tried reinstalling, complete removal & reinstall...nothing worked...except that "unset GTK_MODULES"

I followed this post up in case somebody else runs into a vmware workstation issue where it won't start.  In my case I was desperate to get it running and this thread saved my butt!

---

