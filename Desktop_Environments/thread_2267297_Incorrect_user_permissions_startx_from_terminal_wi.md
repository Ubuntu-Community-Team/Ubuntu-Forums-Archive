---
title: "Incorrect user permissions: startx from terminal with ~/.xsession file"
date: 2015-02-28
forum: Desktop Environments
---

### Post by Opayq on 2015-02-28
Hi,

I'm having this strange issue where my user permissions are totally different after starting a GUI session from the terminal. I boot my Lubuntu 14.04.2 system in text mode with the following line *GRUB_CMDLINE_LINUX_DEFAULT="nomdmonddf nomdmonisw text" *in /etc/default/grub. I login to my only user account and after that I run startx. I have my ~/.xsession file set up as per this post: [http://ubuntuforums.org/showthread.php?t=2222849&page=2&p=13018219#post13018219](http://ubuntuforums.org/showthread.php?t=2222849&page=2&p=13018219#post13018219) and that works great. However, when I am in the desktop environment it seems permissions or policykit policies are incorrect. For example, mounting a USB stick asks me for authentication as wel as rebooting the system.

When I remove "text" from GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, run sudo update-grub and reboot the system I can mount the usb drive without entering my password. Also rebooting etc. works fine. So my question is: how can I boot to the command line interface by default, but still use the desktop environment easily with the right user policy / permissions? What is the 'default boot process' doing differently that allows my user to mount a usb drive?

Any help will be appreciated!

Edit:
I have experimented with policy-kit and found out that I can override these authentication requests by making a pkla file in /etc/polkit-1/localauthority/90-mandatory.d/filename.pkla with contents:

[Always require admin]
Identity=unix-group:group_of_my_user
Action=*
ResultAny=auth_admin
[B]ResultInactive=yes
[/B]ResultActive=yes

However, this is not the solution to the problem. The line in bold is important. It seems that somehow starting the desktop environment in this way makes my an 'Inactive' user. Changing that line to auth_admin gives me the annoying authentication requests again for usb mounting etc.

---

### Post by Opayq on 2015-02-28
.xsession-errors
Terminated
Xsession: X session started for opayq at za feb 28 22:34:29 CET 2015
localuser: opayq being added to access control list
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Unable to create /home/opayq/.dbus/session-bus
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
** Message: main.vala:99: Session is Lubuntu
** Message: main.vala:100: DE is LXDE
** Message: main.vala:131: log directory: /home/opayq/.cache/lxsession/Lubuntu
** Message: main.vala:132: log path: /home/opayq/.cache/lxsession/Lubuntu/run.log

