---
title: "installing f-spot 0.0.9"
date: 2005-02-22
forum: Desktop Environments
---

### Post by doni on 2005-02-22
hi there...

I would like to install the newest f-spot.

During ./configure I've got the following error, which I can't eliminate:

```
checking for libgphoto2 >= 2.1.4... Package libgphoto2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgphoto2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgphoto2' found

configure: error: Library requirements (libgphoto2 >= 2.1.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
``` 

"locate libgphoto2.pc" doesn't return anything, but i've got libgphoto2-2 installed via apt. 

what could be the problem?

thanks
doni

---

### Post by kassetra on 2005-02-22
[QUOTE=doni]hi there...

I would like to install the newest f-spot.

During ./configure I've got the following error, which I can't eliminate:

```
checking for libgphoto2 >= 2.1.4... Package libgphoto2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgphoto2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgphoto2' found

configure: error: Library requirements (libgphoto2 >= 2.1.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
``` 

"locate libgphoto2.pc" doesn't return anything, but i've got libgphoto2-2 installed via apt. 

what could be the problem?

thanks
doni[/QUOTE]

in order to install files from source, you need the -dev files... so in this case, you need libgphoto2-dev  :)

---

### Post by crun on 2005-02-22
*If* you're running Hoary then you can get it from the Universe repos:

```
sudo apt-get install f-spot
```

---

### Post by macewan on 2005-02-22
/usr/lib/pkgconfig/libgphoto2.pc

---

### Post by GeneticFreek on 2005-02-23
[QUOTE=crun]*If* you're running Hoary then you can get it from the Universe repos:

```
sudo apt-get install f-spot
```[/QUOTE]

I am running Hoary and I used Synaptic to install f-spot, but when I run it I get the following:

```
Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Gnome.Vfs.Vfs ---> System.DllNotFoundException: gnomevfs-2
in <0x00053> (wrapper managed-to-native) Gnome.Vfs.Vfs:gnome_vfs_initialized ()
in [0x00000] (at /build/buildd/f-spot-0.0.9/src/gnomevfs/Vfs.cs:43) Gnome.Vfs.Vfs:.cctor ()
--- End of inner exception stack trace ---

in (unmanaged) Driver:Main (string[])
in [0x00021] (at /build/buildd/f-spot-0.0.9/src/main.cs:13) Driver:Main (string[])

```

What do I need to do for this Gnome.Vfs.Vfs?

---

### Post by crun on 2005-02-23
I'm afraid I can't help you with that error. Have you tried running it as root?

---

### Post by GeneticFreek on 2005-02-23
[QUOTE=crun]I'm afraid I can't help you with that error. Have you tried running it as root?[/QUOTE]

 I get the same error with "sudo f-spot"

---

### Post by blixtra on 2005-02-24
This seems to be fixed now. Just update F-stop. Worked for me.

Chris

---

