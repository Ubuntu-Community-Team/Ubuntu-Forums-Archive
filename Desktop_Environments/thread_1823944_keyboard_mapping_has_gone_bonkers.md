---
title: "keyboard mapping has gone bonkers"
date: 2011-08-12
forum: Desktop Environments
---

### Post by lobo2me on 2011-08-12
Basic info:
> ubuntu 10.10
kernel Linux 2.6.35-30-generic-pae
gnome version 2.32.0 (2010-09-27)
xinput version 1.5.2
XI version on server: 2.0
Fujitsu Siemens 105-key keyboard using "Evdev handled" Swedish layout


So I was fiddling around with xsetwacom to set the buttons on the pad to something useful when suddenly the "less" key on my keyboard, instead of returning the character I am unable to write right now, started to generate an event that sent the active window to the bottom of the stack (and quite possibly, some invisible atrocities as well).

As a side note, the keyboard does not match the keyboard layout as displayed by the keyboard setting utility - the "less" key, #94,is not visible in the keyboard map at all, even though it works OK. Or did.

As far as I know, all actual config commands were entered through a script and not directly from the terminal.

> ## configure pad buttons
##xsetwacom set "Wacom Bamboo Comic 2FG Finger pad" Button 1 "key less"
##xsetwacom set "Wacom Bamboo Comic 2FG Finger pad" Button 2 "key greater"
##xsetwacom set "Wacom Bamboo Comic 2FG Finger pad" Button 3 "key ctrl y"
xsetwacom set "Wacom Bamboo Comic 2FG Finger pad" Button 8 "key ctrl z"

The culprit seems to be the line (now commented out) where Button 1 is configured - I might have, at some time, written "key shift less" or something similar, but that is all I can think of that may have messed things up (somehow, that feels unlikely, but stranger things have happened).

Anyway, after a few tries, the end result was that all the pad keys worked fine, however, as the event generated when pressing Button 1 was the same as when pressing "less" on the keyboard, and that had changed into what I described above, I was not overly cheerful despite my success.

Tracking down the events, the "less" key obviously generated:
> KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


The same key, with "shift" looked more like I would expect:
> KeyPress event, serial 33, synthetic NO, window 0x4800001,
    root 0x15a, subw 0x4800002, time 2561525, (41,40), root:(1724,204),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x4800001,
    root 0x15a, subw 0x4800002, time 2562669, (41,40), root:(1724,204),
    state 0x11, keycode 94 (keysym 0x3e, greater), same_screen YES,
    XLookupString gives 1 bytes: (3e) ">"
    XmbLookupString gives 1 bytes: (3e) ">"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4800001,
    root 0x15a, subw 0x4800002, time 2562759, (41,40), root:(1724,204),
    state 0x11, keycode 94 (keysym 0x3e, greater), same_screen YES,
    XLookupString gives 1 bytes: (3e) ">"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4800001,
    root 0x15a, subw 0x4800002, time 2565554, (41,40), root:(1724,204),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
(smileys courtesy of this forum's software, replace them with "colon" + "left parenthesis")

I found this in the /var/log/gdm/:0-greeter.log file (with matching time stamp):
> ** (process:1550): DEBUG: Greeter session pid=1550 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-0INUpE/database

(gnome-power-manager:1551): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
gdm-simple-greeter[1550]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Fönsterhanterarvarning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000034 (Inloggning)
Fönsterhanterarvarning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Fönsterhanterarvarning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000034 (Inloggning)
Fönsterhanterarvarning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Fönsterhanterarvarning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000034 (Inloggning)
Fönsterhanterarvarning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gnome-power-manager:1551): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-power-manager:1551): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
Fönsterhanterarvarning: CurrentTime used to choose focus window; focus window may not be correct.
Fönsterhanterarvarning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

("Fönsterhanterarvarning" is Swedish for Window Manager Warning, I guess. "Inloggning" means "login".)

Now, I don't know enough to decipher this, but the statement that "this shouldn't happen!" probably indicates that things are not well.

There was a pager running (I managed to drop a man page into the background - it has been ages since I was fluent in writing commands that look like line noise), if that could have been a source of trouble.

I do have a track record of running into things that shouldn't happen, and I am certainly curious as to what it could be, but most of all I would like my "less" key back.

So if someone is able to explain this, that will be fine, but I can settle for a tip on how to simply reset the keyboard.

Thanks!

---

### Post by lobo2me on 2011-08-17
Eventually, I discovered a utility, "keyboard shortcuts", and sure enough, the "<" key was enabled to send the active window to the bottom layer.

Disabling it, the problem was fixed.

What beats me is how I managed to set that shortcut. I have never used that tool before, but I guess that there is a line command that can do that, too. xinput, maybe?

---

