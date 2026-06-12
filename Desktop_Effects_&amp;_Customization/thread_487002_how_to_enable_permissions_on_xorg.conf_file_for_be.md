---
title: "how to enable permissions on xorg.conf file? for beryl"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by tribeca26 on 2007-06-28
When I add the line: Option "AddARGBGLXVisuals" "True"  to get it so that the top bar shows up on my windows and i close out and tell it to save it tells me: "could not save... you do not have permissions necessary to save the file. The file is read only when i go under permissions and tells me that it is not my file... I am an administrator on the computer, how do I get it so that it will allow me to add the value to it?:(

---

### Post by Metacarpal on 2007-06-28
Open it from the command line with "sudo" in front of the command.

---

### Post by throwingks on 2007-06-28
If you are in Gnome.
> sudo gedit /etc/X11/xorg.conf

---

