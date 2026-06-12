---
title: "Broken GDM in 10.13"
date: 2013-11-08
forum: Desktop Environments
---

### Post by r.darwish on 2013-11-08
[COLOR=#333333][FONT=UbuntuRegular]I recently switched my 13.10 installation from Unity to Gnome Shell. I did that by installing ubuntu-gnome-desktop. Everything is working fine and I'm using LightDM, but I want to switch to GDM to get the full Gnome Experience.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I ran dpkg-reconfigure gdm, choose GDM and rebooted. Ubuntu seemed to boot as usual, but at the end of the boot process all I could see is a black screen. I switched to the terminal and ran service gdm stopand them service lightdm start to make sure LightDM still works, and it does.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Then I stopped LightDM and ran sudo gdm --fatal-warnings. This time I could see the cursor and move it, but gdm did not start. I'll I could find the the syslog was:[/FONT][/COLOR]
[INDENT]Nov 7 22:42:41 tarsonis gnome-session[3055]: dconf-CRITICAL: unable to op en file '/etc/dconf/db/gdm': Failed to open file '/etc/dconf/db/gdm': open () failed: No such file or directory; expect degraded performance
Nov 7 22:42:41 tarsonis gdm-simple-slave[2977]: Failed to give slave prog rams access to the display. Trying to proceed.
Nov 7 22:42:16 tarsonis gdm-simple-slave[2209]: GLib-GObject: g_object_un ref: assertion 'object->ref_count > 0' failed
[/INDENT]

---

