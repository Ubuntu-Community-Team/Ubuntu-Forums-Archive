---
title: "Mouse middle button configure"
date: 2011-03-15
forum: Desktop Environments
---

### Post by runeh76 on 2011-03-15
Hi guys!

How to set internet page action *refresh* to middle mouse button?

```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; **Logitech USB Laser Mouse**                	id=8	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; IR-receiver inside an USB DVB receiver  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

Middle mouse button click:
```
xinput test 8
button press 2
button release 2
```

xorg.conf
```
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

---

### Post by XsheepX on 2011-03-15
Pretty sure that would have to be done by configuring your web browser to do so, not your OS.

---

### Post by runeh76 on 2011-03-15
Hi, can u say how to configure Chromium-browser?

---

### Post by runeh76 on 2011-03-17
[IMG]http://ubuntuforums.org/picture.php?pictureid=7272&albumid=2164&dl=1293545403&thumb=1[/IMG]

---

