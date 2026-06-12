---
title: "Disabling (certain) Xubuntu keyboard + mouse shortcuts"
date: 2006-10-01
forum: Desktop Environments
---

### Post by lt paul on 2006-10-01
I need some help figuring out how to disable the atl+rmb shortcut for xfwm. It  currently resizes the window but I'm using blender so the key is needed for other important funtions.

---

### Post by kurageart on 2008-06-06
mmm I tried everything i could.
Nothing works.
I even edited some text file, but still nothing...

when I found this page i tough I had found a fix... but still not working for me :
[http://www.xfce.org/documentation/4.2/manuals/xfwm4](http://www.xfce.org/documentation/4.2/manuals/xfwm4)

this part was interesting, and might help someone to get close to the solution...

Hidden options

Some hidden options allow you to customize xfwm4 behaviour. They have to be added by hand to your HOME/.config/xfce4/xfwm4/xfwm4rc file. You may have to create this file.

cycle_minimum=false

    Add this line to your xfwm4rc file if you want apps that do not appear in the taskbar to be included when you switch the focus using the Alt+Tab shortcut.
cycle_hidden=false

    Add this line to your xfwm4rc file if you want to exclude hidden windows from the list presented when using the Alt+Tab shortcut.
easy_click=false

    Add this line to your xfwm4rc file if you want to disable the ability to move and resize windows using the Alt button + mouse click shortcut.
focus_hint=false

    Add this line to your xfwm4rc file to instruct xfwm4 to ignore the focus hint provided by the applications.
prevent_focus_stealing=true

    Add this line to your xfwm4rc file to prevent windows from stealing focus.
raise_with_any_button=false

    Add this line to your xfwm4rc file if you want to raise a window only when clicked with the left mouse button.
move_opacity=100

    Set the window opacity while being moved. Opacity is an integer value between 0 and 100; 100 being opaque, 0 totally invisible.

    That option has no effect if the compositing manager is not enabled.
resize_opacity=100

    Set the window opacity while being resized. Opacity is an integer value between 0 and 100; 100 being opaque, 0 totally invisible.

    That option has no effect if the compositing manager is not enabled.
toggle_workspaces=true

    Add this line to your xfwm4rc file if you want the Control+F(N) keyboard shortcut to remember the previous workspace.
wrap_layout=true

    wrap workspaces depending on the actual desktop layout.
wrap_cycle=true

    wrap workspaces when the first or last workspace is reached.

I'll have to reinstall normal ubuntu , but i'll be happy to switch back to xubuntu...

---

