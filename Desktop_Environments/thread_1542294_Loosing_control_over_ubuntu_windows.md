---
title: "Loosing control over ubuntu windows"
date: 2010-07-30
forum: Desktop Environments
---

### Post by Zhaala on 2010-07-30
Hey everyone.
I've tried everything i've got to solve this. I would really appreciate even just pointing me the way to debbug my problem
Well here it is:
I was running ubuntu 9.10, everything was going just fine. Because of low flash fps problem i was forced to jump back on windows leaving my linux behind. After a while I though i will look up if anything changed with the flash plugin, and there the problem comes. Out of nowhere, since the Ubuntu installation stayed untouched.

If i open more than one window, or a window that uses a lot of memory like firefox, i loose control over it. The mouse highlights the buttons but when i click, nothing happens. I cannot move it nor close it using the mouse. When I Tab it with keyboard everything works fine.


[LIST]
[*]Ive tried reinstalling metacity (ive read somewhere it is responsible for windows managing in ubuntu).
[*]Ive reinstalled ubuntu to version 10.
[/LIST]
Any ideas would help. Thanks in advance!
Cheers, Zhaala

---

### Post by dino99 on 2010-07-30
check driver activation: system admin hardware driver

and you can remove/purge (right click) then reinstall flashplugin-installer (with synaptic)

you might find usefull errors logged into:
- .xsession-errors (/home, ctrl+h to unhide)
- system admin logviewer

---

### Post by Zhaala on 2010-08-01
Hi. Thanks for a quick answer.
Drivers are activated.
Ive checked the .xsession-error file.
I've found out that when i switch windows via ALT-Tab (cant use a mouse to activate a window) this appends to the log
"(gedit:1610): Gdk-CRITICAL **: gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(gedit:1610): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gedit:1610): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed"

I've tried changin to Openbox, but still the windows hangs.
Ive completely uninstall compiz. Still it doesnt work.
Can you help me out more on diagnose?

Cheers Zhaala.

---

