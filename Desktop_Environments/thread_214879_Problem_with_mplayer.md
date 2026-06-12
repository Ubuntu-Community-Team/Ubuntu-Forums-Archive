---
title: "Problem with mplayer"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-13
When I try to start mplayer it doesn't happen anything, if I try through the console it displays this warning:

> mplayer: error while loading shared libraries: libGL.so.1

What can I do?

---

### Post by taurus on 2006-07-13
How did you install mplayer and use synaptic to search for libGL then?

---

### Post by philippe_carlo on 2006-07-13
Can you try

```

sudo apt-get --reinstall install xlibmesa-gl

```

---

### Post by Dearhell on 2006-07-13
> **philippe_carlo said:**
> Can you try

```

sudo apt-get --reinstall install xlibmesa-gl

```

It says that package it's not found

I have installed mplayer with aptitude install mplayer

It was all fine till yesterday.

I have tried aptitude purge mplayer and aptitude install mplayer but it appears the same error.

---

### Post by philippe_carlo on 2006-07-13
Sorry,

try this instead 

```
sudo apt-get --reinstall libgl1-mesa libglu1-mesa
```


[I]The above is wrong --reinstall does not exist as an option
You have to remove the libgl1-mesa-dev package
and then reinstall it again[/I]

---

### Post by Dearhell on 2006-07-13
It displays:

> E: Invalid operation: libgl1-mesa

---

### Post by philippe_carlo on 2006-07-13
Can you give the output of 
```
ls -al /usr/lib/libGL.so*
```

---

### Post by Dearhell on 2006-07-13
It displays this:

> ls: /usr/lib/libGL.so*: it doesn't exist file or folder

---

### Post by philippe_carlo on 2006-07-13
So, about the packages:
(1) open Synaptic
(2) Search for "mesa"
(3) Mark the following package for reinstallation:
      libgl1-mesa-dev

---

### Post by Dearhell on 2006-07-13
I have installed that package as you said, but I still have the same problem:

> mplayer: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


ls -al /usr/lib/libGL.so*, now displays this:

> lrwxrwxrwx 1 root root 10 2006-07-13 15:52 /usr/lib/libGL.so -> libGL.so.1


---

### Post by philippe_carlo on 2006-07-13
Ok, seems like you will have to do the same for the 

libgl-mesa 
libgl1-mesa-glide3 

packages (mark for reinstallation). Seems like some dependencies got screwed up along the line. 

ls -al /usr/lib/libGL.so* should display:
lrwxrwxrwx 1 root root   10 2006-06-28 08:57 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root   12 2006-06-03 09:36 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 398K 2006-05-05 17:05 /usr/lib/libGL.so.1.2

---

### Post by Dearhell on 2006-07-13
> **philippe_carlo said:**
> Ok, seems like you will have to do the same for the 

libgl-mesa 
libgl1-mesa-glide3 

packages (mark for reinstallation). Seems like some dependencies got screwed up along the line. 

ls -al /usr/lib/libGL.so* should display:
lrwxrwxrwx 1 root root   10 2006-06-28 08:57 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root   12 2006-06-03 09:36 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 398K 2006-05-05 17:05 /usr/lib/libGL.so.1.2

If I select libgl1-mesa-glide3, sypnatic says that it will uninstall libgl1-mesa, libgl1-mesa-dev, libgl1-mesa-dri, ubuntu-desktop, x-window-system-core, and that will install libglide3

Beside that, it doesn't appear libgl-mesa, it appears libgl1-mesa

---

### Post by philippe_carlo on 2006-07-13
I suspect that what happened is the following:
You installed the NVIDIA or ATI drivers for X and removed them again later on. Typically this cripples your install because it removes the NVIDIA/ATI specifig version of the aforementioned libraries and did not reinstall the generic mesa-ones.

So reinstalling mesa is the way to fix this. For this, you have to reinstall the above packages and yes, I meant libgl1-mesa of course. Reinstallation should not harm you, it will just REinstall (not remove) the packages and their dependencies.

---

### Post by Dearhell on 2006-07-13
I will try to reinstall ati drivers then, I can't reinstall mesa because it freezes the computer when the screensaver appears.

---

