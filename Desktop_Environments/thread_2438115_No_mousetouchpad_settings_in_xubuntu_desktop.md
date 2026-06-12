---
title: "No mouse/touchpad settings in xubuntu desktop"
date: 2020-03-06
forum: Desktop Environments
---

### Post by freonpsandoz on 2020-03-06
I installed xubuntu desktop for RDP because I couldn't get the default desktop to work with it. When I click on mouse/touchpad settings in an RDP environment, nothing happens. If I do it from the general settings window, a circle cursor is displayed, which I guess means it's trying to open those settings. I want to swap left/right buttons. Any ideas? Can I change mouse settings from the terminal? Thanks.

---

### Post by Holger_Gehrke on 2020-03-06
You could try to run 'xfce4-mouse-settings' from a terminal. This is the program that should run when you try to open those settings from the menu. It probably won't run that way either, but the output in the terminal will give you some idea of what is wrong.

If you just want to swap the mouse buttons, 'xinput' should be able to do that. 'xinput list' will give you a list of connected input devices including id and name. 'xinput set-button-map device-name map-button-1 map-button-2 map-button-3 ...' will remap buttons. Example:
```

xinput set-button-map 'Logitech USB-PS/2 Optical Mouse' 3 2 1

```
would map the first button to act as the third and the third to acts as the first for the mouse connected to my machine.

Holger

---

### Post by freonpsandoz on 2020-03-06
> **Holger_Gehrke said:**
> You could try to run 'xfce4-mouse-settings' from a terminal. This is the program that should run when you try to open those settings from the menu. It probably won't run that way either, but the output in the terminal will give you some idea of what is wrong.
Holger

When I run that command, I get the following errors:

Xlib:  extension "XInputExtension" missing on display ":10.0".

(xfce4-mouse-settings:11920): xfce4-mouse-settings-CRITICAL **: XI is not present.

(I have since created a systemd job to swap buttons on startup; I'm now just trying to find out why the mouse/touchpad settings dialog doesn't open.)

Thanks.

---

