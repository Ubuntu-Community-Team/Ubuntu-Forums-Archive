---
title: "Switch of the middle button of the mouse"
date: 2010-10-26
forum: Desktop Environments
---

### Post by Ewgenijkkg on 2010-10-26
Hello, guys. I am getting really annoyed by the feature of copy/paste with the mouse wheel. I am programming, I am scrolling up and down, and after that I have a lot of code pasted on differented places :))) I want to switch of this button functionality. I know, that that goes by switching the button mappings. On my Debian Lenny installation I just put the following two lines in the input device section of /etc/X11/xorg.conf:
 
Option     "ZAxisMapping" "4 5"
Option     "ButtonMapping" "1 9 3 4 5"
 
That solved the problem. In my current Ubuntu Maverick installation, I do not have an InputDevice-Section. I tried xinput, but xinput list writes a quite strange output:
 
Virtual core pointer                     id=2 [master pointer  (3)]
   Virtual core XTEST pointer               id=4 [slave  pointer  (2)]
   HID 04d9:1400                            id=9 [slave  pointer  (2)]
Virtual core keyboard                    id=3 [master keyboard (2)]
   Virtual core XTEST keyboard              id=5 [slave  keyboard (3)]
   Power Button                             id=6 [slave  keyboard (3)]
   Power Button                             id=7 [slave  keyboard (3)]
   HID 04d9:1400                            id=8 [slave  keyboard (3)]
 
I tried several mappings on the numbers 2, 4 and 9 of the list above. But that does not work :(((

---

### Post by Ewgenijkkg on 2010-10-29
OK, I was told a good solution which worked. Just added the following section to my /etc/X11/xorg.conf
 
Section "InputClass"
    Identifier   "DisableWheelButton"
    MatchIsPointer "on"
    Option "ButtonMapping" "1 9 3 4 5"
EndSection

Here is the link to the thread where my question was answered:
 
[http://lists.freedesktop.org/archives/xorg/2010-October/051578.html](http://lists.freedesktop.org/archives/xorg/2010-October/051578.html)

---

