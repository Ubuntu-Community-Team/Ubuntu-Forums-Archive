---
title: "Where Are My Desktop Top &amp; Bottom Bars?"
date: 2009-03-31
forum: Desktop Environments
---

### Post by DavidDee on 2009-03-31
All of a sudden My desktop shows only the background and the icons representing the items in the Desktop directory. No main menu, no clock, workplace switcher... 

I've recently installed Ubuntu 8.10 on a Lenova 3000 v100 and am in the process of installing my applications.

Can you give me any clues as to how to get the regular desktop back?

Thanks

---

### Post by UbuntuNerd on 2009-03-31
try Alt+f2 and see if you get the "Run" menu

---

### Post by drs305 on 2009-03-31
If you just want the default panels back with the main stuff, this command will reset them to the original setting:
```
gconftool-2 --recursive-unset /apps/panel
```
You may have to run "killall gnome-panel" if it doesn't refresh immediately. Running that command will just make your screens refresh for a few seconds.

---

### Post by DavidDee on 2009-03-31
drs305, UbuntuNerd:

Appreciate your ideas:

None of the alt-F keys work except Alt-F6 which displays a Nautalus button in the middle of the screen that vanishes if I try to click it.


I entered these commands but nothing happened:

david@david-lenovo:/$ gconftool-2 --recursive-unset /apps/panel
david@david-lenovo:/$ sudo killall gnome-panel
gnome-panel: no process killed

Any more ideas appreciated.

David

---

### Post by paledread on 2009-04-01
My gnome-panel has also disappeared on one of my machines this morning after an update. I'm running gnome-panel under Openbox.

None of the above suggestions, nor rebooting appears to help.

Running gnome-panel from a terminal I get :

Xlib:  extension "Generic Event Extension" missing on display ":1048.0".
Xlib:  extension "Generic Event Extension" missing on display ":1048.0".
Xlib:  extension "Generic Event Extension" missing on display ":1048.0".
Xlib:  extension "Generic Event Extension" missing on display ":1048.0".
Xlib:  extension "Generic Event Extension" missing on display ":1048.0".
The program 'gnome-panel' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 109 error_code 1 request_code 150 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

[1]+  Exit 1                  gnome-panel

This is painful.

---

### Post by UbuntuNerd on 2009-04-03
> **DavidDee said:**
> drs305, UbuntuNerd:

Appreciate your ideas:

None of the alt-F keys work except Alt-F6 which displays a Nautalus button in the middle of the screen that vanishes if I try to click it.


I entered these commands but nothing happened:

david@david-lenovo:/$ gconftool-2 --recursive-unset /apps/panel
david@david-lenovo:/$ sudo killall gnome-panel
gnome-panel: no process killed

Any more ideas appreciated.

David
 if you're able try this command, it should restore your panels
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by AndersBrontosaurus on 2009-04-14
> **drs305 said:**
> If you just want the default panels back with the main stuff, this command will reset them to the original setting:
```
gconftool-2 --recursive-unset /apps/panel
```
You may have to run "killall gnome-panel" if it doesn't refresh immediately. Running that command will just make your screens refresh for a few seconds.

@DRS305: That did the trick for me. Eternal thankfulness!

Anders

---

