---
title: "Running a 32bit app on a 64bit system?"
date: 2009-01-07
forum: General Help
---

### Post by porchrat on 2009-01-07
Hi all.

I've been trying out papyrus UML modeller as an eclipse plugin, but would like to give the standalone a try as well.  Unfortunately it only comes as a x86 version with no x86_64 available.  I am running a 64bit Ubuntu and this is causing a few problems.

I've tried extracting the x86 version and running it, but I get what seem to be the typical error messages:

```
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

```

Am I correct in assuming that this is saying that it can only find the 64bit libraries and therefore is unable to run?

Therefore is there a way to get it to run on a 64bit system?  Perhaps there is a way to give it the 32bit libraries it needs without affecting the rest of my system?

---

### Post by thedarkwinter on 2009-01-07
I'm not sure if this will help or not, but i believe the package ia32-libs has something to do with 32 bit compatibility under 64 bit.

sudo apt-get install ia32-libs

I can't help with your specific problem tho... :(

cheers,
Michael

---

### Post by porchrat on 2009-01-07
> **thedarkwinter said:**
> I'm not sure if this will help or not, but i believe the package ia32-libs has something to do with 32 bit compatibility under 64 bit.

sudo apt-get install ia32-libs

I can't help with your specific problem tho... :(

cheers,
Michael

Thank you for your reply.

That was what I thought too.  I have ia32-libs installed (probably should've mentioned that sorry).  I've noticed that the ati proprietary fglrx drivers (for example) use 32bit libraries provided by the ia32-libs package and I was hoping that papyrus would do the same.  however it looks like it needs to be specifically coded as a 32bit app that will be running on a 64bit system in order to know how to access those ia32-libs libraries.

Well if anyone else has any suggestions I would be most appreciative.

Otherwise I'm going to run it standalone under Vista (aieeeeeee) or just keep it running as an eclipse plugin until a standalone 64bit linux version becomes available.

---

### Post by jespdj on 2009-01-07
It looks like your 32-bit program is trying to load 64-bit libraries, which doesn't work. You'll need the 32-bit versions of those libraries.

Have a look at [getlibs](http://ubuntuforums.org/showthread.php?t=474790), that should be able to automatically find and install the 32-bit libraries that your specific program needs.

---

### Post by porchrat on 2009-01-07
> **jespdj said:**
> It looks like your 32-bit program is trying to load 64-bit libraries, which doesn't work. You'll need the 32-bit versions of those libraries.

Have a look at [getlibs](http://ubuntuforums.org/showthread.php?t=474790), that should be able to automatically find and install the 32-bit libraries that your specific program needs.

That is awesome!  Looks like exactly what I'm looking for.  I will definitely give this a try :D.

---

