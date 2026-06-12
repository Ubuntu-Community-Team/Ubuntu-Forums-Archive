---
title: "xsession errors filled with the same error loop"
date: 2010-05-01
forum: Desktop Environments
---

### Post by nerdy_kid on 2010-05-01
so whenever i try to do something in kde that updates the system config (such as changing icons or changing file associations)  the progress bar will loop forever and this fills my .xsession-errors log:

```

kcmshell(7373) KShortcutsEditorItem::KShortcutsEditorItem: Action without text! "Increase Screen Brightness" 
kcmshell(7373) KShortcutsEditorItem::KShortcutsEditorItem: Action without text! "Decrease Screen Brightness" 
kglobalaccel(6720) KGlobalAccelImpl::x11Event: Got XMappingNotify event
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: 
--------------SNIP-----------------------
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+5" for "amarok" : "rate5"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+A" for "amarok" : "playlist_add"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+S" for "amarok" : "skipTrack"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+V" for "amarok" : "stop_after_current"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Shift+-" for "amarok" : "seek_backward"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Media Play" for "amarok" : "play_pause"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Up" for "kded" : "Increase Screen Brightness"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "F12" for "yakuake" : "toggle-window-state"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey:
Screen Brightness"
-------------SNIP---------------
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Monitor Brightness Down" for "kded" : "Decrease Screen Brightness"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "F12" for "yakuake" : "toggle-window-state"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+R" for "klipper" : "repeat_action"
kglobalaccel(6720) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+X" for "klipper" : "clipboard_action"

kglobalaccel(6720) KGlobalAccelImpl::x11Event: Got XMappingNotify event

kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Volume Mute" for "kmix" : "mute"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(6720) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"

```



it will go on forever.  this does not effect new accounts though.  any ideas? (i am going to remove .kde and see if that helps)

---

### Post by nerdy_kid on 2010-05-01
fixed it...was the .config folder.  leftover from karmic i guess.

---

### Post by Morrighu on 2011-09-14
My log has been looping and filling 600+ GB (not a typo) of disk space.  I'm going to try moving the .config and let the OS rebuild it, if it is still needed and see if that doesn't fix the issue.

---

