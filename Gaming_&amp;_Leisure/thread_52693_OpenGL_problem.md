---
title: "OpenGL problem"
date: 2005-07-28
forum: Gaming &amp; Leisure
---

### Post by ericsp on 2005-07-28
I installed the nvidia drivers and they work well. However, when I try to ruin Codered, I get the following error:

using /root/.codered/data1/ for writing
using /root/.codered/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
ref_gl::R_Init() - could not load "libGL.so"
recursive shutdown
Error: Couldn't initialize renderer!


++++++++++++++++

Also when I try to compile windstille, I get the message that opengl is not installed. How do I solve this issue? 

thanks
Eric

---

### Post by sonny on 2005-07-28
You have to configure your xorg.conf file wich is located in /etc/X11/xorg.conf

From the Nvidia readme:

If you have a working X config file for a different driver (such as the "nv"
or "vesa" driver), then simply edit the file as follows.

Remove the line:

      Driver "nv"
  (or Driver "vesa")
  (or Driver "fbdev")

and replace it with the line:

    Driver "nvidia"

Remove the following lines:

    Load "dri"
    Load "GLCore"

In the "Module" section of the file, add the line (if it does not already
exist):

    Load "glx"

---

### Post by ericsp on 2005-07-29
I of coarse checked this, but that is all OK. Any other suggestion?

Eric

---

### Post by Kitsune on 2005-07-29
The problem is that in ubuntu the libGL link is nammed libGL.so.1 instead of libGL.so as your game is expecting.
Try this :

codered +set r_gldriver libGL.so.1

This trick works with Wolfenstein and Quake 3...

---

### Post by ericsp on 2005-08-30
Thanks for the help. I still have the same problem. Any other suggestion???

ericsp@Tantalos:~$ coderedaa +set r_gldriver libGL.so.1
using /home/ericsp/.codered/data1/ for writing
using /home/ericsp/.codered/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
ref_gl::R_Init() - could not load "libGL.so"
recursive shutdown
Error: Couldn't initialize renderer!

---

### Post by Bo Rosén on 2005-08-30
Not sure if this works, use at your own risk. ;)
/usrlib/libGL.so is a link that points to libGL.so.1.2 which I don't have on my system. Try this.
```

cd /usr/lib
sudo rm libGL.so
sudo ln -s libGL.so.1 libGL.so

```

Restart X and test.

---

