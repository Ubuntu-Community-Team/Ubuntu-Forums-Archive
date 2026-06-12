---
title: "Gnome-shell borken after downgrading from ricotz ppa"
date: 2011-11-26
forum: Desktop Environments
---

### Post by Wise Ferret on 2011-11-26
Hello!

I tried upgrading gnome-shell using ricotz ppa - a grave mistake as it broke my system completely. I downgraded all the packaged using ppa-purge, and made sure that no package originated from this ppa remains on my system. However, now I cannot log in to gnome-shell; all I get is the wallpaper.

What can I do in order to debug this and solve this? Is this a matter of clearing tainted user settings? If s, how can it be done?

---

### Post by ajgreeny on 2011-11-26
Have you reinstalled gnome shell?

Purging the ppa will have removed some packages, as you said, and I do not know if the system automatically replaces all of them from the standard repositories.

---

### Post by bmbaker on 2011-11-26
best todo do a full upgrade 
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install gnome-shell

if you get a problem open up gnome-classic and do it agin from there !

---

### Post by Wise Ferret on 2011-11-26
I did all this. I made sure through Synaptic that absolutely no package from the ppa remained. I re-installed gnome-shell and everything with "mutter" or "clutter" in its name, and, of course. updated and dist-upgraded. 
Still, I get only wallpaper instead of gnome-shell.

---

### Post by ajgreeny on 2011-11-26
Could be it is some changes made to your /home configuration files and folders by the upgraded version of gnome-shell.

What happens if you make a new user?  Does gnome-shell then work OK?

---

### Post by Frogs Hair on 2011-11-26
You either have to use the PPA or the shell package from the software center not both . The version of the shell in the software center will likely remain 3.2.1 for the life of the 11.10 release . A distribution upgrade will give you the highest version available in the Ubuntu repository for your current release .

I looked in to the same PPA as a means of updating to 3,2,2  , but do to a warring about possible breakage I chose not to take the risk .  I don't know what may be causing the problem if the PPA was complely removed .

---

### Post by Wise Ferret on 2011-11-26
The problem appears on new accounts as well, so I can rule out local configuration.

However, I think I found a useful hint in y xsession-errors log:
```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/test/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/00_handle_guest_session
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
gnome-session[3916]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
GNOME_KEYRING_CONTROL=/tmp/keyring-CuNEC7
GPG_AGENT_INFO=/tmp/keyring-CuNEC7/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-CuNEC7
GPG_AGENT_INFO=/tmp/keyring-CuNEC7/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-CuNEC7/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-CuNEC7
GPG_AGENT_INFO=/tmp/keyring-CuNEC7/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-CuNEC7
GPG_AGENT_INFO=/tmp/keyring-CuNEC7/gpg:0:1

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-settings-daemon:3994): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
** (gnome-fallback-mount-helper:4026): DEBUG: Starting automounting manager
Initializing nautilus-gdu extension
** (nautilus:4028): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-dropbox 0.7.1
** (gnome-fallback-mount-helper:4026): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session12
** (gnome-fallback-mount-helper:4026): DEBUG: ScreenSaver name vanished
** (gnome-fallback-mount-helper:4026): DEBUG: ConsoleKit session is active 1
    JS ERROR: !!!   Exception was: Error: Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/environment.js:9
"'
    JS ERROR: !!!     message = '"Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found"'
    JS ERROR: !!!   Exception was: Error: Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/environment.js:9
"'
    JS ERROR: !!!     message = '"Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found

(nautilus:4028): libnotify-WARNING **: Failed to connect to proxy

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

** (nautilus:4028): WARNING **: Can not get _NET_WORKAREA

** (nautilus:4028): WARNING **: Can not determine workarea, guessing at layout

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:4028): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:4028): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed
** (process:4061): DEBUG: Telepathy Indicator started
** Message: applet now removed from the notification area
    JS ERROR: !!!   Exception was: Error: Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/environment.js:9
"'
    JS ERROR: !!!     message = '"Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found"'
    JS ERROR: !!!   Exception was: Error: Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/environment.js:9
"'
    JS ERROR: !!!     message = '"Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found

(nm-applet:4041): libnotify-WARNING **: Failed to connect to proxy
gnome-session[3916]: WARNING: App 'gnome-shell.desktop' respawning too quickly
gnome-session[3916]: CRITICAL: We failed, but the fail whale is dead. Sorry....
** Message: using fallback from indicator to GtkStatusIcon
python: can't open file '/usr/share/gnome-panel/add-indicator-applet.py': [Errno 2] No such file or directory

(gnome-settings-daemon:3994): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(check-new-release-gtk:4102): Gtk-WARNING **: Unknown property: GtkMessageDialog.has-separator
WARNING:root:timeout reached, exiting
** (deja-dup-monitor:4121): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.
** (gnome-fallback-mount-helper:4026): DEBUG: ConsoleKit session is active 0

(gnome-settings-daemon:3994): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:4026): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gdu-notification-daemon:4071): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(evolution-alarm-notify:4094): Gdk-WARNING **: evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-session[3916]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1442 requests (1442 known processed) with 0 events remaining.

(nm-applet:4041): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:4096): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:4028): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
** (process:4074): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:4074): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```

Note the multiple lines of:
```
    JS ERROR: !!!     message = '"Requiring Clutter, version 1.0: Typelib file for namespace 'CoglPango', version '1.0' not found"'
```

Any idea? Is there some package I need to remove or add here?

EDIT: This may be related to bug #877135. Does anyone have a 64-bit cogl-pango deb(s)?

---

### Post by Frogs Hair on 2011-11-26
If you can login to unity and have the synaptic package manager installed lookup  libclutter-1.0-common and see if it is installed . The errors may be pointing to this package .

---

### Post by Wise Ferret on 2011-11-26
> **Frogs Hair said:**
> If you can login to unity and have the synaptic package manager installed lookup  libclutter-1.0-common and see if it is installed . The errors may be pointing to this package .

Thanks, but libclutter-1.0 commmon is already installed (1.8.0-1~svn1). Any other ideas of how to fix this?

---

### Post by Wise Ferret on 2011-11-26
> **ajgreeny said:**
> Have you reinstalled gnome shell?

Purging the ppa will have removed some packages, as you said, and I do not know if the system automatically replaces all of them from the standard repositories.

I re-installed gnome-shell, but to no avail.
I am absolutely certain that no packages from the culprit ppa remain on my system. The "local" section in Synaptic contains now only games and such...

---

### Post by Wise Ferret on 2011-11-26
Problem seems to have disappeared magically! Gnome-shell is back and runinng and the weird cogl-pango errors taint my xsession-errors no more. I hope this will not come back, and in the meanwhile thank you all for sharing my confusion.

---

