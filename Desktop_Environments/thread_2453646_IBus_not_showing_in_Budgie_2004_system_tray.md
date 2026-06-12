---
title: "IBus not showing in Budgie 2004 system tray"
date: 2020-11-14
forum: Desktop Environments
---

### Post by chaopoch on 2020-11-14
Don't know which update broke this, the Ibus systray icon disappears,
and the combined keys Ctrl+space is not working either.

I need to switch input method between Chinese and English,
but now Chinese input is not available. thanks for help.

---

### Post by davidmohammed on 2020-11-16
The layouts should be displayed via the keyboard indicator layout applet that you can add to your panel.

---

### Post by chaopoch on 2020-11-17
> **davidmohammed said:**
> The layouts should be displayed via the keyboard indicator layout applet that you can add to your panel.

Thanks for reply, but this is not what I want


Google arround and find the real solution - start the IBus daemon, 
but I still don't understand why the IBus daemon does not start automatically when I power on the computer.

Here is what I have to do to start the IBus daemon automatically:


[LIST]
[*=left][FONT=inherit]Open [FONT=inherit]System > Preferences > Startup Applications[/FONT][/FONT]
[*=left]Click on the "Add" button
[*=left]Write command as: "/usr/bin/ibus-daemon -dr"
[*=left]Click on the "Add" button
[*=left]
[/LIST]
 then r[COLOR=#333333][FONT=Ubuntu]estart or re-login the computer, the IBus icon is showing on the tray.
now, the problem is SOLVED.


[/FONT][/COLOR]

---

