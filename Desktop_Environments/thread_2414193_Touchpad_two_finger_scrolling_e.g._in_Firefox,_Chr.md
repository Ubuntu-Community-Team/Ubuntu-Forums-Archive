---
title: "Touchpad two finger scrolling e.g. in Firefox, Chromium or Nautilus is to fast"
date: 2019-03-07
forum: Desktop Environments
---

### Post by migoelo on 2019-03-07
Hi all,

with my DELL XPS 15 9560 laptop with a 4K display I have a problem with the two finger scrolling e.g. in Firefox, Chromium or Nautlius. Compared to Windows 10 it is to fast. Is it possible to adjust this? In the settings it is only possible to change the speed of the mouse pointer. I'm working here with a fresh 18.04.2 installation with a standard 200% display scaling regarding the 4K resolution. Thanks

Michael

---

### Post by Rodney9 on 2019-03-07
Go to Settings / Devices / Mouse and Touchpad

---

### Post by migoelo on 2019-03-07
In the settings I have only the possibility to change the speed of the mouse pointer for the mouse and the touchpad, but not for the two finger swip.

---

### Post by Holger_Gehrke on 2019-03-07
There is a command line tool named synclient (the name derives from the fact that it was originally developed for touch pads made by Synaptics, but nowadays it also works for a lot of others). It's part of the package 'xserver-xorg-input-synaptics' (I do believe it's installed by default, try 'apt show xserver-xorg-input-synaptics'. By entering ```
synclient VertScroll=200
```you set it to "200 Units of finger motion for 1 Unit of scrolling". The default value is 68, larger number slow down the scrolling and lower numbers speed it up. There are a lot of other values you can change, just enter 'synclient' without any parameters to see a list of names and current values.

Holger

---

### Post by migoelo on 2019-03-08
After the installation to your proposal the keyboard has stopped to work. A login with the wayland environment has showed no settings for synclient. I believe the Ubuntu standard installation is using libinput and not the synaptic driver. Any other thoughts?

---

### Post by Holger_Gehrke on 2019-03-08
You could try 'xinput', another command line tool to list input device and get or set their properties. 'xinput --list' in a terminal will list all input devices. You can get a list of all the properties of a device with 'xinput --get-properties **name-or-id-of-device**' (replace the bold part with the id or name of the device from the output of 'xinput --list'; if you use the name it will probably be necessary to enclose it in quotes because of the spaces in the name). With 'xinput --set-property name-or-id-of-device **name-of-property** **new-value-for-property**'. On my system (XUbuntu 18.04, both libinput and synaptics installed; I'm not certain, but I do think libinput acts as an abstraction layer on top of whatever actually "talks" to the hardware ...) I get "ETPS/2 Elantech Touchpad" as one off the devices and one of the properties for this device is "Synaptics Scrolling Distance"  with two values (for vertical and horizontal scrolling).

Holger

---

### Post by migoelo on 2019-03-08
xinput --list

```
SynPS/2 Synaptics TouchPad                  id=18    [slave  pointer  (2)]
```

xinput list-props 18

```
Device 'SynPS/2 Synaptics TouchPad':    Device Enabled (147):    1
    Coordinate Transformation Matrix (149):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Tapping Enabled (307):    1
    libinput Tapping Enabled Default (308):    0
    libinput Tapping Drag Enabled (309):    1
    libinput Tapping Drag Enabled Default (310):    1
    libinput Tapping Drag Lock Enabled (311):    0
    libinput Tapping Drag Lock Enabled Default (312):    0
    libinput Tapping Button Mapping Enabled (313):    1, 0
    libinput Tapping Button Mapping Default (314):    1, 0
    libinput Natural Scrolling Enabled (285):    1
    libinput Natural Scrolling Enabled Default (286):    0
    libinput Disable While Typing Enabled (315):    1
    libinput Disable While Typing Enabled Default (316):    1
    libinput Scroll Methods Available (287):    1, 1, 0
    libinput Scroll Method Enabled (288):    1, 0, 0
    libinput Scroll Method Enabled Default (289):    1, 0, 0
    libinput Click Methods Available (317):    1, 1
    libinput Click Method Enabled (318):    0, 1
    libinput Click Method Enabled Default (319):    1, 0
    libinput Middle Emulation Enabled (292):    0
    libinput Middle Emulation Enabled Default (293):    0
    libinput Accel Speed (294):    0.503597
    libinput Accel Speed Default (295):    0.000000
    libinput Left Handed Enabled (299):    0
    libinput Left Handed Enabled Default (300):    0
    libinput Send Events Modes Available (270):    1, 1
    libinput Send Events Mode Enabled (271):    0, 0
    libinput Send Events Mode Enabled Default (272):    0, 0
    Device Node (273):    "/dev/input/event5"
    Device Product ID (274):    2, 7
    libinput Drag Lock Buttons (301):    <no items>
    libinput Horizontal Scroll Enabled (302):    1
```

What I know is, (294) is for the speed of the mouse pointer, but is here also a parameter for the two finger swip speed. If yes, how can I change this (permanently)?

---

### Post by Holger_Gehrke on 2019-03-08
There' no property in that list that seems a likely candidate to do what you want. Which doesn't really surprise me since libinput is meant to be very basic, supporting only what **every** input device of a given type supports. Some searching and reading brought me to [this discussion on Ask Ubuntu]("https://askubuntu.com/questions/1031940/how-to-switch-from-libinput-to-synaptics-in-ubuntu-18-04"), where somebody who was not happy with the lack of options in libinput wanted the synaptics driver back. If you go that route, you'll probably have to create one or more configuration files in /etc/X11/xorg.conf.d/ where you could set some parameters permanently. Otherwise you would set up your DE to execute 'xinput --set-properties' with the right device, property name and value on start up.

Holger

---

