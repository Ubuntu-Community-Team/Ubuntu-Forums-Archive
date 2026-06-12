---
title: "Unity - the underlying shadow is gone and I can't right-click on the desktop!"
date: 2013-02-03
forum: Desktop Environments
---

### Post by the8thstar on 2013-02-03
Hello all,

I'm having two very specific problems since I installed the Elementary PPA onto my Ubuntu 12.04 install:

1. the border shadow from the menu bar is gone. How can I get it back?
2. I can't right-click on the desktop anymore... weird.

Does anyone know how to get this back?

For the record, I uninstalled pantheon, reinstalled ubuntu-desktop and compiz, to no avail.

Thanks for your help!

---

### Post by kostkon on 2013-02-03
Are you sure that you are still using Unity and not Unity2d? You could logout and make sure that you select Ubuntu as your login session.

Hope that helps.

---

### Post by the8thstar on 2013-02-03
> **kostkon said:**
> Are you sure that you are still using Unity and not Unity2d? You could logout and make sure that you select Ubuntu as your login session.

Hope that helps.

Thanks, I did that but it didn't help. I am indeed running the regular Unity session; I'm afraid Elementary configuration borked my system, but I can't seem to see where and how to fix it. 

Maybe with dconf-editor?

Here is a snapshot of the top of my desktop. The "Ubuntu Desktop" title is gone and so is the shadow.

[IMG]http://i.imgur.com/27n81E5.png[/IMG]

---

### Post by the8thstar on 2013-02-03
I also used: 

> unity --reset
> unity --replace

but the problem remains.

---

### Post by the8thstar on 2013-02-03
I wanted to make sure Unity was indeed supported so I launched:

> the8thstar@Packard-Bell:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

So... I'm still puzzled!

---

### Post by the8thstar on 2013-02-03
I found a solution that fixed the problem, by reinstalling a pure Unity Gnome on Ubuntu.

You can use the same solution here: [http://www.psychocats.net/ubuntu/pureubuntuprecise]("http://www.psychocats.net/ubuntu/pureubuntuprecise")

Thanks Psychocats!

---

