---
title: "Only Unity 2D after update ... bug?"
date: 2013-02-26
forum: Desktop Environments
---

### Post by Future Warthog on 2013-02-26
[NOT SOLVED
I have Ubuntu 12.04 LTS (am going to upgrade when 13.04 comes out, maybe earlier to 12.10...dunno) on a Toshiba Satellite A105 S4284 (I believe) w. Intel Centrino Duo chip.
Anyways, I did a whole bunch of Ubuntu updates yesterday (running Unity 3D plenty fine for all of my previous using as well as regular GNOME) and now I can only start in Unity 2D. I ran the ```
/usr/lib/nux/unity_support_test -p
``` command from the terminal and this is what I got:
```

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

```Unity 3D worked great for my using (11.04 to 12.04 LTS) and it was fine on 12.04 LTS *until* I updated. GNOME 3 also worked fine, but it also will only start in GNOME Classic mode.

I tried logging in as guest, same problem. I created a new account and tried logging that way, ditto.

Any help is accepted,
   ~packpatfan

---

### Post by Future Warthog on 2013-02-26
I ran the 
```

unity --replace

```command in terminal, but it just said "Hello there! Have a whole caboodle of error messages that make almost no sense!" and froze, taking my system with it. I had to Ctrl+C the command and log out, because Unity 2D froze.
I had run *apt-get update*  prior to this, so I thought I would restart my computer, but nothing changed, I had the same problem when I logged back in. 
I would post the output, but restarting the computer erased the info I copied (duh, should have known, since *copy*/*paste* is stored in RAM), so I don't have that. I can run it again, it that will help.

---

### Post by Future Warthog on 2013-02-26
I'm back again, with more info! :)
Here's my graphics card info, from terminal:
```

nate@texno-Satellite-A105:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by Future Warthog on 2013-02-27
Here's some more info...

I, after trying several different fixes (all unsuccessful) from other forums/posts, was trying something else and ran the
```
nate@texno-Satellite-A105:~$ /usr/lib/nux/unity_support_test -p
```
command. When I did, however, I got this: 
```

nate@texno-Satellite-A105:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system

```
:confused:
HELP!
I am affeared I broke my system.

---

### Post by grahammechanical on 2013-02-27
This is the key comment from that very first command

> Unity 3D supported:       no

Whatever you may think, you cannot of been running Unity 3D. This tells me that you are using the Nouveau open source driver and you should be getting a Unity 3D experience using llvmpipe which is used now on 12.10 to replace Ubuntu/Unity 2D.

Are you sure you did not upgrade to 12.10? That would remove Ubuntu 2D and put in llvmpipe. You can try using Additional Drivers to put in a proprietary video driver. But that will not change the fact of 

> Unity 3D supported:       no

Regards.

---

