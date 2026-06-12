---
title: "beryl wont run"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by HokeyFry on 2007-09-14
i successfully installed beryl on my machine, i can run the customization app and everything but when i switch to the beryl window manager, i get this error:

```
** (beryl-manager:12026): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

** (xfwm4:12152): WARNING **: The display does not support the XComposite extension.

** (xfwm4:12152): WARNING **: Compositing manager disabled.


```

any ideas? thanks in advance

---

### Post by alpin19 on 2007-09-15
If I good think, you've a some ATI Card ? It's right ?
You have to wait few weeks for new ati drivers which should support 3d acceleration on these cards :)

---

### Post by HokeyFry on 2007-09-15
oh so 3d accelleration is not yet supported? i was under the impression that it was

oh well ill keep tabs on that, thanks

---

### Post by Forlong on 2007-09-15
If you want (or have) to use the fglrx driver, you need to install and set up [Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl").

But if your graphics card is [supported by the open radeon driver](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/radeon.4.html) I recommend removing the fglrx driver -  then you can use Beryl with the regular Ubuntu X-Server (which includes AIGLX)

---

### Post by HokeyFry on 2007-09-19
its not supported, i checked the list and the X1400 isnt in there

ill try installing Xgl

---

