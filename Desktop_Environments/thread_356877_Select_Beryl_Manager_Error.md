---
title: "Select Beryl Manager Error"
date: 2007-02-08
forum: Desktop Environments
---

### Post by nomad00 on 2007-02-08
I just finished installing Beryl via the guide at [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL")
and everything went fine up to attempting to select Beryl from the diamond menu.  I get the following output:
[INDENT]
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed

** (beryl-manager:5794): WARNING **: Beryl caught deadly signal 11
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_maximized"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_2"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_4"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_6"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_8"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_11"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_left"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_right"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_up"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_down"
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize_vertically"
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize_horizontally"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_3"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_7"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_8"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_10"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_11"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_left"[/INDENT]

I am brand new to Ubuntu, XGL & Beryl, so i apologize if this is a simple issue, but-- any ideas?

---

### Post by nomad00 on 2007-02-08
I just noticed that while fglrxinfo looks good:

[INDENT]fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)
[/INDENT]

glxinfo does not:

[INDENT]glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
[/INDENT]

Not sure if that has something to do with it, but figured I'd include it.

---

