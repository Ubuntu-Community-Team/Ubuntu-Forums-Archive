---
title: "Basic Compling Question"
date: 2009-06-03
forum: General Help
---

### Post by nowhere@cox.net on 2009-06-03
Hi,

I compiled a package and did make install to install it. It installed itself in /usr/local/bin. When run, it can't find a lib file which is located in /usr/local/lib. I assume it normally should be in /usr/lib.

I made a symbolic link to the "missing" file in /usr/lib and it works but I'm thinking this isn't the "correct way" to do it.

What is?

Thanks!

---

### Post by colau on 2009-06-03
> **nowhere@cox.net said:**
> Hi,

I compiled a package and did make install to install it. It installed itself in /usr/local/bin. When run, it can't find a lib file which is located in /usr/local/lib. I assume it normally should be in /usr/lib.

I made a symbolic link to the "missing" file in /usr/lib and it works but I'm thinking this isn't the "correct way" to do it.

What is?

Thanks!
Symbolic link is supposed to do the job.
May be, it should be in /usr/bin.

---

### Post by Shazaam on 2009-06-03
Did you do...
```
make install
```
or...
```
sudo make install
```
?

---

### Post by nowhere@cox.net on 2009-06-03
```
sudo make install
```

the lib files associated with the package were place in /usr/local/lib. 

I did ```
sudo ln -s /usr/local/lib/libfile.so.1 /usr/lib/libfile.so.1
```
and the program works fine. Is this really the acceptable way to "install" a compiled package? I assume since it wasn't written for ubuntu's structure specifically I have to shoe horn it in?

Thanks!

---

### Post by lloyd_b on 2009-06-03
> **nowhere@cox.net said:**
> ```
sudo make install
```

the lib files associated with the package were place in /usr/local/lib. 

I did ```
sudo ln -s /usr/local/lib/libfile.so.1 /usr/lib/libfile.so.1
```
and the program works fine. Is this really the acceptable way to "install" a compiled package? I assume since it wasn't written for ubuntu's structure specifically I have to shoe horn it in?

Thanks!

If everything is configured correctly on your system, you should NOT have to do this.

First off, look at the file "/etc/ld.so.conf.d/libc.conf", and verify that "/usr/local/lib" is listed in there.  If not, add it.

Then (whether you changed the file or not), run "sudo ldconfig" from a terminal window.  This command will examine all shared libraries in the defined directories, and add them to an index of sorts, so that the shared library loader knows where to find them.

At that point, you should be able to delete your symlink, and have the program run correctly.

(the "ldconfig" operation should ideally be part of the "make install" for the package that built the library.  If it's failing to do the ldconfig, then you should drop a message to the package maintainer about it).

Lloyd B.

---

### Post by nowhere@cox.net on 2009-06-03
```
sudo ldconfig
```

This did the trick!

Thanks, I'll keep it in mind from now on!

---

