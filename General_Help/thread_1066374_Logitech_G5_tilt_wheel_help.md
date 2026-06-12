---
title: "Logitech G5 tilt wheel help"
date: 2009-02-10
forum: General Help
---

### Post by dhysk on 2009-02-10
I'm running 8.04 just got a new G5 mouse.  Everything works except the tilt wheel.  The forward and back thumb buttons work in Firefox perfectly however the tilt wheel doesn't function.  I tried evdev with little luck however everything i was looking for help was a few years old.  Does anyone know a good way to get it working.  I'd love to get the tilt wheel to flip my desktop.

---

### Post by dhysk on 2009-02-13
Ok.  Finally found the answer.  The old how toos were mostly right for using the evdev driver.  However you have to add the the option "Device" "dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse"  this may be different depending on your setup.

my xorg.conf file looks like this for the "InputeDevide" section.

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "evdev"
    Option	   "CorePointer"
    #Option         "Protocol" "auto"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse"
    Option         "Emulate3Buttons" "false"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

---

### Post by dhysk on 2009-02-13
on another note, it works fine except in games.  The tracking goes to crap 'in game' and it's nearly impossible to predict ware its going.  Anyone have any ideas?

---

### Post by etnlIcarus on 2009-03-13
*bump*

Yesterday I got myself one of [these](http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/3072&cl=au,en).

The tilt-wheel is *kind* of working.

My previous mouse was a [MS Comfort Optical 3000](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=041) so I'm no stranger to the tilt-wheel.

The problem with the logitech is two-fold:

1 - It's not behaving like a tilt-wheel in all apps. For instance, wherever there is a text field, the tilt-wheel moves the *cursor*, rather than pans across the page/field horizontally as it should. In thunar, all the tilt-wheel seems to be doing is changing the selected folder back and forth.

2 - It's exhibiting Windows-like focus behaviour. One of the things that drove me f***ing nuts with XP was having to click in a pane to focus it, before Windows would allow me to scroll that pane - horizontally or vertically.

While vertical scrolling is still behaving in the far-saner *nix way; with the mouse wheel scrolling whichever pane the cursor happens to be hovering over, the tilt-wheel seems to be demanding that a pane currently has focus, before it will allow me to horizontally scroll that pane.

I tried using dhysk's xorg.conf (with "/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse", changed to "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse") and restarting X but the tilt-wheel is still being retarded.

Anyone got any advice?

---

### Post by CK05 on 2009-03-27
Is it possible to have tilt-wheel left minimize apps and titl-wheel right maximize apps? 

That would be great.

---

