---
title: "Connecting go gnome via XDCMP hangs"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Weisshaupt on 2006-09-25
I've set up my Ubuntu box to accept incoming XDCMP requests. I manage to log on using sessions other than gnome, such as PWM. But when I select the gnome session, the session never gets to the splash screen, showing the different subsystems starting.

I'm using XMing and Cygwin/X from a windows box on the local network. The weird thing is that I'm able to log on via XDCMP locally on the Ubuntu box, using gnome.

Any thoughts on this? The XMing log follows:
```
Welcome to the Xming X Server
Vendor: The Xming Project
Release: 6.9.0.15
Contact: colin at StraightRunning dot com

XdmcpRegisterConnection: newAddress 192.168.0.197
glWinInitVisuals:1509: glWinInitVisuals
init_visuals:1055: init_visuals
glWinScreenProbe:1388: glWinScreenProbe
fixup_visuals:1301: fixup_visuals
init_screen_visuals:1334: init_screen_visuals
(--) Setting autorepeat to delay=250, rate=31
(--) winConfigKeyboard - Layout: "0000041D" (0000041d) 
(--) Using preset keyboard for "Swedish (Sweden)" (41d), type "4"
(--) 3 mouse buttons found
Could not init font path element C:\Program\Xming/fonts/TTF/, removing from list!
Could not init font path element C:\Program\Xming/fonts/Type1/, removing from list!
Could not init font path element C:\Program\Xming/fonts/CID/, removing from list!
Could not init font path element C:\Program\Xming/fonts/75dpi/, removing from list!
Could not init font path element C:\Program\Xming/fonts/100dpi/, removing from list!
Could not init font path element C:\Program Files\Xming\fonts\cyrillic, removing from list!
Could not init font path element C:\WINDOWS\Fonts, removing from list!
winProcEstablishConnection - Hello
winProcEstablishConnection - Clipboard is not enabled, returning.
winProcQueryTree - Clipboard is not enabled, returning.
```

---

### Post by Weisshaupt on 2006-09-25
Just a quick reply to this. I'm able to log on to a gnome session if I turn off the firewall of the computer I connect with.
It sounds weird that I'm able to log on using other sessions with other window managers, but gnome requires that I open up ports on the client. Does anyone know which ports I need to keep open in order to log on with a gnome session using XDCMP?

---

### Post by airtonix on 2006-11-02
isnt it 177 udp?

you can find out which ports are being attempted with jnettop....

```

sudo apt-get install jnettop

```

---

