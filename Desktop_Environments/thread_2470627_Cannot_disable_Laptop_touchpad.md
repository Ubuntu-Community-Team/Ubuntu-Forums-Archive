---
title: "Cannot disable Laptop touchpad"
date: 2022-01-05
forum: Desktop Environments
---

### Post by lister171254 on 2022-01-05
I'm running Ubuntu 21.10 on a brand new laptop, have an external USB mouse and cannot disable the touchpad.

I have diabled the touchpad via Settings, which worked until the next boot

I also installed xserver-xorg-input-synaptics as per suggestions I found via a search; that also worked, but only until the next boot

```
llist@LeosGamesLaptop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech B330/M330/M3                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; FTCS1000:01 2808:0102 Mouse             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; FTCS1000:01 2808:0102 Touchpad          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; BisonCam,NB Pro: BisonCam,NB Pr         	id=11	[slave  keyboard (3)]
    &#8627; Intel HID events                        	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; Logitech B330/M330/M3                   	id=17	[slave  keyboard (3)]

```

I've also tried xinput disable 13, but that does nothing for me

---

### Post by lister171254 on 2022-01-06
I followed instructions in this link [https://ubuntuhandbook.org/index.php/2021/10/disable-touchpad-typing-option-not-working/](https://ubuntuhandbook.org/index.php/2021/10/disable-touchpad-typing-option-not-working/) and installed touchpad-indicator.

Things are working as expected now and I have reported this as a bug

---

### Post by coley9225 on 2022-01-07
Hello lister. Double check your command. For my system it is 'xinput --disable <id>" I have that run at startup. I also have a keyboard shortcut for disable, and 1 for enable, just in case my mouse quits and I need to enable the touchpad. Just kind of a backup, in case you for get the exact command.

---

### Post by lister171254 on 2022-01-07
Thanks. I checked and I didn't have the '--' before the 'disable' flag.

In order to try this out I uninstalled touchpad-indicator and guess what; dis/en/abling the touchpad now works as expected through the Settings

Thanks

---

