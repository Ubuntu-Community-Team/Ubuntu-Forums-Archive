---
title: "CompizFusion on UbuntuStudio 7.10?"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by sturla on 2007-10-21
I've just installed UbuntuStudio, the multimedia version of Ubuntu. Been using it for a while, as of 7.04. Ubuntu 7.10 comes with CompizFusion out of the box, right? But UbuntuStudio does not, it seems. How do I install it in the most proper way?

---

### Post by MetalMusicAddict on 2007-10-21
In a terminal: **sudo apt-get install compiz**

Or use Synaptic to grab compiz.

---

### Post by neels on 2008-01-28
well, I did that, but I can't get window decorations to work, even installing and starting emerald or gtk-window-decorator with the --replace option doesn't work.

 compiz --replace ccp & emerald --replace &

 compiz --replace ccp & gtk-window-decorator --replace

they just don't decorate my windows.

Any help?

---

### Post by fracturedmorals on 2008-01-28
Try this command:
sudo apt-get install compiz compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compizconfig-settings-manager

Then go to:
System > Sessions

And add an entry for compiz

If that doesn't work on startup, then add another entry to your sessions for:

gtk-window-decorator --replace

---

### Post by MiD-AwE on 2008-01-28
I believe that there is currently a bug in emerald. It looks like:

libwnck18 (>= 2.15.90) & emerald (= 0.5.2`git20070925+jbs0)

cannot install currently. If I run compiz, I get:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3200x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 352 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

and then compiz freezes. Nothing after.

---

