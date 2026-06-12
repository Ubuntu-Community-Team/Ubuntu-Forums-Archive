---
title: "Unity compiz problem"
date: 2013-01-28
forum: Desktop Environments
---

### Post by joldy on 2013-01-28
Hello all,

I'm having problems with my desktop, as in nothing  appears after login apart from the background image. These problems  started when I was upgrading to 12.10 and my computer crashed halfway  through, so I initially used a terminal to complete the installation,  but after I restarted there are still no sidebars. 

From  searching similar problems, I tried unity --reset, although that now  appears to be a deprecated option. Compiz has crashed a few times so I  suspect that it's something to do with the problem. I also tried unity --reset-icons just in case, and the output I got is at the end in case it helps. 

There's a  dark grey bar that appears on the login screen, but once I've logged in  this disappears. The same happens if I login using a guest account.

Any help would be greatly appreciated!
```

------

unity --reset-icons
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: wall
compiz (core) - Error: Failed to start plugin: wall
compiz (core) - Info: Unloading plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: animation
compiz (core) - Error: Failed to start plugin: animation
compiz (core) - Info: Unloading plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: fade
compiz (core) - Error: Failed to start plugin: fade
compiz (core) - Info: Unloading plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unitymtgrabhandles
compiz (core) - Error: Failed to start plugin: unitymtgrabhandles
compiz (core) - Info: Unloading plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: scale
compiz (core) - Error: Failed to start plugin: scale
compiz (core) - Info: Unloading plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: expo
compiz (core) - Error: Failed to start plugin: expo
compiz (core) - Info: Unloading plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: ezoom
compiz (core) - Error: Failed to start plugin: ezoom
compiz (core) - Info: Unloading plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

(process:3511): GLib-GIO-WARNING **: g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range

(process:3511): GLib-GIO-WARNING **: g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range

(process:3511): GLib-GIO-WARNING **: g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range

(process:3511): GLib-GIO-WARNING **: g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
```

---

### Post by stinkeye on 2013-01-28
Where you using proprietary gfx drivers when you upgraded?

In Quantal use:
reset compiz/unity to default....
```
dconf reset -f /org/compiz/
```

Reload unity...
```
setsid unity
```

---

### Post by joldy on 2013-01-28
> **stinkeye said:**
> Where you using proprietary gfx drivers when you upgraded?

Good question, I'm not sure. Is there a way to find out? My graphics adapter is an ATI Mobility Radeon HD 4670. 

> **stinkeye said:**
> In Quantal use:
reset compiz/unity to default....
```
dconf reset -f /org/compiz/
```Reload unity...
```
setsid unity
```

Doing this unfortunately gives exactly the same error messages as in the first post.

---

### Post by superglide03 on 2013-01-28
I had the same problem yesterday.  Background but no top panel or launcher.  I had to restart my display manager.  

sudo service lightdm restart

This brought me out to a tty1 terminal.  After logging on (username first) I entered the same code.

sudo service lightdm restart

Now I was brought to a regular login screen and once logged in I had everything back.  

Hope this helps.

---

### Post by joldy on 2013-01-29
Thanks for the advice, unfortunately I returned to same blank screen after trying that. :(

---

### Post by stinkeye on 2013-01-29
Were you using unity/compiz or unity 2d before upgrading.
The error says **Unity is not supported by your hardware**.
There is no 2d session in 12.10.

What is the output of...
```
lspci -nnk | grep -iA2 vga
```

In the mean time you could try to get to a functioning desktop by ctrl+alt+f1.
Login and run...
```
sudo apt-get install gnome-panel
```
When the installation has finished enter...
```
sudo reboot
```

This will give you a Gnome-Classic(no effects) session you can choose at the login screen.

---

