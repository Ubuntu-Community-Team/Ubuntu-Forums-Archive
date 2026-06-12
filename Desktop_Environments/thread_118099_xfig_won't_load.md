---
title: "xfig won't load"
date: 2006-01-16
forum: Desktop Environments
---

### Post by hollowhead on 2006-01-16
I downloaded xfig 3.2.5 using synaptic w/o incident.  Imagine my surprise when I try xfig at the terminal and get a 

libXaw3d.so.6 => not found

error.  The athena widget 3d lib is on my machine so I feel the need for a symbolic link but link what to this lib.  Any help would be appreciated I need to use Xfig soon to draw some diagram soon.  Ta.  Hollowhead

---

### Post by schilcha on 2006-01-16
I also installed xfig via synaptic. Runs close to flawlessly (some libraries with these nice images are broken and cause xfig to go down hard).

On my system, I found libXaw3d.so in /usr/lib
```

$ locate libXaw3d.so.6
/usr/lib/libXaw3d.so.6.1
/usr/lib/libXaw3d.so.6

$ ls -l /usr/lib/libXaw3d.so.6
lrwxrwxrwx  1 root root 15 2005-11-07 22:29 /usr/lib/libXaw3d.so.6 -> libXaw3d.so.6.1

$ ls -l /usr/lib/libXaw3d.so.6.1
-rw-r--r--  1 root root 282252 2005-09-12 10:41 /usr/lib/libXaw3d.so.6.1

```

Is your libXaw3d in a non-standard directory (not /lib or /usr/lib)?
Is your libXaw3d world-readable (-**r**w-**r**--**r**--)?

---

### Post by hollowhead on 2006-01-16
I'll check I'm not stting in front my machine, but I think /usr/lib I will check permissions though.  What should I make permissions 664 or 775 if they are root only?

---

### Post by schilcha on 2006-01-16
I'm not familiar to the numeric representation of the permissions -- I'd use 
```

chmod a+r /usr/lib/libXaw3d.so*

```

Also make sure, the symbolic link libXaw3d.so.6 to libXaw3d.so.6.1 is there, since xfig will look for that library (at least the error suggests so).

If they're not in /usr/lib, you can either set the LD_LIBRARY_PATH environment-variable or edit the file /etc/ld.so.conf to add the installation path to the search list. 

BTW, did you install athena widgets via synaptic as well?

Good Luck!

---

### Post by hollowhead on 2006-01-16
Ta.  I will try all this tonight.  I'm more used to the number system although I'm poor on permissions.  Athena lib they seemed to be sitting on the machine pre this app installation.  I have installed stacks of stuff via synaptic so it is possible they came with something else, not sure what though.

---

### Post by hollowhead on 2006-01-16
Tried altering permissions on the library files as above. This is my current status.  

neil@hollobuntu:~$ ls -l /usr/X11R6/lib/libXaw3d.so.*
lrwxrwxrwx  1 root root     15 2005-11-16 20:36 /usr/X11R6/lib/libXaw3d.so.6 -> libXaw3d.so.6.1
-rwxr-xr-x  1 root root 293616 2004-10-26 17:11 /usr/X11R6/lib/libXaw3d.so.6.1

I tried creating a symbolic link thus

sudo ln -s libXaw3d.so.6 libXaw3d.so.6.1 even though my reading of the output above indicates there is one already.

I do not have a /etc/ld.so.conf file. Any suggestions would be appreciated

---

### Post by schilcha on 2006-01-16
Here's my /etc/ld.so.conf:
> 
/usr/lib/atlas


So, in your case, create a file with a single line, containing:
> 
/usr/X11R6/lib


---

### Post by hollowhead on 2006-01-17
schilcha (or anyone) else tried and created /etc/ld.so.conf this doesn't help the same stubben message appears.  Also tried creating a symbolic link thus

sudo ln -s /usr/lib/ /usr/X11R6/lib/

Also makes no difference.

Any advice would be appreciated.

---

### Post by schilcha on 2006-01-18
Two more suggestions -- don't know if they'll help:

In a terminal, try
```

export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/X11R6/lib"
xfig

```

or,
```

sudo ln -s /usr/X11R6/lib/libXaw3d.so.6.1 /usr/lib/libXaw3d.so.6

```

Hope this helps!

---

### Post by hollowhead on 2006-01-18
cheers I copied the lib files concerned to usr/lib and xfig runs but there are now other errors see my recent post.  Hollowhead.

---

### Post by FredSambo on 2006-04-14
[QUOTE=schilcha]Two more suggestions -- don't know if they'll help:

In a terminal, try
```

export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/X11R6/lib"
xfig

```

or,
```

sudo ln -s /usr/X11R6/lib/libXaw3d.so.6.1 /usr/lib/libXaw3d.so.6

```

Hope this helps![/QUOTE]

ya, 

```
sudo ln -s /usr/X11R6/lib/libXaw3d.so.6.1 /usr/lib/libXaw3d.so.6
``` 

worked for me when i was getting the same error running xboard. "ibXaw3d.so.6 => not found"

thanks!

---

