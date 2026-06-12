---
title: "Setting up mouse with many buttons?"
date: 2009-10-16
forum: Desktop Environments
---

### Post by OrangeVixen on 2009-10-16
I have a USB mouse, I think it's from microinv.com (that's according to the label on the bottom), it has 9 buttons, and using xev, the buttons are as follows:

Button1 - standard left button
Button2 - wheel if you press straight down
Button3 - standard right button
Button4 - wheel rolling
Button5 - wheel rolling
Button6 - not reported
Button7 - not reported
Button8 - left side button, wheel press left
Button9 - right side button, wheel press right

Now, I think buttons 6 and 7, *should* be for the wheel press left and right (respectively). But I have no idea how to configure this.

I'm using Ubuntu 9.04 but the USB mouse came from an older Linux computer, does anyone have this mouse and know how to get those last few buttons working?

---

### Post by Vermind on 2009-10-16
You can try gpointing-device-settings [from this ppa]("https://launchpad.net/~sarvatt/+archive/ppa"). You will need libgpds0 and gpointing-device-settings packages.

---

### Post by OrangeVixen on 2009-10-16
Okay, I installed it and ran gpointing-device-settings, but it seems to be a workaround for mice with 2 or so buttons. I have one with **9 buttons**.

I also already looked on the mouse's manufacture website for drivers but none. My model is a PD945P.

Here is my mouse section in xorg.conf:

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
#    Option         "Protocol" "USB"
    Option         "Device" "/dev/psaux"
#    Option         "Device" "/dev/input/mouse1"
    Option         "Buttons" "9"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Note that I have tried the commented out settings already, they all produce the same results.

Is there a particular Protocol setting that I should use?

---

