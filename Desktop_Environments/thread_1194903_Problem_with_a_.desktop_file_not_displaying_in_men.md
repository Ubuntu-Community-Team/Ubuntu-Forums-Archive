---
title: "Problem with a .desktop file not displaying in menus."
date: 2009-06-23
forum: Desktop Environments
---

### Post by laeg_ on 2009-06-23
I have the following pidgin.desktop file in /usr/share/applications: 
```

[Desktop Entry]
Encoding=UTF-8
Name=Pidgin Internet Messenger
GenericName=Internet Messenger
Comment=Send instant messages over multiple protocols
Exec=pidgin
Icon=pidgin
StartupNotify=true
Terminal=false
Type=Application
Categories=Network;InstantMessaging;
X-Ubuntu-Gettext-Domain=pidgin
X-Ubuntu-Gettext-Domain=pidgin
```

but it does not display the shortcut in applications >> internet menu. -

From a previous install in edit menus I had unchecked pidgin and also deleted it but now it's not there so I don't have the option to check it.

The problem stems from when in 8.10 I wanted a newer Pidgin version than the ubuntu repos so I compiled the source and left the synaptic version on, no probolems there and I could access it from the menu.

Since upgrading to 9.04 pidgin stopped working so I re-installed the synaptic version, updated with the Pidgin repo and did a make uninstall on the old source.

How can I remedy this?

---

