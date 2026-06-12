---
title: "Compiz config crashed and removed windows"
date: 2011-10-28
forum: Desktop Environments
---

### Post by Acharial on 2011-10-28
hello guys!

Was toying around in Compiz config and hit the "plug in" tab and there is where the program hanged itself and then all windows are gona and menus. There is only the background...

How can I fix this back to normal again? I'm pretty new to Ubuntu. This thing happened once before and I just reinstalled ubuntu. I feel like there must be some kind of better way to fix this than just reinstalling....

Any ideas?

---

### Post by linuxonbute on 2011-10-28
> **Acharial said:**
> hello guys!

Was toying around in Compiz config and hit the "plug in" tab and there is where the program hanged itself and then all windows are gona and menus. There is only the background...

How can I fix this back to normal again? I'm pretty new to Ubuntu. This thing happened once before and I just reinstalled ubuntu. I feel like there must be some kind of better way to fix this than just reinstalling....

Any ideas?
Not sure but I think that if you boot from a live ubuntu one option is some form of system repair.

---

### Post by stinkeye on 2011-10-28
If you can bring up a terminal with ctrl+alt+t
run
```
compiz --replace &
```

---

### Post by Acharial on 2011-10-28
> **stinkeye said:**
> If you can bring up a terminal with ctrl+alt+t
run
```
compiz --replace &
```

Tried this and still the same :(

---

### Post by stinkeye on 2011-10-28
Open ccsm > prefences and set to defaults.
Then re-enable the unity plugin resolving any conflicts as they pop up.
May need to run compiz --replace during the  process.

---

### Post by Acharial on 2011-10-28
I have no way to open the compiz config though since I cannot access my program bar. There is only the background. 

This is quite an annoying issue :(

---

### Post by stinkeye on 2011-10-28
No ctrl+alt+t terminal.

---

### Post by Acharial on 2011-10-28
This is the error message I keep getting when reseting unity-icons and unity in the terminal:

> unity-panel-service: ingen process hittades
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...[ERROR]: Option "next_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "next_no_popup_button" already defined
[ERROR]: Option "next_no_popup_key" already defined
[ERROR]: Option "prev_no_popup_button" already defined
[ERROR]: Option "prev_no_popup_key" already defined
[ERROR]: Option "next_panel_button" already defined
[ERROR]: Option "next_panel_key" already defined
[ERROR]: Option "prev_panel_button" already defined
[ERROR]: Option "prev_panel_key" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "auto_change_vp" already defined
[ERROR]: Option "popup_delay" already defined
[ERROR]: Option "mouse_select" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "brightness" already defined
[ERROR]: Option "opacity" already defined
[ERROR]: Option "icon" already defined
[ERROR]: Option "icon_only" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "row_align" already defined
[ERROR]: Option "focus_on_switch" already defined
[ERROR]: Option "bring_to_front" already defined
[ERROR]: Option "highlight_mode" already defined
[ERROR]: Option "highlight_rect_hidden" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "highlight_border_color" already defined
[ERROR]: Option "highlight_border_inlay_color" already defined
done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done

---

### Post by stinkeye on 2011-10-28
In the terminal see if you can bring up a panel.
```
gnome-panel
```
keep the terminal open.

Then open ccsm from the menu in the panel(under **other** on mine) and go to preferences
and set to defaults.
Wait a bit then re-enable the unity plugin,resolving conflicts and clicking on all the disable button popups.
Wait a bit and then close the terminal.

---

### Post by Acharial on 2011-10-28
I don't know how to thank you! This worked and IT's awesome. I'm really new to Linux and made a map with all issues and how I solve them for future reference.

Thanks a lot! /happypanda

---

### Post by stinkeye on 2011-10-28
No problem.
What you might want to look at is installing something like
**easystroke** ...a mouse gesture app which enables you to set commands to gestures.
Set **compiz --replace** and **gnome-terminal** to gestures.

and/or 

**kupfer** an app and command launcher that you bind to a keyboard shortcut.
Goodluck. :)

Keeping notes is a good idea.
Tomboy notes or gnotes is good for this.
I've got about 4 years worth.

---

### Post by Acharial on 2011-10-28
looks interesting! I'll check it out :):D

---

