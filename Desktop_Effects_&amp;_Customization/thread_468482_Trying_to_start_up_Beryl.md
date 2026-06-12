---
title: "Trying to start up Beryl"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by Armman on 2007-06-08
Finished installing Beryl and then went to start it in terminal BTW I have a ATI card and already installed the drivers.
:~$ beryl-manager
:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

I just haven't used Ubuntu in a while so I don't remember much. Does it have to do with my xorg.conf? Beause it says composite disabled. I'm not sure...

Thanks in advance.

---

### Post by Armman on 2007-06-08
I"m pretty sure it's nothing complicated...

---

### Post by miggols99 on 2007-06-09
You can't use AIGLX with the fglrx ATI drivers. You will need to use XGL. Look at the following page for some help:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

