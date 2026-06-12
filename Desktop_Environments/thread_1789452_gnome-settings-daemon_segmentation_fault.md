---
title: "gnome-settings-daemon segmentation fault"
date: 2011-06-23
forum: Desktop Environments
---

### Post by telseth on 2011-06-23
I'm having trouble with gnome-settings-daemon in gnome 3.  I can start it with sudo and get my pretty theme, but under my normal user it segfaults.


blah@heymon ~/.config/gtk-3.0 $ gnome-settings-daemon 

(gnome-settings-daemon:3098): Gtk-WARNING **: Could not load named theme "Adwaita": File doesn't exist: /usr/share/themes/Adwaita/gtk-3.0/-gtk-gradient (linear,
                                 left top, left bottom,
                                 from (shade (@theme_bg_color, 0.56)),
                                 to (shade (@theme_bg_color, 0.83))) 1 stretch

** (gnome-settings-daemon:3098): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'

** (gnome-settings-daemon:3098): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:3098): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

** (gnome-settings-daemon:3098): WARNING **: Name taken or bus went away - shutting down
Segmentation fault

---

### Post by telseth on 2011-06-23
here is the --debug information

blah@heymon ~/.config/gtk-3.0 $ gnome-settings-daemon --debug

(gnome-settings-daemon:3119): Gtk-WARNING **: Could not load named theme "Adwaita": File doesn't exist: /usr/share/themes/Adwaita/gtk-3.0/-gtk-gradient (linear,
                                 left top, left bottom,
                                 from (shade (@theme_bg_color, 0.56)),
                                 to (shade (@theme_bg_color, 0.83))) 1 stretch
** (gnome-settings-daemon:3119): DEBUG: Starting settings manager
** (gnome-settings-daemon:3119): DEBUG: Loading settings plugins from dir: /usr/lib/gnome-settings-daemon-3.0/
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/media-keys.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Media keys' file='/usr/lib/gnome-settings-daemon-3.0/media-keys.gnome-settings-plugin' location='media-keys'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/xrandr.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='XRandR' file='/usr/lib/gnome-settings-daemon-3.0/xrandr.gnome-settings-plugin' location='xrandr'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/clipboard.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Clipboard' file='/usr/lib/gnome-settings-daemon-3.0/clipboard.gnome-settings-plugin' location='clipboard'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/housekeeping.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Housekeeping' file='/usr/lib/gnome-settings-daemon-3.0/housekeeping.gnome-settings-plugin' location='housekeeping'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/a11y-keyboard.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Accessibility Keyboard' file='/usr/lib/gnome-settings-daemon-3.0/a11y-keyboard.gnome-settings-plugin' location='a11y-keyboard'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/sound.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Sound' file='/usr/lib/gnome-settings-daemon-3.0/sound.gnome-settings-plugin' location='sound'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/keybindings.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Keybindings' file='/usr/lib/gnome-settings-daemon-3.0/keybindings.gnome-settings-plugin' location='keybindings'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/mouse.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Mouse' file='/usr/lib/gnome-settings-daemon-3.0/mouse.gnome-settings-plugin' location='mouse'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/background.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Background' file='/usr/lib/gnome-settings-daemon-3.0/background.gnome-settings-plugin' location='background'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/xsettings.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='X Settings' file='/usr/lib/gnome-settings-daemon-3.0/xsettings.gnome-settings-plugin' location='xsettings'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/gconf.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='GConf' file='/usr/lib/gnome-settings-daemon-3.0/gconf.gnome-settings-plugin' location='gconf'

** (gnome-settings-daemon:3119): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/wacom.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Wacom' file='/usr/lib/gnome-settings-daemon-3.0/wacom.gnome-settings-plugin' location='wacom'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/automount.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Automount' file='/usr/lib/gnome-settings-daemon-3.0/automount.gnome-settings-plugin' location='automount'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/a11y-settings.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Accessibility settings' file='/usr/lib/gnome-settings-daemon-3.0/a11y-settings.gnome-settings-plugin' location='a11y-settings'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/keyboard.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Keyboard' file='/usr/lib/gnome-settings-daemon-3.0/keyboard.gnome-settings-plugin' location='keyboard'
** (gnome-settings-daemon:3119): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-3.0/print-notifications.gnome-settings-plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsPluginInfo: name='Print-notifications' file='/usr/lib/gnome-settings-daemon-3.0/print-notifications.gnome-settings-plugin' location='print-notifications'
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x82848a0 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libxsettings.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GnomeXSettingsPlugin
** (gnome-settings-daemon:3119): DEBUG: GnomeXSettingsPlugin initializing
** (gnome-settings-daemon:3119): DEBUG: Activating xsettings plugin
** (gnome-settings-daemon:3119): DEBUG: Starting xsettings manager

