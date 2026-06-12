---
title: "no menu bar in beryl"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by Donhu on 2007-04-08
i have no menu bar in beryl and would love for someone to help me fix this prob

---

### Post by siciliancasanova on 2007-04-08
You mean that your panel is missing?

Here is the [Beryl Troubleshooting Guide]("http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl")

---

### Post by Hieronymus on 2007-04-08
Just put this in your startxgl.sh script instead of what you have now and all should work.

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```Jeroen

PS. This and more info you can find [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")

---

### Post by Donhu on 2007-04-08
how do i get to that file? when i pico bin/sh, i get a bunch of unrecognizable characters

---

### Post by siciliancasanova on 2007-04-08
see below \/

---

### Post by ajmorris on 2007-04-08
> **Donhu said:**
> how do i get to that file? when i pico bin/sh, i get a bunch of unrecognizable characters

That goes here : /usr/local/bin/startxgl.sh
But that is only if you are using xgl, are you using xgl or aiglx?

---

### Post by Donhu on 2007-04-08
wen i open it, i get a bunch of unrecognizable charac's. should i jus type it at the bottom or something?

---

### Post by Donhu on 2007-04-08
i think it is aiglx

---

### Post by ajmorris on 2007-04-08
> **Donhu said:**
> i think it is aiglx

What version of ubuntu are you using?

and can you please start beryl through and command line for us? go to gnome-terminal and type "beryl-manager" then can you paste the results that it shows?

ALso what version of beryl? ("beryl --version" in a command line) and where did you download it from?

---

### Post by Donhu on 2007-04-08
im using the 6.10, and the output is:

donhu@a-c33:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x5b
Reloading options

---

### Post by Donhu on 2007-04-08
wat is the command to stop running beryl please?

---

### Post by ajmorris on 2007-04-08
and you installed it through this guide ? : [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

also what beryl version?

---

### Post by ajmorris on 2007-04-08
> **Donhu said:**
> wat is the command to stop running beryl please?

Right Click the diamond in the system tray and select your normal windows manager, or in the command line sudo killall beryl. Also just to clarify, is your startmenu and taskbar (panel) missing or your window title bars?

---

### Post by ajmorris on 2007-04-08
> **Donhu said:**
> im using the 6.10, and the output is:

donhu@a-c33:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x5b
Reloading options

is that all? no vtable plugin errors?

---

### Post by ajmorris on 2007-04-08
also what graphics card? that error : libGL warning: 3D driver claims to not support visual 0x5b is usually caused by not having drivers/having outdated drivers for your graphics card installed.

---