```
run.log
** Message: environement.vala:58: Exporting primary_variable
** Message: environement.vala:59: desktop_environnement XDG_CURRENT_DESKTOP
** Message: environement.vala:149: confir_dirs is null, export : /etc/xdg/lubuntu:/etc/xdg
** Message: environement.vala:183: Exporting XDG_CONFIG_DIRS
** Message: environement.vala:190: data_dirs is null, export : /etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg
** Message: environement.vala:224: Exporting XDG_DATA_DIRS
** Message: utils.vala:68: User config used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:89: Final file used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: settings.vala:619: Create new config key: Session;windows_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, windows_manager, command, string, openbox: 
** Message: settings.vala:359: key of set_value: Session;windows_manager;command;
** Message: settings.vala:924: Changing Session - windows_manager - command to openbox
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;windows_manager;session;
** Message: settings.vala:105: Enter if of read_value for Session, windows_manager, session, string, Lubuntu: 
** Message: settings.vala:359: key of set_value: Session;windows_manager;session;
** Message: settings.vala:924: Changing Session - windows_manager - session to Lubuntu
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;windows_manager;extras;
** Message: settings.vala:105: Enter if of read_value for Session, windows_manager, extras, string, : 
** Message: settings.vala:359: key of set_value: Session;windows_manager;extras;
** Message: settings.vala:924: Changing Session - windows_manager - extras to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;panel;command;
** Message: settings.vala:105: Enter if of read_value for Session, panel, command, string, lxpanel: 
** Message: settings.vala:359: key of set_value: Session;panel;command;
** Message: settings.vala:924: Changing Session - panel - command to lxpanel
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;panel;session;
** Message: settings.vala:105: Enter if of read_value for Session, panel, session, string, Lubuntu: 
** Message: settings.vala:359: key of set_value: Session;panel;session;
** Message: settings.vala:924: Changing Session - panel - session to Lubuntu
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:513: Key file does not have key 'dock/command'
** Message: settings.vala:619: Create new config key: Session;file_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, file_manager, command, string, pcmanfm: 
** Message: settings.vala:359: key of set_value: Session;file_manager;command;
** Message: settings.vala:924: Changing Session - file_manager - command to pcmanfm
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;file_manager;session;
** Message: settings.vala:105: Enter if of read_value for Session, file_manager, session, string, lubuntu: 
** Message: settings.vala:359: key of set_value: Session;file_manager;session;
** Message: settings.vala:924: Changing Session - file_manager - session to lubuntu
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;file_manager;extras;
** Message: settings.vala:105: Enter if of read_value for Session, file_manager, extras, string, : 
** Message: settings.vala:359: key of set_value: Session;file_manager;extras;
** Message: settings.vala:924: Changing Session - file_manager - extras to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;desktop_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, desktop_manager, command, string, filemanager: 
** Message: settings.vala:359: key of set_value: Session;desktop_manager;command;
** Message: settings.vala:924: Changing Session - desktop_manager - command to filemanager
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;desktop_manager;wallpaper;
** Message: settings.vala:105: Enter if of read_value for Session, desktop_manager, wallpaper, string, : 
** Message: settings.vala:359: key of set_value: Session;desktop_manager;wallpaper;
** Message: settings.vala:924: Changing Session - desktop_manager - wallpaper to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;launcher_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, launcher_manager, command, string, lxpanelctl: 
** Message: settings.vala:359: key of set_value: Session;launcher_manager;command;
** Message: settings.vala:924: Changing Session - launcher_manager - command to lxpanelctl
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;launcher_manager;autostart;
** Message: settings.vala:105: Enter if of read_value for Session, launcher_manager, autostart, string, false: 
** Message: settings.vala:359: key of set_value: Session;launcher_manager;autostart;
** Message: settings.vala:924: Changing Session - launcher_manager - autostart to false
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;composite_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, composite_manager, command, string, : 
** Message: settings.vala:359: key of set_value: Session;composite_manager;command;
** Message: settings.vala:924: Changing Session - composite_manager - command to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;composite_manager;autostart;
** Message: settings.vala:105: Enter if of read_value for Session, composite_manager, autostart, string, : 
** Message: settings.vala:359: key of set_value: Session;composite_manager;autostart;
** Message: settings.vala:924: Changing Session - composite_manager - autostart to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;im1;command;
** Message: settings.vala:105: Enter if of read_value for Session, im1, command, string, pidgin: 
** Message: settings.vala:359: key of set_value: Session;im1;command;
** Message: settings.vala:924: Changing Session - im1 - command to pidgin
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;im1;autostart;
** Message: settings.vala:105: Enter if of read_value for Session, im1, autostart, string, : 
** Message: settings.vala:359: key of set_value: Session;im1;autostart;
** Message: settings.vala:924: Changing Session - im1 - autostart to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:513: Key file does not have key 'im2/command'
** Message: settings.vala:513: Key file does not have key 'widget1/command'
** Message: settings.vala:513: Key file does not have key 'notification/command'
** Message: settings.vala:513: Key file does not have key 'keybindings/command'
** Message: settings.vala:619: Create new config key: Session;screensaver;command;
** Message: settings.vala:105: Enter if of read_value for Session, screensaver, command, string, : 
** Message: settings.vala:359: key of set_value: Session;screensaver;command;
** Message: settings.vala:924: Changing Session - screensaver - command to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;power_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, power_manager, command, string, auto: 
** Message: settings.vala:359: key of set_value: Session;power_manager;command;
** Message: settings.vala:924: Changing Session - power_manager - command to auto
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;polkit;command;
** Message: settings.vala:105: Enter if of read_value for Session, polkit, command, string, lxpolkit: 
** Message: settings.vala:359: key of set_value: Session;polkit;command;
** Message: settings.vala:924: Changing Session - polkit - command to lxpolkit
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;audio_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, audio_manager, command, string, alsamixer: 
** Message: settings.vala:359: key of set_value: Session;audio_manager;command;
** Message: settings.vala:924: Changing Session - audio_manager - command to alsamixer
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;quit_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, command, string, lxsession-logout: 
** Message: settings.vala:359: key of set_value: Session;quit_manager;command;
** Message: settings.vala:924: Changing Session - quit_manager - command to lxsession-logout
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, command, string, lxsession-logout: 
** Message: settings.vala:619: Create new config key: Session;quit_manager;image;
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, image, string, /usr/share/lubuntu/images/logout-banner.png: 
** Message: settings.vala:359: key of set_value: Session;quit_manager;image;
** Message: settings.vala:924: Changing Session - quit_manager - image to /usr/share/lubuntu/images/logout-banner.png
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;quit_manager;layout;
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, layout, string, top: 
** Message: settings.vala:359: key of set_value: Session;quit_manager;layout;
** Message: settings.vala:924: Changing Session - quit_manager - layout to top
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;workspace_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, workspace_manager, command, string, obconf: 
** Message: settings.vala:359: key of set_value: Session;workspace_manager;command;
** Message: settings.vala:924: Changing Session - workspace_manager - command to obconf
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;terminal_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, terminal_manager, command, string, x-terminal-emulator: 
** Message: settings.vala:359: key of set_value: Session;terminal_manager;command;
** Message: settings.vala:924: Changing Session - terminal_manager - command to x-terminal-emulator
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;screenshot_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, screenshot_manager, command, string, scrot: 
** Message: settings.vala:359: key of set_value: Session;screenshot_manager;command;
** Message: settings.vala:924: Changing Session - screenshot_manager - command to scrot
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;lock_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, lock_manager, command, string, lxlock: 
** Message: settings.vala:359: key of set_value: Session;lock_manager;command;
** Message: settings.vala:924: Changing Session - lock_manager - command to lxlock
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;message_manager;command;
** Message: settings.vala:513: Key file does not have key 'message_manager/command'
** Message: settings.vala:105: Enter if of read_value for Session, message_manager, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;upgrade_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, upgrade_manager, command, string, update-manager: 
** Message: settings.vala:359: key of set_value: Session;upgrade_manager;command;
** Message: settings.vala:924: Changing Session - upgrade_manager - command to update-manager
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;clipboard;command;
** Message: settings.vala:105: Enter if of read_value for Session, clipboard, command, string, lxclipboard: 
** Message: settings.vala:359: key of set_value: Session;clipboard;command;
** Message: settings.vala:924: Changing Session - clipboard - command to lxclipboard
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;disable_autostart;;
** Message: settings.vala:105: Enter if of read_value for Session, disable_autostart, (null), string, no: 
** Message: settings.vala:359: key of set_value: Session;disable_autostart;;
** Message: settings.vala:912: Changing Session - disable_autostart to no
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;upstart_user_session;;
** Message: settings.vala:105: Enter if of read_value for Session, upstart_user_session, (null), string, false: 
** Message: settings.vala:359: key of set_value: Session;upstart_user_session;;
** Message: settings.vala:912: Changing Session - upstart_user_session to false
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;xsettings_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, xsettings_manager, command, string, build-in: 
** Message: settings.vala:359: key of set_value: Session;xsettings_manager;command;
** Message: settings.vala:924: Changing Session - xsettings_manager - command to build-in
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;proxy_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, proxy_manager, command, string, build-in: 
** Message: settings.vala:359: key of set_value: Session;proxy_manager;command;
** Message: settings.vala:924: Changing Session - proxy_manager - command to build-in
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;proxy_manager;http;
** Message: settings.vala:513: Key file does not have key 'proxy_manager/http'
** Message: settings.vala:105: Enter if of read_value for Session, proxy_manager, http, string, (null): 
** Message: settings.vala:619: Create new config key: Session;a11y;command;
** Message: settings.vala:513: Key file does not have key 'a11y/command'
** Message: settings.vala:105: Enter if of read_value for Session, a11y, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;keyring;command;
** Message: settings.vala:105: Enter if of read_value for Session, keyring, command, string, ssh-agent: 
** Message: settings.vala:359: key of set_value: Session;keyring;command;
** Message: settings.vala:924: Changing Session - keyring - command to ssh-agent
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;xrandr;command;
** Message: settings.vala:513: Key file does not have key 'xrandr/command'
** Message: settings.vala:105: Enter if of read_value for Session, xrandr, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;webbrowser;command;
** Message: settings.vala:105: Enter if of read_value for Session, webbrowser, command, string, x-www-browser: 
** Message: settings.vala:359: key of set_value: Session;webbrowser;command;
** Message: settings.vala:924: Changing Session - webbrowser - command to x-www-browser
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;email;command;
** Message: settings.vala:105: Enter if of read_value for Session, email, command, string, sylpheed: 
** Message: settings.vala:359: key of set_value: Session;email;command;
** Message: settings.vala:924: Changing Session - email - command to sylpheed
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;pdf_reader;command;
** Message: settings.vala:105: Enter if of read_value for Session, pdf_reader, command, string, evince: 
** Message: settings.vala:359: key of set_value: Session;pdf_reader;command;
** Message: settings.vala:924: Changing Session - pdf_reader - command to evince
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;video_player;command;
** Message: settings.vala:105: Enter if of read_value for Session, video_player, command, string, gnome-mplayer: 
** Message: settings.vala:359: key of set_value: Session;video_player;command;
** Message: settings.vala:924: Changing Session - video_player - command to gnome-mplayer
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;audio_player;command;
** Message: settings.vala:105: Enter if of read_value for Session, audio_player, command, string, audacious: 
** Message: settings.vala:359: key of set_value: Session;audio_player;command;
** Message: settings.vala:924: Changing Session - audio_player - command to audacious
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;images_display;command;
** Message: settings.vala:105: Enter if of read_value for Session, images_display, command, string, gpicview: 
** Message: settings.vala:359: key of set_value: Session;images_display;command;
** Message: settings.vala:924: Changing Session - images_display - command to gpicview
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;text_editor;command;
** Message: settings.vala:105: Enter if of read_value for Session, text_editor, command, string, leafpad: 
** Message: settings.vala:359: key of set_value: Session;text_editor;command;
** Message: settings.vala:924: Changing Session - text_editor - command to leafpad
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;archive;command;
** Message: settings.vala:105: Enter if of read_value for Session, archive, command, string, file-roller: 
** Message: settings.vala:359: key of set_value: Session;archive;command;
** Message: settings.vala:924: Changing Session - archive - command to file-roller
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;charmap;command;
** Message: settings.vala:513: Key file does not have key 'charmap/command'
** Message: settings.vala:105: Enter if of read_value for Session, charmap, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;calculator;command;
** Message: settings.vala:105: Enter if of read_value for Session, calculator, command, string, galculator: 
** Message: settings.vala:359: key of set_value: Session;calculator;command;
** Message: settings.vala:924: Changing Session - calculator - command to galculator
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;spreadsheet;command;
** Message: settings.vala:105: Enter if of read_value for Session, spreadsheet, command, string, gnumeric: 
** Message: settings.vala:359: key of set_value: Session;spreadsheet;command;
** Message: settings.vala:924: Changing Session - spreadsheet - command to gnumeric
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;bittorent;command;
** Message: settings.vala:105: Enter if of read_value for Session, bittorent, command, string, transmission-gtk: 
** Message: settings.vala:359: key of set_value: Session;bittorent;command;
** Message: settings.vala:924: Changing Session - bittorent - command to transmission-gtk
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;document;command;
** Message: settings.vala:105: Enter if of read_value for Session, document, command, string, abiword: 
** Message: settings.vala:359: key of set_value: Session;document;command;
** Message: settings.vala:924: Changing Session - document - command to abiword
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;webcam;command;
** Message: settings.vala:105: Enter if of read_value for Session, webcam, command, string, guvcview: 
** Message: settings.vala:359: key of set_value: Session;webcam;command;
** Message: settings.vala:924: Changing Session - webcam - command to guvcview
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;burn;command;
** Message: settings.vala:105: Enter if of read_value for Session, burn, command, string, xfburn: 
** Message: settings.vala:359: key of set_value: Session;burn;command;
** Message: settings.vala:924: Changing Session - burn - command to xfburn
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;notes;command;
** Message: settings.vala:105: Enter if of read_value for Session, notes, command, string, xpad: 
** Message: settings.vala:359: key of set_value: Session;notes;command;
** Message: settings.vala:924: Changing Session - notes - command to xpad
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;disk_utility;command;
** Message: settings.vala:105: Enter if of read_value for Session, disk_utility, command, string, gnome-disks: 
** Message: settings.vala:359: key of set_value: Session;disk_utility;command;
** Message: settings.vala:924: Changing Session - disk_utility - command to gnome-disks
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;tasks;command;
** Message: settings.vala:105: Enter if of read_value for Session, tasks, command, string, lxtask: 
** Message: settings.vala:359: key of set_value: Session;tasks;command;
** Message: settings.vala:924: Changing Session - tasks - command to lxtask
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keymap;mode;;
** Message: settings.vala:105: Enter if of read_value for Keymap, mode, (null), string, system: 
** Message: settings.vala:359: key of set_value: Keymap;mode;;
** Message: settings.vala:912: Changing Keymap - mode to system
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keymap;model;;
** Message: settings.vala:105: Enter if of read_value for Keymap, model, (null), string, : 
** Message: settings.vala:359: key of set_value: Keymap;model;;
** Message: settings.vala:912: Changing Keymap - model to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keymap;layout;;
** Message: settings.vala:105: Enter if of read_value for Keymap, layout, (null), string, : 
** Message: settings.vala:359: key of set_value: Keymap;layout;;
** Message: settings.vala:912: Changing Keymap - layout to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keymap;variant;;
** Message: settings.vala:105: Enter if of read_value for Keymap, variant, (null), string, : 
** Message: settings.vala:359: key of set_value: Keymap;variant;;
** Message: settings.vala:912: Changing Keymap - variant to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keymap;options;;
** Message: settings.vala:105: Enter if of read_value for Keymap, options, (null), string, : 
** Message: settings.vala:359: key of set_value: Keymap;options;;
** Message: settings.vala:912: Changing Keymap - options to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: State;laptop_mode;;
** Message: settings.vala:105: Enter if of read_value for State, laptop_mode, (null), string, no: 
** Message: settings.vala:359: key of set_value: State;laptop_mode;;
** Message: settings.vala:912: Changing State - laptop_mode to no
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: State;guess_default;;
** Message: settings.vala:105: Enter if of read_value for State, guess_default, (null), string, true: 
** Message: settings.vala:359: key of set_value: State;guess_default;;
** Message: settings.vala:912: Changing State - guess_default to true
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Dbus;lxde;;
** Message: settings.vala:105: Enter if of read_value for Dbus, lxde, (null), string, true: 
** Message: settings.vala:359: key of set_value: Dbus;lxde;;
** Message: settings.vala:912: Changing Dbus - lxde to true
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Dbus;gnome;;
** Message: settings.vala:105: Enter if of read_value for Dbus, gnome, (null), string, false: 
** Message: settings.vala:359: key of set_value: Dbus;gnome;;
** Message: settings.vala:912: Changing Dbus - gnome to false
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Updates;type;;
** Message: settings.vala:513: Key file does not have key 'type'
** Message: settings.vala:105: Enter if of read_value for Updates, type, (null), string, (null): 
** Message: settings.vala:619: Create new config key: Environment;type;;
** Message: settings.vala:105: Enter if of read_value for Environment, type, (null), string, lubuntu: 
** Message: settings.vala:359: key of set_value: Environment;type;;
** Message: settings.vala:912: Changing Environment - type to lubuntu
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Environment;menu_prefix;;
** Message: settings.vala:105: Enter if of read_value for Environment, menu_prefix, (null), string, lxde-: 
** Message: settings.vala:359: key of set_value: Environment;menu_prefix;;
** Message: settings.vala:912: Changing Environment - menu_prefix to lxde-
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sNet;ThemeName;
** Message: settings.vala:105: Enter if of read_value for GTK, sNet, ThemeName, string, Lubuntu-default: 
** Message: settings.vala:359: key of set_value: GTK;sNet;ThemeName;
** Message: settings.vala:924: Changing GTK - sNet - ThemeName to Lubuntu-default
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sNet;IconThemeName;
** Message: settings.vala:105: Enter if of read_value for GTK, sNet, IconThemeName, string, lubuntu: 
** Message: settings.vala:359: key of set_value: GTK;sNet;IconThemeName;
** Message: settings.vala:924: Changing GTK - sNet - IconThemeName to lubuntu
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sGtk;FontName;
** Message: settings.vala:105: Enter if of read_value for GTK, sGtk, FontName, string, Ubuntu 11: 
** Message: settings.vala:359: key of set_value: GTK;sGtk;FontName;
** Message: settings.vala:924: Changing GTK - sGtk - FontName to Ubuntu 11
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;ToolbarStyle;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, ToolbarStyle, string, 3: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ToolbarStyle;
** Message: settings.vala:924: Changing GTK - iGtk - ToolbarStyle to 3
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;ButtonImages;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, ButtonImages, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ButtonImages;
** Message: settings.vala:924: Changing GTK - iGtk - ButtonImages to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;MenuImages;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, MenuImages, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;MenuImages;
** Message: settings.vala:924: Changing GTK - iGtk - MenuImages to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;CursorThemeSize;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, CursorThemeSize, string, 18: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;CursorThemeSize;
** Message: settings.vala:924: Changing GTK - iGtk - CursorThemeSize to 18
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iXft;Antialias;
** Message: settings.vala:105: Enter if of read_value for GTK, iXft, Antialias, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iXft;Antialias;
** Message: settings.vala:924: Changing GTK - iXft - Antialias to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iXft;Hinting;
** Message: settings.vala:105: Enter if of read_value for GTK, iXft, Hinting, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iXft;Hinting;
** Message: settings.vala:924: Changing GTK - iXft - Hinting to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sXft;HintStyle;
** Message: settings.vala:105: Enter if of read_value for GTK, sXft, HintStyle, string, hintslight: 
** Message: settings.vala:359: key of set_value: GTK;sXft;HintStyle;
** Message: settings.vala:924: Changing GTK - sXft - HintStyle to hintslight
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sXft;RGBA;
** Message: settings.vala:105: Enter if of read_value for GTK, sXft, RGBA, string, rgb: 
** Message: settings.vala:359: key of set_value: GTK;sXft;RGBA;
** Message: settings.vala:924: Changing GTK - sXft - RGBA to rgb
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sGtk;ColorScheme;
** Message: settings.vala:105: Enter if of read_value for GTK, sGtk, ColorScheme, string, : 
** Message: settings.vala:359: key of set_value: GTK;sGtk;ColorScheme;
** Message: settings.vala:924: Changing GTK - sGtk - ColorScheme to 
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sGtk;CursorThemeName;
** Message: settings.vala:105: Enter if of read_value for GTK, sGtk, CursorThemeName, string, DMZ-White: 
** Message: settings.vala:359: key of set_value: GTK;sGtk;CursorThemeName;
** Message: settings.vala:924: Changing GTK - sGtk - CursorThemeName to DMZ-White
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;ToolbarIconSize;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, ToolbarIconSize, string, 3: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ToolbarIconSize;
** Message: settings.vala:924: Changing GTK - iGtk - ToolbarIconSize to 3
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iNet;EnableEventSounds;
** Message: settings.vala:105: Enter if of read_value for GTK, iNet, EnableEventSounds, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iNet;EnableEventSounds;
** Message: settings.vala:924: Changing GTK - iNet - EnableEventSounds to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iNet;EnableInputFeedbackSounds;
** Message: settings.vala:105: Enter if of read_value for GTK, iNet, EnableInputFeedbackSounds, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iNet;EnableInputFeedbackSounds;
** Message: settings.vala:924: Changing GTK - iNet - EnableInputFeedbackSounds to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Mouse;AccFactor;;
** Message: settings.vala:105: Enter if of read_value for Mouse, AccFactor, (null), string, 20: 
** Message: settings.vala:359: key of set_value: Mouse;AccFactor;;
** Message: settings.vala:912: Changing Mouse - AccFactor to 20
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Mouse;AccThreshold;;
** Message: settings.vala:105: Enter if of read_value for Mouse, AccThreshold, (null), string, 10: 
** Message: settings.vala:359: key of set_value: Mouse;AccThreshold;;
** Message: settings.vala:912: Changing Mouse - AccThreshold to 10
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Mouse;LeftHanded;;
** Message: settings.vala:105: Enter if of read_value for Mouse, LeftHanded, (null), string, 0: 
** Message: settings.vala:359: key of set_value: Mouse;LeftHanded;;
** Message: settings.vala:912: Changing Mouse - LeftHanded to 0
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keyboard;Delay;;
** Message: settings.vala:105: Enter if of read_value for Keyboard, Delay, (null), string, 500: 
** Message: settings.vala:359: key of set_value: Keyboard;Delay;;
** Message: settings.vala:912: Changing Keyboard - Delay to 500
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keyboard;Interval;;
** Message: settings.vala:105: Enter if of read_value for Keyboard, Interval, (null), string, 30: 
** Message: settings.vala:359: key of set_value: Keyboard;Interval;;
** Message: settings.vala:912: Changing Keyboard - Interval to 30
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keyboard;Beep;;
** Message: settings.vala:105: Enter if of read_value for Keyboard, Beep, (null), string, 1: 
** Message: settings.vala:359: key of set_value: Keyboard;Beep;;
** Message: settings.vala:912: Changing Keyboard - Beep to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:435: Monitoring: /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: settings.vala:439: Desktop file is already in config home, do nothing
** Message: settings.vala:346: Settings default for GTK, iGtk, ColorScheme : 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ColorScheme;
** Message: settings.vala:924: Changing GTK - iGtk - ColorScheme to 
** Message: settings.vala:860: Saving desktop file
** Message: environement.vala:79: Exporting variable
** Message: environement.vala:80: desktop_environnement XDG_CURRENT_DESKTOP
** Message: environement.vala:176: custom_config :
** Message: environement.vala:177: config_dirs :/etc/xdg/lubuntu:/etc/xdg
** Message: environement.vala:178: confir_dirs not null, export : /etc/xdg/lubuntu:/etc/xdg
** Message: environement.vala:183: Exporting XDG_CONFIG_DIRS
** Message: environement.vala:217: custom_data :
** Message: environement.vala:218: data_dirs :/etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg
** Message: environement.vala:219: data_dirs not null, export : /etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg
** Message: environement.vala:224: Exporting XDG_DATA_DIRS
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/Lubuntu
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/Lubuntu/conffiles.conf
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/Lubuntu/conffiles.conf
** Message: options.vala:164: Activate xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:89: Final file used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
xprop:  no such property "_NET_NUMBER_OF_DESKTOPS"
xprop:  no such property "_NET_DESKTOP_NAMES"
** Message: main.vala:231: DEBUG2 : openbox
** Message: app.vala:431: DEBUG6 : lxpanel
** Message: app.vala:433: DEBUG6 : Lubuntu
** Message: app.vala:431: DEBUG6 : lxpanel
** Message: app.vala:433: DEBUG6 : Lubuntu
** Message: app.vala:76: Launching lxpanel 
** Message: main.vala:320: DEBUG4 : filemanager
** Message: app.vala:76: Launching pcmanfm 
** Message: app.vala:717: polkit separate
** Message: app.vala:717: polkit separate
** Message: utils.vala:68: User config used : /home/opayq/.config/lxsession/Lubuntu/autostart
** Message: utils.vala:89: Final file used : /home/opayq/.config/lxsession/Lubuntu/autostart
** Message: autostart.vala:42: Autostart path : /home/opayq/.config/lxsession/Lubuntu/autostart
** Message: options.vala:107: Create build-in Clipboard
** Message: main.vala:429: Check keymap_mode system
** Message: main.vala:432: Create Option Keymap
** Message: app.vala:76: Launching /usr/bin/ssh-agent 
SSH_AUTH_SOCK=/tmp/ssh-VuBqbcUaczA1/agent.10165; export SSH_AUTH_SOCK;
SSH_AGENT_PID=10170; export SSH_AGENT_PID;
echo Agent pid 10170;
** Message: app.vala:130: /usr/bin/ssh-agent exit with this type of exit: 0
/home/opayq/.config/autostart/screensaver-settings.desktop
/home/opayq/.config/autostart/light-locker.desktop
/etc/xdg/autostart/user-dirs-update-gtk.desktop
/etc/xdg/autostart/gsettings-data-convert.desktop
/etc/xdg/autostart/at-spi-dbus-bus.desktop
/etc/xdg/autostart/indicator-application.desktop
/etc/xdg/autostart/blueman.desktop
/etc/xdg/autostart/print-applet.desktop
/etc/xdg/autostart/update-notifier.desktop
/etc/xdg/autostart/gnome-keyring-gpg.desktop
/etc/xdg/autostart/pulseaudio-kde.desktop
/etc/xdg/autostart/gnome-keyring-ssh.desktop
/etc/xdg/autostart/gnome-keyring-pkcs11.desktop
/etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
/etc/xdg/autostart/gnome-keyring-secrets.desktop
/etc/xdg/autostart/light-locker.desktop
/etc/xdg/autostart/pulseaudio.desktop
/etc/xdg/autostart/xfce4-power-manager.desktop
/etc/xdg/autostart/nm-applet.desktop
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
indicator: unknown var network


** (pcmanfm:10161): WARNING **: terminal lxsession-default-terminal isn't known, consider report it to LibFM developers
nm-applet-Message: using fallback from indicator to GtkStatusIcon
** Message: settings.vala:482: Desktop file change, reloading XSettings daemon
** Message: options.vala:186: Reload xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:89: Final file used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: settings.vala:476: Reload the xsettings option
** Message: settings.vala:482: Desktop file change, reloading XSettings daemon
** Message: options.vala:186: Reload xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: utils.vala:89: Final file used : /home/opayq/.config/lxsession/Lubuntu/desktop.conf
** Message: settings.vala:476: Reload the xsettings option


** (pcmanfm:10161): WARNING **: modules directory is not accessible
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
```

---

### Post by steeldriver on 2015-02-28
This seems suspicious to me:
```

Unable to create /home/opayq/.dbus/session-bus

```

---

### Post by Opayq on 2015-03-01
Seems suspicious to me too. This is what is in the [COLOR=#000000].xsession-errors file after a normal boot:[/COLOR]

```
[COLOR=#000000]Script for ibus started at run_im.[/COLOR]
[COLOR=#000000]Script for auto started at run_im.[/COLOR]
[COLOR=#000000]Script for default started at run_im.
[/COLOR]
```

Edit:
And this is the diff of the run.log between normal boot and startx from terminal with a .xsession file in my users home directory: [https://www.diffchecker.com/3t2zvfqv](https://www.diffchecker.com/3t2zvfqv)
It seems the normal boot uses many more config files.

---

