---
title: "Synergy client can't connect"
date: 2009-02-16
forum: General Help
---

### Post by ba0bab on 2009-02-16
Hi,

I found out about the app Quicksynergy using synergy. I can't make it work. 

Under "share" I place my clients name and start the server. 

On my client, under"use", I tell it to connect to my host's internal IP-adress (found via ifconfig).

It doesn't work. when I start synergy via the terminal I get this message on the client side:

```
DEBUG: CXWindowsScreen.cpp,841: XOpenDisplay(":0.0")
DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00000000
DEBUG: CXWindowsScreen.cpp,111: screen shape: 0,0 3200x1200 (xinerama)
DEBUG: CXWindowsScreen.cpp,112: window is 0x04600004
DEBUG: CScreen.cpp,38: opened display
NOTE: synergyc.cpp,330: started client
WARNING: synergyc.cpp,265: failed to connect to server: Connection refused
DEBUG: synergyc.cpp,237: retry in 1 seconds
WARNING: synergyc.cpp,265: failed to connect to server: Connection refused
DEBUG: synergyc.cpp,237: retry in 3 seconds
```

The host side seems okay. Can somebody help me?

thanks!

---

### Post by Phlee on 2009-02-16
Do you have any firewalls getting in the way?

---

### Post by ba0bab on 2009-02-17
Nope - I have Firestarter installed, but it's not running. I don't think there is anything running in the background, like iptables or something.

---

