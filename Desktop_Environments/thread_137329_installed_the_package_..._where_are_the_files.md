---
title: "installed the package ... where are the files?"
date: 2006-02-27
forum: Desktop Environments
---

### Post by svref on 2006-02-27
I just installed the linux-headers package for my kernel, but I can't figure out where ubuntu stuck the actual headers.  How do I ask APT what files are in a package?

---

### Post by RAOF on 2006-02-27
[QUOTE=svref]I just installed the linux-headers package for my kernel, but I can't figure out where ubuntu stuck the actual headers.  How do I ask APT what files are in a package?[/QUOTE]
You can check out the "Properties" of the package in Synaptic - one of the tabs will be "installed files".

And the linux-headers *should* install to /usr/src/linux-headers-2.yourkernelversion/

---

### Post by taurus on 2006-02-27
It should be in /usr/src

```

ls -la /usr/src

```

---

### Post by 5-HT on 2006-02-27
To list files installed from a package you can either:

1) dpkg -L <package name>

2) Search for the package in synaptic, and you can see where installed files are.


I'm not familiar with kernel headers, but my guess is they may go into /usr/src.

Hope that helps.



*Edit: Whoa, I'm slow again today; more evidence for how great these forums are!

---

### Post by svref on 2006-02-27
Thanks guys.  Now I can use my comic book guy voice (and the technique you taught me) to point out that the headers go in /usr/include/linux NOT /usr/src.

---

### Post by 5-HT on 2006-02-27
[QUOTE=svref]Thanks guys.  Now I can use my comic book guy voice (and the technique you taught me) to point out that the headers go in /usr/include/linux NOT /usr/src.[/QUOTE]

:-# 
My bad, sorry. 
Well the good thing is that you now know how to list the installed files of a package right? :twisted:

---

### Post by az on 2006-02-27
[QUOTE=svref]Thanks guys.  Now I can use my comic book guy voice (and the technique you taught me) to point out that the headers go in /usr/include/linux NOT /usr/src.[/QUOTE]

In debian, they go in /usr/src

The headers package also creates the important symlink at
/lib/modules/'uname -r'/build 
so that you just have to install the linux-headers package and run the source code configure script for the module you need to build and it will find  it.  If your source package is properly built, you don't need to care where the headers actualy are....  It should find them automagically.

---

