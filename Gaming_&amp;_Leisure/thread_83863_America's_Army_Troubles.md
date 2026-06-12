---
title: "America's Army Troubles"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by souled on 2005-10-29
I installed AA 2.5, but it will not start up. I see the splash screen and then it goes to a black flullscreen like it's about to start up, but then it closes. I get this error.
```

Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.

```
I have the ati drivers installed and working. Thanks for any help.

---

### Post by souled on 2005-10-29
Found the solution!
> 
The display driver requires POSIX shared memory to be enabled on the system in order to run these applications correctly. This feature should be enabled by default on most current Linux distributions, but may be disabled intentionally by some system administrators or not included in older distributions.

To enable POSIX shared memory on your system, perform the following as root:

1. Add to following line to /etc/fstab (if it isn't there already):

tmpfs /dev/shm tmpfs defaults 0 0

2. Mount POSIX shared memory as follows:

mount /dev/shm

3. Issue the following command to check that it mounted properly:

mount | grep "shm"

4. If the mount was successful, then the following output (or similar) should appear:

tmpfs on /dev/shm type tmpfs (rw)

At this point, POSIX shared memory is enabled. Your 3D applications should run properly and the error message above should no longer occur.

If the output from this commnd is blank, then the mount failed.

If /dev/shm fails to mount, then this feature may not be turned on in your Linux kernel. In this case we recommend upgrading to a more recent Linux kernel, or contacting your Linux Distribution vendor for more information on enabling this feature.


Did this and now AA works perfectly.

---

### Post by Zillion on 2005-11-01
how does it run compared to windows? is it faster.. and hopefully less buggy? :)

---

### Post by gamesmad on 2005-11-02
It runs like a dream, loading times are 2x quicker, and even with my 32MB (!!!!) graphics card, I can play most maps without to much lag :D

Will

---

### Post by bryan986 on 2005-11-02
Running excellent on my machine, I can have all the settings maxed, but I have a pretty good gfx card too

---

### Post by JurB on 2005-11-02
Runs much smoother than in windows. Most of the games i try do.

---

### Post by hanover.fiste on 2005-11-02
A little thing I found today is to edit ~.armyops250/System/Armyops.ini and change MaxTextureUnits to the actual number of texture units on your card. I got about double my frame rates by doing that. It's under the OpenGLDrv.OpenGLRenderDevice section.

---

### Post by souled on 2005-11-02
[QUOTE=hanover.fiste]A little thing I found today is to edit ~.armyops250/System/Armyops.ini and change MaxTextureUnits to the actual number of texture units on your card. I got about double my frame rates by doing that. It's under the OpenGLDrv.OpenGLRenderDevice section.[/QUOTE]

How can you find the number of texture units your card has? I have a Radeon 9200.

---

### Post by bryan986 on 2005-11-03
[QUOTE=souled]How can you find the number of texture units your card has? I have a Radeon 9200.[/QUOTE]

The radeon 9200 has 4 pipelines and 1 texture unit per pipeline, so it should be 4

---

### Post by souled on 2005-11-03
Thank you sir

---

### Post by infi on 2006-04-18
Hi, im new to linux environment and is there any more concret guide. I mean I don't know how to add lines on that or how to edit any kind of file. Any help is aprecciated, thanks in advance.

---

### Post by madz3391 on 2007-10-22
[FONT="Century Gothic"][SIZE="5"]Hey guys, I have a little problem,
I've just downloaded Americas Army v2.8.2 and when I start installing it, it says: Fail 1: failed to install ISKernel Files
                        Make sure you have the privileges on this machine.
It's not the problem of the download, but the problem of my pc.
I have a windows Vista, so if someone of you can help me, I would be very glad!!! [/SIZE][/FONT]

---

### Post by tango250 on 2007-10-22
Are you sure you can edit the file in the game... Will any errors come up when you do that?

---

### Post by madz3391 on 2007-10-22
What do u mean?
It's fully downloaded and the first screen of installing woth all that extracting stuff, is gone and normally windows installer need to start, but then comes the erorr.
Is it possible that Americas Army doesn't run on Windows Vista?:(

---

