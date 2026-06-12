---
title: "After upgrade to Oneiric, Nautilus manages desktop"
date: 2011-10-27
forum: Desktop Environments
---

### Post by Ale1ster on 2011-10-27
1. After the upgrade to 11.10 (in Xubuntu), whenever I open Nautilus, it starts managing the desktop. I don't want it to act as a desktop manager.
The thing is that when i want to open something with Nautilus I don't want always to specify --no-desktop.
I have seen a solution saying to edit the preferences' 'show_desktop' value in apps/nautilus/preferences to false, but when I try to navigate there with gconf-editor, there is no such variable. Same with 'gconftool -t bool /apps/nautilus/preferences/show_desktop -s false'.
The variables that exist can be seen in the screenshot.

2. Nautilus is starting during system startup, but is nowhere to be found at Settings>Settings Manager>Session and Startup>Application Autostart.
How can that be?

The only thing I want is to use xfce default desktop manager and not Nautilus.
Can anyone help?

Edit: Also, this might not be of any significance, but whenever I try to start docky (after the upgrade), I get
 the following message:
"
[Info  20:47:05.489] Docky version: 2.2.0 bzr docky r1817 ppa
[Info  20:47:05.503] Kernel version: 3.0.0.12
[Info  20:47:05.503] CLR version: 2.0.50727.1433
Missing method System.Type::op_Inequality(Type,Type) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for GLib.GType ---> System.MissingMethodException: Method not found: 'System.Type.op_Inequality'.
  at GLib.GType..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Docky.Docky.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeInitializationException: An exception was thrown by the type initializer for GLib.GType ---> System.MissingMethodException: Method not found: 'System.Type.op_Inequality'.
  at GLib.GType..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Docky.Docky.Main (System.String[] args) [0x00000] in <filename unknown>:0 
"
Might that mean that some gnome libraries got renamed or deleted?

---

### Post by crdlb on 2011-10-27
1) You can disable the show-desktop-icons option in dconf-editor at org.gnome.desktop.background.

2) My guess is that the cause of this is the GNOME Compatibility option. It unconditionally runs autostart apps that contain OnlyShowIn=GNOME. With the show-desktop-icons option disabled, /etc/xdg/autostart/nautilus-autostart.desktop file will continue to start nautilus (which will exit because there's nothing for it to do).

I have no idea about the docky error, but it looks contained to mono to me.

---

### Post by Ale1ster on 2011-10-28
show-desktop-icons option was already disabled.
Nevertheless, by modifying /etc/xdg/autostart/nautilus-autostart.desktop file to

[Desktop Entry]
Type=Application
Name=Files
Exec=nautilus [COLOR="Red"]--no-desktop[/COLOR] -n
AutostartCondition=GSettings org.gnome.desktop.background show-desktop-icons
NoDisplay=true
OnlyShowIn=GNOME;Unity;
X-Ubuntu-Gettext-Domain=nautilus

it doesn't take over the desktop anymore.
Thank you.

---

### Post by foresto on 2011-11-22
I was having the same problem.

> **crdlb said:**
> 1) You can disable the show-desktop-icons option in dconf-editor at org.gnome.desktop.background.

After installing dconf-tools, I found that show-desktop-icons was unchecked.  I checked it and unchecked it again just to be sure, and took the extra precaution of unchecking the draw-background option.  After closing dconf-editor and rebooting, Nautilus no longer took over my desktop.

> **crdlb said:**
> 2) My guess is that the cause of this is the GNOME Compatibility option. It unconditionally runs autostart apps that contain OnlyShowIn=GNOME. With the show-desktop-icons option disabled, /etc/xdg/autostart/nautilus-autostart.desktop file will continue to start nautilus (which will exit because there's nothing for it to do).

Here are two related bug reports:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/872515](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/872515)
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/893811](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/893811)

Thanks so much for the workarounds!

---

