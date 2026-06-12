---
title: "Maple in bash"
date: 2008-08-24
forum: Education &amp; Science
---

### Post by evillan on 2008-08-24
I've installed Maple 12 in /usr/bin/ (as root). I'm able to access the program at /usr/bin/maple12/bin/xmaple in Nautilus so it seems to work.

However, when I type "xmaple" or "maple" in bash, the command is not found. How do I connect Maple so it is accessible from bash?

---

### Post by mali2297 on 2008-08-24
I would have installed it in /opt or /usr/local, but anyhow...

Make symbolic links to the executable files so that they're found in /usr/bin:
```

sudo ln -sv /usr/bin/maple12/bin/*maple /usr/bin/

```

---

### Post by evillan on 2008-08-25
Thanks!

---

### Post by evillan on 2008-08-25
> **mali2297 said:**
> I would have installed it in /opt or /usr/local, but anyhow...



One more thing, how do I know where to install programs? I just installed it the same place as gedit because I happened to use gedit at that time and the program is located at /usr/bin.

---

### Post by mali2297 on 2008-08-25
> **evillan said:**
> One more thing, how do I know where to install programs? I just installed it the same place as gedit because I happened to use gedit at that time and the program is located at /usr/bin.

If you install programs from debian packages (for example, when you use Synaptic) then you don't need to worry about it. The files are usually scattered in several directories; the executable is most often placed in /usr/bin whereas other files are placed in /usr/lib, /usr/share and elsewhere.

When you install programs like maple which isn't available in ubuntu's repositories, it is a good idea to place it in /opt. That way, you know exactly where the files are and can remove them manually if you need. In any case, you need to make symbolic links to the executables (unless the installer makes them for you).

---

### Post by evillan on 2008-08-26
> **mali2297 said:**
> If you install programs from debian packages (for example, when you use Synaptic) then you don't need to worry about it. The files are usually scattered in several directories; the executable is most often placed in /usr/bin whereas other files are placed in /usr/lib, /usr/share and elsewhere.

When you install programs like maple which isn't available in ubuntu's repositories, it is a good idea to place it in /opt. That way, you know exactly where the files are and can remove them manually if you need. In any case, you need to make symbolic links to the executables (unless the installer makes them for you).

Thanks again, I'll keep that in mind the next time I install something.

---

