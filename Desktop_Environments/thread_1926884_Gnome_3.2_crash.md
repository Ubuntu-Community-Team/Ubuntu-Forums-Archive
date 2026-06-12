---
title: "Gnome 3.2 crash"
date: 2012-02-17
forum: Desktop Environments
---

### Post by akashtripathi on 2012-02-17
Help my gnome 3 crashes on startup!
And if i try running it manually it shows this output in terminal

(gnome-shell:1736): folks-DEBUG: individual-aggregator.vala:310: Setting primary store IDs to defaults.
(gnome-shell:1736): folks-DEBUG: individual-aggregator.vala:338: Primary store IDs are 'eds' and 'system'.
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Fri Feb 17 2012 14:23:58 GMT+0530 (IST)

(gnome-shell:1736): folks-WARNING **: Failed to find primary PersonaStore with type ID 'eds' and ID 'system'.
Individuals will not be linked properly and creating new links between Personas will not work.
The configured primary PersonaStore's backend may not be installed. If you are unsure, check with your distribution.

(gnome-shell:1736): Clutter-CRITICAL **: clutter_text_get_editable: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:1736): Clutter-CRITICAL **: clutter_text_get_text: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:1736): Clutter-CRITICAL **: clutter_text_set_text: assertion `CLUTTER_IS_TEXT (self)' failed

St-ERROR **: st_widget_get_theme_node called on the widget [0xa347c00 StButton.status-chooser-user-icon] which is not in the stage.
Trace/breakpoint trap
gnome-shell-calendar-server[1745]: Got HUP on stdin - exiting






Please help
I am using ubuntu 11.10
Thanx

---

