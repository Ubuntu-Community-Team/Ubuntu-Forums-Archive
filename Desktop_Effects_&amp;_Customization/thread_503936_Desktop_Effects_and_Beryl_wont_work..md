---
title: "Desktop Effects and Beryl wont work."
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by Psyco_Chipmunk on 2007-07-18
When I try to enable Desktop Effects, it says "Desktop effects could not be be enabled"   And whenever I try to switch to Beryl manager. it just switches back to compiz.  I Need to know how to fix these problems!  Thanks!

---

### Post by ThrobbingBrain66 on 2007-07-18
Could you please type 'beryl-manager' into a terminal and paste the output here?

---

### Post by Psyco_Chipmunk on 2007-07-18
luke@luke-laptop:~$ beryl-manager
luke@luke-laptop:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real: Root visual is not a GL visual
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"



  There you go.   :)

---

### Post by Psyco_Chipmunk on 2007-07-18
u there?

---

### Post by ThrobbingBrain66 on 2007-07-18
Yes, sorry.

I should have asked in my last post what kind of video card you have. ATI, NVIDIA, Intel, etc.

[http://doc.gwos.org/index.php/BerylOnEdgy#ATI](http://doc.gwos.org/index.php/BerylOnEdgy#ATI)
The above link will give you directions for the three card types above.  If you still have questions, post back.

---

