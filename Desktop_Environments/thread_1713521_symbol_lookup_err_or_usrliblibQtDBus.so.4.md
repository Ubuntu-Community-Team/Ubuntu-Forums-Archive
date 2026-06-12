---
title: "symbol lookup err or: /usr/lib/libQtDBus.so.4"
date: 2011-03-24
forum: Desktop Environments
---

### Post by shantiq on 2011-03-24
everything going fine and then this morning trying to start 3 programs and this for everyione of them    any ideas?


```
shantiq@shantiq-00000000000000000000000:~$ skype
skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv
shantiq@shantiq-00000000000000000000000:~$ yakuake
yakuake:symbol lookup err or: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv
shantiq@shantiq-00000000000000000000000:~$ vlc
VLC media player 1.1.7 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9d85914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9e304fc] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x9e304fc] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x9d85914] main libvlc error: interface "default" initialization failed
shantiq@shantiq-00000000000000000000000:~$ 
```

---

