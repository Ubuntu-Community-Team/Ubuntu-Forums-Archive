---
title: "VideoWoes..."
date: 2005-07-04
forum: Desktop Environments
---

### Post by uberlinux on 2005-07-04
Jeebus!
I have tried wxVLC, GTK-vlc, gxine, totem-xine, totem gstreamer, xineUI and every time I try to play a video, it displays the first fram and then crashes...  I would have installed MPlayer, but it has deps that I cant sort out...
Heres what it says if I do it in a console:

gxine
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 126 error_code 11 request_code 142 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by uberlinux on 2005-07-05
Bump, somebody has to know what is up...

---

### Post by DarkManX4lf on 2005-07-05
after a fresh install in use totem-xine and i installed the codecs like it says on the starter guide and it works fine for me.

---

### Post by uberlinux on 2005-07-05
[QUOTE=DarkManX4lf]after a fresh install in use totem-xine and i installed the codecs like it says on the starter guide and it works fine for me.[/QUOTE]
I tried totem xine, right after totem-gstreamer, and it didnt work,  this is not a problem of the codecs, I think.  This seems to be more serious as after the first frame, the whole thing dies.

---

### Post by nexus_dublin on 2005-10-19
hey man did you find what the problem is? i've tried everything and i still can't get any video... 
pls help!

---

### Post by scrillamaan on 2005-10-28
Any updates because I'm having the same problem? I think there was a bug filed but I can't remember it exactly. MPlayer works but I don't like the interface and it doesn't make my videos fullscreen. VLC closes as soon as I open a video.

---

### Post by scrillamaan on 2005-10-28
I just installed the nvidia drivers from synaptic and changed all instances of "nv" to "nvidia" in my xorg.conf and the problem went away. YMMV

---

