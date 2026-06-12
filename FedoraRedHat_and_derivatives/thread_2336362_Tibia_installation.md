---
title: "Tibia installation"
date: 2016-09-07
forum: Fedora/RedHat and derivatives
---

### Post by pebbles22 on 2016-09-07
Now I tried Tibia. It has a StartTibiaonLegacySystems.sh file that I can't open because the default program is set incorrectly. I use the terminal to open it but I get the message > "./Tibia: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory" I use Fedora 24...

---

### Post by ajgreeny on 2016-09-07
*Thread moved to **Fedora/RedHat and derivatives**.* which is more appropriate for the problem.

---

### Post by pebbles22 on 2016-09-09
Sorry mod.  Edit: Also, does anyone know what application opens a .sh file? I accidentally changed my "Open with" default application.

---

### Post by Dennis N on 2016-09-09
It would be a bash script. So you did the correct thing in using the terminal. The error means you are missing a needed library - **libGL.so.1** - it is provided by the package **mesa-libGL**

---

### Post by pebbles22 on 2016-09-10
Actually the file's already there... ```
$ whereis libGL.so.1 libGL.so: /usr/lib64/libGL.so.1 
```

---

### Post by Dennis N on 2016-09-10
> **pebbles22 said:**
> Actually the file's already there... ```
$ whereis libGL.so.1 libGL.so: /usr/lib64/libGL.so.1 
```

Is Tibia a 32-bit application? If so, it needs the 32-bit version of libGL.so.1
Start yumex, search mesa-libGL, and note there are two - one is 64-bit, one is 32-bit (see the 'Arch.' column). 
32-bit libraries are in /usr/lib
64-bit libraries are in /usr/lib64

---

### Post by pebbles22 on 2016-09-16
It is 32 bit.
Could you tell me how to install the right libGLU, please?

---