** (gnome-settings-daemon:3119): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:3119): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated xsettings
** (gnome-settings-daemon:3119): DEBUG: Plugin xsettings: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x8284850 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libxrandr.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdXrandrPlugin
(gnome-settings-daemon:3119): xrandr-plugin-DEBUG: GsdXrandrPlugin initializing
(gnome-settings-daemon:3119): xrandr-plugin-DEBUG: Activating xrandr plugin
(gnome-settings-daemon:3119): xrandr-plugin-DEBUG: Starting xrandr manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated xrandr
** (gnome-settings-daemon:3119): DEBUG: Plugin xrandr: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x826d7b8 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libsound.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdSoundPlugin
(gnome-settings-daemon:3119): sound-plugin-DEBUG: GsdSoundPlugin initializing
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Activating sound plugin
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Starting sound manager
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Registering directory monitor for /home/troy/.local/share/sounds
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Registering directory monitor for /usr/share/gnome-shell
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Registering directory monitor for /usr/share/gnome
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Registering directory monitor for /usr/local/share/
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Registering directory monitor for /usr/share/
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated sound
** (gnome-settings-daemon:3119): DEBUG: Plugin sound: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x826d740 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libkeyboard.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdKeyboardPlugin
(gnome-settings-daemon:3119): keyboard-plugin-DEBUG: GsdKeyboardPlugin initializing
(gnome-settings-daemon:3119): keyboard-plugin-DEBUG: Activating keyboard plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated keyboard
** (gnome-settings-daemon:3119): DEBUG: Plugin keyboard: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x8281278 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libwacom.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdWacomPlugin
(gnome-settings-daemon:3119): wacom-plugin-DEBUG: GsdWacomPlugin initializing
(gnome-settings-daemon:3119): wacom-plugin-DEBUG: Activating wacom plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated wacom
** (gnome-settings-daemon:3119): DEBUG: Plugin wacom: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x826d6f0 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/liba11y-settings.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdA11ySettingsPlugin
(gnome-settings-daemon:3119): ally-settings-plugin-DEBUG: GsdA11ySettingsPlugin initializing
(gnome-settings-daemon:3119): ally-settings-plugin-DEBUG: Activating a11y-settings plugin
(gnome-settings-daemon:3119): ally-settings-plugin-DEBUG: Starting a11y_settings manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated a11y-settings
** (gnome-settings-daemon:3119): DEBUG: Plugin a11y-settings: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x8282ec8 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libmouse.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdMousePlugin
(gnome-settings-daemon:3119): mouse-plugin-DEBUG: GsdMousePlugin initializing
(gnome-settings-daemon:3119): mouse-plugin-DEBUG: Activating mouse plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated mouse
** (gnome-settings-daemon:3119): DEBUG: Plugin mouse: active
** (gnome-settings-daemon:3119): DEBUG: Plugin a11y-keyboard: inactive
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x8282e50 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libkeybindings.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdKeybindingsPlugin
(gnome-settings-daemon:3119): keybindings-plugin-DEBUG: GsdKeybindingsPlugin initializing
(gnome-settings-daemon:3119): keybindings-plugin-DEBUG: Activating keybindings plugin
(gnome-settings-daemon:3119): keybindings-plugin-DEBUG: Starting keybindings manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated keybindings
** (gnome-settings-daemon:3119): DEBUG: Plugin keybindings: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x8282f68 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libautomount.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdAutomountPlugin
** (gnome-settings-daemon:3119): DEBUG: Automount plugin initializing
** (gnome-settings-daemon:3119): DEBUG: Activating automount plugin
** (gnome-settings-daemon:3119): DEBUG: Starting automounting manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated automount
** (gnome-settings-daemon:3119): DEBUG: Plugin automount: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x828c340 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libbackground.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdBackgroundPlugin
** (gnome-settings-daemon:3119): DEBUG: GsdBackgroundPlugin initializing
** (gnome-settings-daemon:3119): DEBUG: Activating background plugin
** (gnome-settings-daemon:3119): DEBUG: Starting background manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated background
** (gnome-settings-daemon:3119): DEBUG: Plugin background: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x828c540 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libmedia-keys.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdMediaKeysPlugin
(gnome-settings-daemon:3119): media-keys-plugin-DEBUG: GsdMediaKeysPlugin initializing
(gnome-settings-daemon:3119): media-keys-plugin-DEBUG: Activating media_keys plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated media-keys
** (gnome-settings-daemon:3119): DEBUG: Plugin media-keys: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x828c590 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libprint-notifications.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdPrintNotificationsPlugin
(gnome-settings-daemon:3119): print-notifications-plugin-DEBUG: Activating print-notifications plugin
(gnome-settings-daemon:3119): print-notifications-plugin-DEBUG: Starting print-notifications manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated print-notifications
** (gnome-settings-daemon:3119): DEBUG: Plugin print-notifications: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x828c628 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libclipboard.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdClipboardPlugin
(gnome-settings-daemon:3119): clipboard-plugin-DEBUG: GsdClipboardPlugin initializing
(gnome-settings-daemon:3119): clipboard-plugin-DEBUG: Activating clipboard plugin
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated clipboard
** (gnome-settings-daemon:3119): DEBUG: Plugin clipboard: active
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsModule 0x828c650 initialising
** (gnome-settings-daemon:3119): DEBUG: Loading /usr/lib/gnome-settings-daemon-3.0/libhousekeeping.so
** (gnome-settings-daemon:3119): DEBUG: Creating object of type GsdHousekeepingPlugin
(gnome-settings-daemon:3119): housekeeping-plugin-DEBUG: GsdHousekeepingPlugin initializing
(gnome-settings-daemon:3119): housekeeping-plugin-DEBUG: Activating housekeeping plugin
(gnome-settings-daemon:3119): housekeeping-plugin-DEBUG: Starting housekeeping manager
(gnome-settings-daemon:3119): housekeeping-plugin-DEBUG: housekeeping: will tidy up in 2 minutes
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-activated housekeeping
** (gnome-settings-daemon:3119): DEBUG: Plugin housekeeping: active
** (gnome-settings-daemon:3119): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session2

