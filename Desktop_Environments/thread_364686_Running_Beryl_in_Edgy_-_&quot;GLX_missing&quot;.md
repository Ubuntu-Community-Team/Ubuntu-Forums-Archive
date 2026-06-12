---
title: "Running Beryl in Edgy - &quot;GLX missing&quot;"
date: 2007-02-18
forum: Desktop Environments
---

### Post by lolwhites on 2007-02-18
I've just installed Beryl as per the instructions here:
[[COLOR="Blue"]Install Beryl on Ubuntu Edgy with Nvidia[/COLOR]]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation")

When I tried to run it I got this:

[PHP]**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
[/PHP]

Any idea what the problem is?

---

### Post by lolwhites on 2007-02-19
Am now able to run Beryl now I've installed the right drivers for my graphics card. However, when I select Beryl as the window manager, the borders around the windows disappear and I can't move them around. Any advice?

---

### Post by moma on 2007-02-19
Start beryl-manager from the icon on the system tray (normally in the upper right corner of the screen) or start it from the [CLI]("http://en.wikipedia.org/wiki/Command_line_interface"):
$ [COLOR="SeaGreen"]beryl-manager[/COLOR]

Then right-click the Beryl emerald icon and select "Reload window decorator"

Are you running Beryl 0.2.0?
[http://lunapark6.com/?p=2916](http://lunapark6.com/?p=2916)   :: Look at the bottom of the article
---------------------------------------------------------------------

ps. Perfict NVIDIA driver installment with guarantee
[http://www.ubuntuforums.org/showthread.php?p=1997908#post1997908](http://www.ubuntuforums.org/showthread.php?p=1997908#post1997908)

---

### Post by lolwhites on 2007-02-19
Have followed your instructions but the problem persists, and no 3D as far as I can tell. I do get nice little preview panes when I hover over the minimised windows though.

To be honest I'm not sure what version it is; whichever one you get by following the instructions I linked to, I suppose. The themer says 0.1.9999.2.

---

### Post by lolwhites on 2007-02-19
Have removed and reinstalled both xgl and Beryl as per the instructions [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_the_Beryl_Project_repositories") but still no joy. What's more, the command line appears as a blank box and I can't type anything into it.

If I type $ beryl into terminal I get this :
[PHP]
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
[/PHP]

---

### Post by lolwhites on 2007-02-20
Followed w1ndow's advice [here]("http://ubuntuforums.org/showthread.php?t=358962&highlight=No+GLXFBConfig+for+depth+32") and it works a dream! Who needs Vista?

---

