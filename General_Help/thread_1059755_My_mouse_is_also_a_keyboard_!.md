---
title: "My mouse is also a keyboard ?!?"
date: 2009-02-04
forum: General Help
---

### Post by AJSB on 2009-02-04
I tryed to install a brand new GENIUS ERGO 555 and all standard keys and wheel work but not the extra keys (5) that it's supposed to be available...i try the cat command and this seems the relevant info:

---------------------------------
# cat /proc/bus/input/devices

I: Bus=0003 Vendor=0458 Product=0084 Version=0110
N: Name="Genius ERGO 555"
P: Phys=usb-0000:00:10.3-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:10.3/usb5/5-1/5-1:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=e080ffdf 1cfffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0458 Product=0084 Version=0110
N: Name="Genius ERGO 555"
P: Phys=usb-0000:00:10.3-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:10.3/usb5/5-1/5-1:1.1/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=e080ffdf 1cfffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0458 Product=0084 Version=0110
N: Name="Genius ERGO 555"
P: Phys=usb-0000:00:10.3-1/input2
S: Sysfs=/devices/pci0000:00/0000:00:10.3/usb5/5-1/5-1:1.2/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10


# ./evdev-key-btn-test /dev/input/event5
Supported Keys:
  Key  0x110  (Left Button)
  Key  0x111  (Right Button)
  Key  0x112  (Middle Button)
  Key  0x113  (Side Button)
  Key  0x114  (Extra Button)
Buttons/Keys:   5

Supported Relative axes:
  Relative axis 0x00  (X Axis)
  Relative axis 0x01  (Y Axis)
  Relative axis 0x08  (Vertical Wheel)
