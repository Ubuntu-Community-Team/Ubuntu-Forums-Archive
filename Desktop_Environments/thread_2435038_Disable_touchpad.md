---
title: "Disable touchpad"
date: 2020-01-15
forum: Desktop Environments
---

### Post by mar.ste on 2020-01-15
My touchpad sometime interfere with my writings (probably because of me touching it inadvertedly) so I want to disable it.

I found this nice setting for Ubuntu: [http://ubuntuguide.net/disable-touchpad-tap-to-click-in-ubuntu-12-04-12-10](http://ubuntuguide.net/disable-touchpad-tap-to-click-in-ubuntu-12-04-12-10), but in Lubuntu the setting do not contains something like this in keyboard and mouse section.

There is a way to do it?

(I'm on 19.10)

Thank you

---

### Post by CelticWarrior on 2020-01-15
Different Desktop Environments deal differently with input devices and may have different settings. The setting you mentioned seems to be specific to Unity. I couldn't find anything similar in the current Ubuntu 19.10 (Gnome). It may never have been in Lubuntu.

You can install a third-party software that includes among others the "disable touchpad when typing" called touchpad-indicator that resides in the system tray:

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt update
sudo apt install touchpad-indicator
```

Open it from the Accessories menu, right-click the icon and select Preferences. In the Actions tab you can enable the required feature (cf. attached image)

---

### Post by gdesilva on 2020-01-16
This also may be useful...

[https://askubuntu.com/questions/844151/enable-disable-touchpad](https://askubuntu.com/questions/844151/enable-disable-touchpad)

---

### Post by mar.ste on 2020-02-21
> **gdesilva said:**
> This also may be useful...

[https://askubuntu.com/questions/844151/enable-disable-touchpad](https://askubuntu.com/questions/844151/enable-disable-touchpad)

Yes, this was useful!

And I also understood the problem with the other solution: my touchpad is recognized as a "keyboard mouse" (so other touchpad solutions seems not working)!

```
$ xinput
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SINO WEALTH USB KEYBOARD Mouse            id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]                                                                                                                
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]                                                                                                                
    &#8627; Power Button                              id=8    [slave  keyboard (3)]                                                                                                                
    &#8627; USB 2.0 Camera: USB 2.0 Camera            id=9    [slave  keyboard (3)]                                                                                                                
    &#8627; SINO WEALTH USB KEYBOARD                  id=10   [slave  keyboard (3)]                                                                                                                
    &#8627; SINO WEALTH USB KEYBOARD System Control   id=12   [slave  keyboard (3)]                                                                                                                
    &#8627; SINO WEALTH USB KEYBOARD Wireless Radio Control   id=13   [slave  keyboard (3)]                                                                                                        
    &#8627; SINO WEALTH USB KEYBOARD Consumer Control id=14   [slave  keyboard (3)]
    &#8627; bytcr-rt5651 Headset                      id=15   [slave  keyboard (3)]
    &#8627; Intel HID events                          id=16   [slave  keyboard (3)]
    &#8627; gpio-keys                                 id=17   [slave  keyboard (3)]

```

---