** (gnome-settings-daemon:3119): WARNING **: Name taken or bus went away - shutting down
** (gnome-settings-daemon:3119): DEBUG: ScreenSaver name appeared
** (gnome-settings-daemon:3119): DEBUG: Shutting down
** (gnome-settings-daemon:3119): DEBUG: Stopping settings manager
** (gnome-settings-daemon:3119): DEBUG: Deactivating xsettings plugin
** (gnome-settings-daemon:3119): DEBUG: Stopping xsettings manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated xsettings
** (gnome-settings-daemon:3119): DEBUG: Unref plugin X Settings
** (gnome-settings-daemon:3119): DEBUG: GnomeXSettingsPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libxsettings.so
(gnome-settings-daemon:3119): xrandr-plugin-DEBUG: Deactivating xrandr plugin
(gnome-settings-daemon:3119): xrandr-plugin-DEBUG: Stopping xrandr manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated xrandr
** (gnome-settings-daemon:3119): DEBUG: Unref plugin XRandR
(gnome-settings-daemon:3119): xrandr-plugin-DEBUG: GsdXrandrPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libxrandr.so
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Deactivating sound plugin
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Stopping sound manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated sound
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Sound
(gnome-settings-daemon:3119): sound-plugin-DEBUG: GsdSoundPlugin finalizing
(gnome-settings-daemon:3119): sound-plugin-DEBUG: Stopping sound manager
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libsound.so
(gnome-settings-daemon:3119): keyboard-plugin-DEBUG: Deactivating keyboard plugin
(gnome-settings-daemon:3119): keyboard-plugin-DEBUG: Stopping keyboard manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated keyboard
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Keyboard
(gnome-settings-daemon:3119): keyboard-plugin-DEBUG: GsdKeyboardPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libkeyboard.so
(gnome-settings-daemon:3119): wacom-plugin-DEBUG: Deactivating wacom plugin
(gnome-settings-daemon:3119): wacom-plugin-DEBUG: Stopping wacom manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated wacom
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Wacom
(gnome-settings-daemon:3119): wacom-plugin-DEBUG: GsdWacomPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libwacom.so
(gnome-settings-daemon:3119): ally-settings-plugin-DEBUG: Deactivating a11y-settings plugin
(gnome-settings-daemon:3119): ally-settings-plugin-DEBUG: Stopping a11y_settings manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated a11y-settings
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Accessibility settings
(gnome-settings-daemon:3119): ally-settings-plugin-DEBUG: GsdA11ySettingsPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/liba11y-settings.so
(gnome-settings-daemon:3119): mouse-plugin-DEBUG: Deactivating mouse plugin
(gnome-settings-daemon:3119): mouse-plugin-DEBUG: Stopping mouse manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated mouse
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Mouse
(gnome-settings-daemon:3119): mouse-plugin-DEBUG: GsdMousePlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libmouse.so
(gnome-settings-daemon:3119): keybindings-plugin-DEBUG: Deactivating keybindings plugin
(gnome-settings-daemon:3119): keybindings-plugin-DEBUG: Stopping keybindings manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated keybindings
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Keybindings
(gnome-settings-daemon:3119): keybindings-plugin-DEBUG: GsdKeybindingsPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libkeybindings.so
** (gnome-settings-daemon:3119): DEBUG: Deactivating automount plugin
** (gnome-settings-daemon:3119): DEBUG: Stopping automounting manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated automount
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Automount
** (gnome-settings-daemon:3119): DEBUG: Automount plugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libautomount.so
** (gnome-settings-daemon:3119): DEBUG: Deactivating background plugin
** (gnome-settings-daemon:3119): DEBUG: Stopping background manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated background
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Background
** (gnome-settings-daemon:3119): DEBUG: GsdBackgroundPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libbackground.so
(gnome-settings-daemon:3119): media-keys-plugin-DEBUG: Deactivating media_keys plugin
(gnome-settings-daemon:3119): media-keys-plugin-DEBUG: Stopping media_keys manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated media-keys
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Media keys
(gnome-settings-daemon:3119): media-keys-plugin-DEBUG: GsdMediaKeysPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libmedia-keys.so
(gnome-settings-daemon:3119): print-notifications-plugin-DEBUG: Deactivating print_notifications plugin
(gnome-settings-daemon:3119): print-notifications-plugin-DEBUG: Stopping print-notifications manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated print-notifications
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Print-notifications
(gnome-settings-daemon:3119): print-notifications-plugin-DEBUG: GsdPrintNotificationsPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libprint-notifications.so
(gnome-settings-daemon:3119): clipboard-plugin-DEBUG: Deactivating clipboard plugin
(gnome-settings-daemon:3119): clipboard-plugin-DEBUG: Stopping clipboard manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated clipboard
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Clipboard
(gnome-settings-daemon:3119): clipboard-plugin-DEBUG: GsdClipboardPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libclipboard.so
(gnome-settings-daemon:3119): housekeeping-plugin-DEBUG: Deactivating housekeeping plugin
(gnome-settings-daemon:3119): housekeeping-plugin-DEBUG: Stopping housekeeping manager
** (gnome-settings-daemon:3119): DEBUG: GnomeSettingsManager: emitting plugin-deactivated housekeeping
** (gnome-settings-daemon:3119): DEBUG: Unref plugin Housekeeping
(gnome-settings-daemon:3119): housekeeping-plugin-DEBUG: GsdHousekeepingPlugin finalizing
** (gnome-settings-daemon:3119): DEBUG: Unloading /usr/lib/gnome-settings-daemon-3.0/libhousekeeping.so
** (gnome-settings-daemon:3119): DEBUG: SettingsDaemon finished
Segmentation fault

