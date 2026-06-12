---
title: "Compiz and Separate X Screens"
date: 2016-08-26
forum: Desktop Environments
---

### Post by neelix57 on 2016-08-26
Hello,

I'm under Xubuntu 16.04lts x64. Video Card NVIDIA Geforce GTX 550 Ti.

I installed the MATE environment and compiz. I configured two X Screens.

The desktop appears only on the first X screen. The second remain black with a panel and a black cross instead of the mouse cursor. No right click on desktop, but I can right click on panel and add elements on it.

I tried the command:
```
compiz --replace --display :0.1
```

Here is the output:
```
neelix@cochrane:~$ compiz --replace --display :0.1 &
[1] 4874
neelix@cochrane:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : false
compizconfig - Info: Profile     : mate
compiz (core) - Info: Loading plugin: crashhandler
compiz (core) - Info: Starting plugin: crashhandler
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
compiz (core) - Info: Loading plugin: workspacenames
compiz (core) - Info: Starting plugin: workspacenames
compiz (core) - Error: Plugin 'text' not loaded.

compiz (workspacenames) - Warn: No compatible text plugin loaded
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: matecompat
compiz (core) - Info: Starting plugin: matecompat
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: neg
compiz (core) - Info: Starting plugin: neg
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: showmouse
compiz (core) - Info: Starting plugin: showmouse
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: thumbnail
compiz (core) - Info: Starting plugin: thumbnail
compiz (core) - Error: Plugin 'text' not loaded.

compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: switcher
compiz (core) - Info: Starting plugin: switcher
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

neelix@cochrane:~$ 
(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_display_get_screen: assertion 'screen_num == 0' failed

(gtk-window-decorator:4879): Gdk-CRITICAL **: gdk_x11_screen_supports_net_wm_hint: assertion 'GDK_IS_SCREEN (screen)' failed


```

Could someone help me please ?

---

