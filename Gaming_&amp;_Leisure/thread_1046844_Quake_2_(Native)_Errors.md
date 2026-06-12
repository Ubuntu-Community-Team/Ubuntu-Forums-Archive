---
title: "Quake 2 (Native) Errors"
date: 2009-01-21
forum: Gaming &amp; Leisure
---

### Post by aspekt9 on 2009-01-21
I can run quake 2 using +set vid_ref softx. But if I try glx or gl I get the following output:

```
sudo ./quake2 +set vid_ref glx
```

```
Added packfile ./baseq2/pak0.pak (3307 files)
Added packfile ./baseq2/pak1.pak (279 files)
Added packfile ./baseq2/pak2.pak (2 files)
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------- Loading ref_glx.so -------
ref_gl version: GL 0.01
/usr/games/quake2/opengl32: cannot open shared object file: No such file or directory
ref_gl::R_Init() - could not load "opengl32"
------- Loading ref_soft.so -------
LoadLibrary("ref_soft.so") failed: libvga.so.1: cannot open shared object file: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!
```

I'm not sure what I need in order to get glx running. I have LibGL installed.

Also, i have opengl32 in the quake2 directory, but when is type:

ls -l

It shows it as opengl32 > libGL.so

---

### Post by aspekt9 on 2009-01-22
Ok, so I've fixed the errors and the game now runs in both software and opengl mode. However, when ran in open gl, any text and some skyboxes get all garbage and unreadable and artifacty. But everything runs 100% in software mode. Does anyone have any ideas?

---

### Post by rotor_of_the_internet on 2009-01-23
try killing compiz before playing?

---

### Post by ozricus on 2009-12-24
So what did you do?  I have the same issue below and googled to find this but you didn't say what you did.



It could help others in the future that do a google search with the same problem.


> **aspekt9 said:**
> I can run quake 2 using +set vid_ref softx. But if I try glx or gl I get the following output:

```
sudo ./quake2 +set vid_ref glx
``````
Added packfile ./baseq2/pak0.pak (3307 files)
Added packfile ./baseq2/pak1.pak (279 files)
Added packfile ./baseq2/pak2.pak (2 files)
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------- Loading ref_glx.so -------
ref_gl version: GL 0.01
/usr/games/quake2/opengl32: cannot open shared object file: No such file or directory
ref_gl::R_Init() - could not load "opengl32"
------- Loading ref_soft.so -------
LoadLibrary("ref_soft.so") failed: libvga.so.1: cannot open shared object file: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!
```I'm not sure what I need in order to get glx running. I have LibGL installed.

Also, i have opengl32 in the quake2 directory, but when is type:

ls -l

It shows it as opengl32 > libGL.so

---

### Post by vambop on 2010-09-17
Yes, OP, it would be nice if you actually described what you did to fix the initial errors.

---

### Post by ArthurPeale on 2012-03-13
I can tell you what I did to fix this exact issue.  Since this thread kept popping up, over and over again, when I was searching for the solution, I'm sure others are having this issue.

In the baseq2 directory, there is a file, config.cfg, with a  reference to "opengl32".  Comment it out.

I didn't even realize that there was a config file in that directory, I'd been looking for one in my home directory, or in /etc/.  Once I found that, it popped right up.

---