bash-3.1# ./evdev-key-btn-test /dev/input/event4
Supported Keys:
  Key  0x01  (Escape)
  Key  0x02  (1)
  Key  0x03  (2)
  Key  0x04  (3)
  Key  0x05  (4)
  Key  0x06  (5)
  Key  0x07  (6)
  Key  0x08  (7)
  Key  0x09  (8)
  Key  0x0a  (9)
  Key  0x0b  (0)
  Key  0x0c  (-)
  Key  0x0d  (=)
  Key  0x0e  (Backspace)
  Key  0x0f  (Tab)
  Key  0x10  (Q)
  Key  0x11  (W)
  Key  0x12  (E)
  Key  0x13  (R)
  Key  0x14  (T)
  Key  0x15  (Y)
  Key  0x16  (U)
  Key  0x17  (I)
  Key  0x18  (O)
  Key  0x19  (P)
  Key  0x1a  ([)
  Key  0x1b  (])
  Key  0x1c  (Enter)
  Key  0x1d  (LH Control)
  Key  0x1e  (A)
  Key  0x1f  (S)
  Key  0x20  (D)
  Key  0x21  (F)
  Key  0x22  (G)
  Key  0x23  (H)
  Key  0x24  (J)
  Key  0x25  (K)
  Key  0x26  (L)
  Key  0x27  (;)
  Key  0x28  (')
  Key  0x29  (`)
  Key  0x2a  (LH Shift)
  Key  0x2b  (\)
  Key  0x2c  (Z)
  Key  0x2d  (X)
  Key  0x2e  (C)
  Key  0x2f  (V)
  Key  0x30  (B)
  Key  0x31  (N)
  Key  0x32  (M)
  Key  0x33  (,)
  Key  0x34  (.)
  Key  0x35  (/)
  Key  0x36  (RH Shift)
  Key  0x37  (*)
  Key  0x38  (LH Alt)
  Key  0x39  (Space)
  Key  0x3a  (CapsLock)
  Key  0x3b  (F1)
  Key  0x3c  (F2)
  Key  0x3d  (F3)
  Key  0x3e  (F4)
  Key  0x3f  (F5)
  Key  0x40  (F6)
  Key  0x41  (F7)
  Key  0x42  (F8)
  Key  0x43  (F9)
  Key  0x44  (F10)
  Key  0x45  (NumLock)
  Key  0x46  (ScrollLock)
  Key  0x47  (KeyPad 7)
  Key  0x48  (KeyPad 8)
  Key  0x49  (Keypad 9)
  Key  0x4a  (KeyPad Minus)
  Key  0x4b  (KeyPad 4)
  Key  0x4c  (KeyPad 5)
  Key  0x4d  (KeyPad 6)
  Key  0x4e  (KeyPad Plus)
  Key  0x4f  (KeyPad 1)
  Key  0x50  (KeyPad 2)
  Key  0x51  (KeyPad 3)
  Key  0x52  (Unknown key)
  Key  0x53  (KeyPad decimal point)
  Key  0x56  (Beats me...)
  Key  0x57  (F11)
  Key  0x58  (F12)
  Key  0x60  (Keypad Enter)
  Key  0x61  (RH Control)
  Key  0x62  (KeyPad Forward Slash)
  Key  0x63  (System Request)
  Key  0x64  (RH Alternate)
  Key  0x66  (Home)
  Key  0x67  (Up)
  Key  0x68  (Page Up)
  Key  0x69  (Left)
  Key  0x6a  (Right)
  Key  0x6b  (End)
  Key  0x6c  (Down)
  Key  0x6d  (Page Down)
  Key  0x6e  (Insert)
  Key  0x6f  (Delete)
  Key  0x77  (Pause)
  Key  0x7d  (LH Meta)
  Key  0x7e  (RH Meta)
  Key  0x7f  (Compose)
Buttons/Keys: 105

Supported Relative axes:
# ./evdev-key-btn-test /dev/input/event3
Supported Keys:
  Key  0x01  (Escape)
  Key  0x02  (1)
  Key  0x03  (2)
  Key  0x04  (3)
  Key  0x05  (4)
  Key  0x06  (5)
  Key  0x07  (6)
  Key  0x08  (7)
  Key  0x09  (8)
  Key  0x0a  (9)
  Key  0x0b  (0)
  Key  0x0c  (-)
  Key  0x0d  (=)
  Key  0x0e  (Backspace)
  Key  0x0f  (Tab)
  Key  0x10  (Q)
  Key  0x11  (W)
  Key  0x12  (E)
  Key  0x13  (R)
  Key  0x14  (T)
  Key  0x15  (Y)
  Key  0x16  (U)
  Key  0x17  (I)
  Key  0x18  (O)
  Key  0x19  (P)
  Key  0x1a  ([)
  Key  0x1b  (])
  Key  0x1c  (Enter)
  Key  0x1d  (LH Control)
  Key  0x1e  (A)
  Key  0x1f  (S)
  Key  0x20  (D)
  Key  0x21  (F)
  Key  0x22  (G)
  Key  0x23  (H)
  Key  0x24  (J)
  Key  0x25  (K)
  Key  0x26  (L)
  Key  0x27  (;)
  Key  0x28  (')
  Key  0x29  (`)
  Key  0x2a  (LH Shift)
  Key  0x2b  (\)
  Key  0x2c  (Z)
  Key  0x2d  (X)
  Key  0x2e  (C)
  Key  0x2f  (V)
  Key  0x30  (B)
  Key  0x31  (N)
  Key  0x32  (M)
  Key  0x33  (,)
  Key  0x34  (.)
  Key  0x35  (/)
  Key  0x36  (RH Shift)
  Key  0x37  (*)
  Key  0x38  (LH Alt)
  Key  0x39  (Space)
  Key  0x3a  (CapsLock)
  Key  0x3b  (F1)
  Key  0x3c  (F2)
  Key  0x3d  (F3)
  Key  0x3e  (F4)
  Key  0x3f  (F5)
  Key  0x40  (F6)
  Key  0x41  (F7)
  Key  0x42  (F8)
  Key  0x43  (F9)
  Key  0x44  (F10)
  Key  0x45  (NumLock)
  Key  0x46  (ScrollLock)
  Key  0x47  (KeyPad 7)
  Key  0x48  (KeyPad 8)
  Key  0x49  (Keypad 9)
  Key  0x4a  (KeyPad Minus)
  Key  0x4b  (KeyPad 4)
  Key  0x4c  (KeyPad 5)
  Key  0x4d  (KeyPad 6)
  Key  0x4e  (KeyPad Plus)
  Key  0x4f  (KeyPad 1)
  Key  0x50  (KeyPad 2)
  Key  0x51  (KeyPad 3)
  Key  0x52  (Unknown key)
  Key  0x53  (KeyPad decimal point)
  Key  0x56  (Beats me...)
  Key  0x57  (F11)
  Key  0x58  (F12)
  Key  0x60  (Keypad Enter)
  Key  0x61  (RH Control)
  Key  0x62  (KeyPad Forward Slash)
  Key  0x63  (System Request)
  Key  0x64  (RH Alternate)
  Key  0x66  (Home)
  Key  0x67  (Up)
  Key  0x68  (Page Up)
  Key  0x69  (Left)
  Key  0x6a  (Right)
  Key  0x6b  (End)
  Key  0x6c  (Down)
  Key  0x6d  (Page Down)
  Key  0x6e  (Insert)
  Key  0x6f  (Delete)
  Key  0x77  (Pause)
  Key  0x7d  (LH Meta)
  Key  0x7e  (RH Meta)
  Key  0x7f  (Compose)
Buttons/Keys: 105

Supported Relative axes:
# 

------------------------------------------------------

so it seems that the extra keys are controlled as a keyboard ?!? if so, how to install this beast ?!? should/can i try sing wine and the CD included to try to set the extra buttons to emulate keyboard keys (it seems that the Win Genius soft let's me do so) ? or maybe use a Win comp to use soft to asign kbd key values (lie "a" "b" "ENTER",etc) to those keys (those assignments will be saved in mouse internal flash memory AFAIK) ?

BTW, i'm, using this to control the standard keys and wheel:

Section "InputDevice"
    Identifier     "Mouse1"
     Driver        "mouse"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7 8 9 10"
Option "SendCoreEvents" "true"
Option "Buttons" "10"
Option          "Protocol"              "ExplorerPS/2"
Option          "Emulate3Buttons"       "false"

EndSection

The total of buttons is actually 12 but two are dedicated to DPI setting and can't be used for anything else even in Window$  "10" or "7" gives same result and also tryed w/o buttonmapping line...in all cases all standard keys and wheel work but not the extra keys....even xev doesn't report them.

TIA,
AJSB

---

