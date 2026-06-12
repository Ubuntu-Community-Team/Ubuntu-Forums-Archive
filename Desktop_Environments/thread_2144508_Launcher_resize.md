---
title: "Launcher resize"
date: 2013-05-12
forum: Desktop Environments
---

### Post by duncantickner on 2013-05-12
Have just upgraded to 12.04. the Ubuntu documentation says I can resize the launcher icons via settings- appearance and move slider, but I have no slider. Please help

---

### Post by Frogs Hair on 2013-05-12
Check in the behavior tab .

---

### Post by Bashing-om on 2013-05-12
duncantickner; 
Also be aware in order to have that function one must have 3d enabled (login icon)then:
Launcher ->System Settings ->appearance ->slider at bottom of screen.
[INDENT=2]
hope this helps

[/INDENT]

---

### Post by duncantickner on 2013-05-13
Thanks for your reply, 
I may be stupid but I can't find an option for 3d effects or a login icon.

---

### Post by deadflowr on 2013-05-13
When you login, the box where yor name and password go is a small icon in the right corner.
It should be an icon of the Ubuntu logo, click on it and a dropdown should open with at least two options, Ubuntu and Ubuntu 2d.
Click on Ubuntu and proceed to login.

There is a chance you can't run full Unity, which means the login will drop to the Ubuntu 2d setting.

run

```
/usr/lib/nux/unity_support_test -p
```
If any of the settings are marked no then you can't run unity.

You could then post the output for
```
lspci | grep VGA
```

This way we can get a basic idea if your gpu is unity capable.

---

### Post by duncantickner on 2013-05-14
Thanks for your help, I am stupid I had it on auto login:confused:
Have run your shell commands and my setup does not support 3d unity.
here are the results:-
duncan@duncan-laptop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
duncan@duncan-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
duncan@duncan-laptop:~$

---

### Post by epikvision on 2013-05-14
> **duncantickner said:**
> Thanks for your help, I am stupid I had it on auto login:confused:
Have run your shell commands and my setup does not support 3d unity.
here are the results:-
duncan@duncan-laptop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

** Unity 3D supported:       no**
duncan@duncan-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
duncan@duncan-laptop:~$

Guess you can't run unity 3d...  However, there is a [workaround for resizing in Unity 2D]("http://www.dedoimedo.com/computers/ubuntu-unity-2d-resize-launcher.html"). Hope it helps!

---

### Post by deadflowr on 2013-05-14
I've used this one, works well in 12.04.

[http://ubuntuforums.org/showthread.php?t=1954637](http://ubuntuforums.org/showthread.php?t=1954637)

---

### Post by duncantickner on 2013-05-15
That's me sorted. Many thanks to all who helped

---

