---
title: "why do compiz effects no work?"
date: 2009-06-18
forum: Desktop Environments
---

### Post by spursncowboys on 2009-06-18
Hi everyone. I, using the Community Documents, installed compiz and compiz fusion plugins. I have CCSM under my system-preference. However, I still cannot get normal or extra visual effects to be applied, under system-preference-appearance. I also cannot get effects for ccsm to work.

```
family@desktop:~$ xdpyinfo | grep -i composite
    Composite
family@desktop:~$ glxinfo | grep -i direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by UbuntuNerd on 2009-06-18
did you try installing any drivers under System > administration > hardware drivers ?

---

### Post by spursncowboys on 2009-06-18
> **UbuntuNerd said:**
> did you try installing any drivers under System > administration > hardware drivers ?
Thank you UbuntuNerd, I went to system-admin-hardware drivers and there was nothing in there. No drivers to choose from. I had just installed nvidia drivers, following ubuntu forum 1125400.

---

### Post by spursncowboys on 2009-06-18
```
family@desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C51G [GeForce 6100] (rev a2)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
family@desktop:~$ 
(gksu:10616): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

```

---

### Post by UbuntuNerd on 2009-06-18
I don't think you have the right drivers?

---

### Post by ~sHyLoCk~ on 2009-06-18
You have "vesa" driver activated instead of "nvidia". You need the[ Nvidia driver]("http://www.nvidia.com/object/linux_display_ia32_185.18.14.html").

---

### Post by spursncowboys on 2009-06-18
so do I have to uninstall these drivers or can I just install the nvidia drivers?

---

### Post by spursncowboys on 2009-06-19
I went to envyng -t and went to install nvidia 180 and it has it that it is already installed. then I went to sys>admin>hardware drivers and it too had the ver. 180 activated.
however when I do ./compiz-check it comes up the same with vesa as my driver.Still when I go to sys>pref>appearance, it will not let me do any effects. 
```
family@desktop:~$ xdpyinfo | grep -i composite
    Composite
family@desktop:~$  glxinfo | grep -i direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
family@desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C51G [GeForce 6100] (rev a2)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
family@desktop:~$ 
(gksu:7512): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

family@desktop:~$ envyng -t

 +----------------------------------------------------------------------------+
 | Number | Candidate Version  | Installed Version | Compatible | Recommended |
 |----------------------------------------------------------------------------|
 | 0      | 180.44-0ubuntu1    | 180.44-0ubuntu1   | +          | +           |
 |----------------------------------------------------------------------------|
 | 1      | 173.14.16-0ubuntu1 | -                 | +          | -           |
 |----------------------------------------------------------------------------|
 | 2      | 96.43.10-0ubuntu1  | -                 | +          | -           |
 |----------------------------------------------------------------------------|
 | 3      | 71.86.08-0ubuntu1  | -                 | -          | -           |
 +----------------------------------------------------------------------------+

```

---

### Post by spursncowboys on 2009-06-19
I stop gdm with ```
sudo /etc/init.d/gdm stop
```
then, using envyng, I uninstalled the 180 and installed it again. Then I restart x, reboot. This is what I got with nvidia xconfig and compiz check.
```
sudo nvidia-xconfig
[sudo] password for family: 

Using X configuration file: "/etc/X11/xorg.conf".

PARSE ERROR: Parse error on line 29 of section Module in file
             /etc/X11/xorg.conf.
             "Disable" is not a valid keyword in this section.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

family@desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C51G [GeForce 6100] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 


```

---

### Post by spursncowboys on 2009-06-20
Ok all I did was redo the entire process of installing the nvidia driver from Ubuntu forum 1125400.```
http://ubuntuforums.org/showthread.php?t=1125400&highlight=180
``` Now I went to sys>preference>appearance and then went to visual effects and it worked.
Thanks for all the help.

---

