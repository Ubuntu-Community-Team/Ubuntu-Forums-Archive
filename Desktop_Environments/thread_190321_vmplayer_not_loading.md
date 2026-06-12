---
title: "vmplayer not loading"
date: 2006-06-06
forum: Desktop Environments
---

### Post by | MM | on 2006-06-06
I'v just installed vmplayer from the repositories.

I'm getting these errors:

```

matthew@ubuntu:~$ vmplayer
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libgcc_s.so.1/li bgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/li bpng12.so.0: no version information available (required by /usr/lib/libcairo.so. 2)

(vmplayer:6055): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc _s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/re lease/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-pn g.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/lib conf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object  file: No such file or directory

```

I saw gcc 3.4 mentioned so i installed that ... :P, infact this is the error i get post installing gcc3.4, though i have yet to restart after installing gcc3.4.  However, i have rebooted after installing vmplayer.

Iv noticed 'Cairo' in the error.  So perhaps its pertinent to mention that i have XGL and Compiz installed, along with all the relevant dependency releases ... cairo, glitz etc from [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) and [http://xgl.compiz.info/](http://xgl.compiz.info/).

So maybe the new versions of these dependencies are causing vmplayer issues?
Anyone with XGL+compiz have vmplayer going for them?

---

### Post by gatiba on 2006-06-06
I have another Dapper's PC with XGL+Compiz and vmware Workstation installed. Vmplayer is working fine there, but on another Dapper installation (with Xgl+Compiz) i have your same problem, and i installed vmplayer from Synaptic there.

---

### Post by baumer1122 on 2006-06-06
I'm having the exact same problem. Exact same setup.

When I built from source it worked fine with XGL/Compiz. Uninstalling then installing the official debs caused this problem.

---

### Post by baumer1122 on 2006-06-06
Just found a bug report for this: [https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/47792](https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/47792)

This will fix it:
```

$ sudo mv /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1 /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1.old
$ sudo mv /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0 /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0.old
$ sudo ln -s /lib/libgcc_s.so.1 /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1
$ sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0

```

I accidentally marked [47827]("https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/47827") as a duplicate of this bug, which it is not. I can't figure out how to retract marking it as a duplicate though :???:

---

### Post by | MM | on 2006-06-06
Havnt tried it yet.  But thank you :D

EDIT:  Ah wicked it works nicely!

---

