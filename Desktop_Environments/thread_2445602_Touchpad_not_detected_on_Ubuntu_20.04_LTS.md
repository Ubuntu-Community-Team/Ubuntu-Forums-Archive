---
title: "Touchpad not detected on Ubuntu 20.04 LTS"
date: 2020-06-16
forum: Desktop Environments
---

### Post by dayana-maldonado on 2020-06-16
Hi all,
 
Just bought a Lenovo Ideapad Slim model 1-14ast-05 with Windows 10 installed and touchpad worked ok. 
 
I installed Ubuntu 20.04 for a better use of resources, but it does not detect the touchpad at all.
 

I'm getting this output from dmesg | grep ELAN

[    0.871292] i2c_hid i2c-ELAN0666:00: i2c-ELAN0666:00 supply vdd not found, using dummy regulator
[    0.871324] i2c_hid i2c-ELAN0666:00: i2c-ELAN0666:00 supply vddl not found, using dummy regulator


[B]I have physically disconnected and reconnected the touchpad connector from the motherboard and Ubuntu detects the touchpad correctly, BUT after rebooting it fails to detect it again.
[/B]
**Every time i physically disconnect and reconnect the touchpad from the motherboard its correctly detected by Ubuntu, but after i reboot the laptop the touchpad is not detected**

 

*This is the output from dmesg | grep ELAN after touchpad is detected:*

[ 0.865690] i2c_hid i2c-ELAN0666:00: i2c-ELAN0666:00 supply vdd not found, using dummy regulator
[ 0.865713] i2c_hid i2c-ELAN0666:00: i2c-ELAN0666:00 supply vddl not found, using dummy regulator
[ 0.983421] input: ELAN0666:00 04F3:304B Mouse as /devices/platform/AMD0010:03/i2c-0/i2c-ELAN0666:00/0018:04F3:304B.0001/input/input6
[ 0.983551] input: ELAN0666:00 04F3:304B Touchpad as /devices/platform/AMD0010:03/i2c-0/i2c-ELAN0666:00/0018:04F3:304B.0001/input/input7
[ 0.983657] hid-generic 0018:04F3:304B.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN0666:00 04F3:304B] on i2c-ELAN0666:00
[ 4.523227] input: ELAN0666:00 04F3:304B Mouse as /devices/platform/AMD0010:03/i2c-0/i2c-ELAN0666:00/0018:04F3:304B.0001/input/input10
[ 4.523535] input: ELAN0666:00 04F3:304B Touchpad as /devices/platform/AMD0010:03/i2c-0/i2c-ELAN0666:00/0018:04F3:304B.0001/input/input11
[ 4.523759] hid-multitouch 0018:04F3:304B.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN0666:00 04F3:304B] on i2c-ELAN0666:00
 

*This is the output for sudo libinput list-devices after touchpad is detected:*

Device:           ELAN0666:00 04F3:304B Mouse
Kernel:           /dev/input/event6
Group:            10
Seat:             seat0, default
Capabilities:     pointer
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   *button
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   flat *adaptive
Rotation:         n/a
 
Device:           ELAN0666:00 04F3:304B Touchpad
Kernel:           /dev/input/event7
Group:            10
Seat:             seat0, default
Size:             100x66mm
Capabilities:     pointer gesture
Tap-to-click:     disabled
Tap-and-drag:     enabled
Tap drag lock:    disabled
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *two-finger edge
Click methods:    *button-areas clickfinger
Disable-w-typing: enabled
Accel profiles:   none
Rotation:         n/a
 
*This is the output of xinput list after touchpad is detected:*

&#9121; Virtual core pointer                     id=2 [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer               id=4 [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse               id=10 [slave  pointer  (2)]
&#9116;   &#8627; ELAN0666:00 04F3:304B Mouse              id=13 [slave  pointer  (2)]

&#9116;   &#8627; ELAN0666:00 04F3:304B Touchpad           id=14 [slave  pointer  (2)]
&#9123; Virtual core keyboard                    id=3 [master keyboard (2)]
   &#8627; Virtual core XTEST keyboard              id=5 [slave  keyboard (3)]
   &#8627; Power Button                             id=6 [slave  keyboard (3)]
   &#8627; Video Bus                                id=7 [slave  keyboard (3)]
   &#8627; Power Button                             id=8 [slave  keyboard (3)]
   &#8627; Sleep Button                             id=9 [slave  keyboard (3)]
   &#8627; EasyCamera: EasyCamera                   id=11 [slave  keyboard (3)]
   &#8627; Ideapad extra buttons                    id=12 [slave  keyboard (3)]
   &#8627; AT Translated Set 2 keyboard             id=15 [slave  keyboard (3)]

Any thoughts to fix this issue?

---

