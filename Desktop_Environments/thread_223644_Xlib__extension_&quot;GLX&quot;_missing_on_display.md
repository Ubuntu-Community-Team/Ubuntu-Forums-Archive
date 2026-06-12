---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2006-07-26
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-07-26
I am trying to get XGL and Compiz woking on a machine with an Nvidia 6600GT. When I run the startup script (followed guide from somewhere around here) I get this output

Xlib:  extension "GLX" missing on display ":0.0".
compiz.real: Root visual is not a GL visual
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

I tried glxinfo | grep rendering and got 

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

GLX is not commented out and definately installed.

Can anyone help me sort this GLX problem out?

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-07-26
Quick update. Restarted GDM. When it tried to start it failed and the log showed this

Module GLX failed to load (no NVIDIA X driver found)

Er why has it suddenly decided this?

Thanks

Ironfistchamp

---

### Post by ufalcon on 2006-10-14
What's the full output from that log?

I've run into a similar problem after updating Edgy AMD64, and I've had to make Xorg the GDM server because Xgl will no long work properly for some reason or another.  I believe part of it is that I'm getting the same "missing glx modules" issue.

---

### Post by ironfistchamp on 2006-10-14
I can no longer post any info on this as that was about three installs ago. I gave up in the end and reinstalled. Sorry.

---