---

### Post by 23dornot23d on 2011-06-23
> 
(gnome-settings-daemon:309:cool:: Gtk-WARNING **: [COLOR=Red]**Could not load named theme "Adwaita": File doesn't exist:**[/COLOR]
The thing to do is make sure the Adwaita theme is in usr/share/themes

[IMG]http://img35.imageshack.us/img35/1498/themeej.jpg[/IMG]



Next thing is to add it ..... this is the only link I could find there may be a newer one ...... it came

from this thread as I had the problem a couple of months back  ..... [COLOR=Red]_***[LINK]("http://ubuntuforums.org/showpost.php?p=10655293&postcount=86")***_[/COLOR]

[IMG]http://ubuntuforums.org/images/attach/bz2.gif[/IMG] [Adwaita.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=188533&d=1302319605") (269.0 KB)


[B]and as I was told ....
You should be able to just extract the Adwaita folder to ~/.themes/
that's for it to be picked up locally ...[/B]

Globally you would need to be root and add it into usr/shere/themes/
where it will be available for everyone on your system .....

Then most of the errors will go away ....

---

### Post by telseth on 2011-06-23
I do have it, and i also made symlinks to all of the themes in ~/.themes/ still seg faults. (notice the ugly...)

[IMG]http://i.imgur.com/CNvCf.png[/IMG]

---

### Post by 23dornot23d on 2011-06-23
Put it in your local home folder too .... just to see if it changes the situation.

[home]/.themes/



Unless part of its missing to do with gtk-3.0

could check this exists too ... maybe its only part of it you have installed  ..... 

Just lookng at the first error ....

> 
(gnome-settings-daemon:3119): Gtk-WARNING **: Could not load named theme "Adwaita": File doesn't exist:

/usr/share/themes/Adwaita/gtk-3.0/-gtk-gradient


---

### Post by telseth on 2011-06-23
It did not help, however, I am wondering if it should be loading one of the css files.  

> File doesn't exist: /usr/share/themes/Adwaita/gtk-3.0/-gtk-gradient 

Shouldn't that be gtk-3.0/gtk.css ?

Also, are these an issue? 
> Unable to start xsettings manager: Could not initialize xsettings manager.
> Name taken or bus went away - shutting down

---

### Post by 23dornot23d on 2011-06-23
How did you install it I am presuming that this is gnome-shell ....

There is a Dvd that has just been made for Gnome Shell and its fully up to date

Check this link out ..... its a quick way to get upto speed with it ....

[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

or is it UNITY .....

maybe re-installing the Gnome-Themes-Standard through synaptic would sort it out ...

---

### Post by telseth on 2011-06-23
I'm hoping not to have to install again, and no, I installed using the ppa.

Here is more information though, dmesg gives me this:

> [ 1566.199658] gnome-settings-[3485]: segfault at b4e22a70 ip b4e22a70 sp bfb9429c error 14 in libdbus-1.so.3.5.4[b4e56000+3b000]

---

### Post by 23dornot23d on 2011-06-23
If it was me .....

this is what I would try .....

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update

( these first 3 commands just update lists and add another package manager that handles dependencies )

but show me the list of things it wants to install ...... first .....
would like to look through the list first ...... **so answer no** 
when it asks you after this last command.

**sudo aptitude safe-upgrade**

***[COLOR=Red]and just cut and paste what it advises here please[/COLOR]***
____________________________________

> 
 I can start it with sudo and get my pretty theme, but under my normal user it segfaults.
Just a thought ...... ( might be a permissions problem )

Just read this again ..... have you got read write privileges to the themes file or is there a lock on it ...
in your user ......  [home]/.themes
is it owned by root ?

[B]If not carry on with what I initially asked for ...

_*( also which ppa did you use ... do you have a link to what you used .... or the instructions you followed )*_
[/B]

---

### Post by telseth on 2011-06-23
sudo aptitude safe-upgrade
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.


--- and the prettiness doesn't show with the sudo I guess (just tried it again) but it doesn't segfault either.

Permissions are fine, they are -rw-r--r-

Looks like re-installation...

---

### Post by 23dornot23d on 2011-06-23
Ok well the 3.1 Gnome-Shell installation is right uptodate as of last night ....

and I am currently helping seed the files so if you want that one its the best I know
is available at this moment in time ...... in this link  .... use transmission or qbittorrent ...

This is still in development .... so please use the thread link below to report any problems

[IMG]http://ubuntuforums.org/images/attach/gz.gif[/IMG]     [gNatty Gnome i686 v3.1 Live.torrent.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=195728&d=1308755839") (21.2 KB, 3 views)


[http://ubuntuforums.org/showthread.php?p=10973639#post10973639](http://ubuntuforums.org/showthread.php?p=10973639#post10973639)

---

