---
title: "Touchpad with unexpected behavior"
date: 2023-11-11
forum: Desktop Environments
---

### Post by gloster10 on 2023-11-11
6.2.0-36-generic
Xubuntu
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy


I use an Asus Laptop with a "one Key" touchpad (Yes of course on the left/right bottom side will be the left/right mouse button emulation).
HW Info, output of 

```
 xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN1200:00 04F3:309F Mouse                 id=10    [slave  pointer  (2)]
&#9116;   &#8627; ELAN1200:00 04F3:309F Touchpad              id=11    [slave  pointer  (2)]
...

```

The problem :

If I reopen e.g. Thunar, and move on the touchpad over the presented files/directories, a file/directory can be grabbed, and after removing my finger from the touchpad, it will be dropped into the last pointer position, if there will be directory.
Another example, I reopen a x-terminal, and also with moving my finger over the touchpad, the former x-terminal output will moved up/down.

No former left/right button I did click, during open the window but it seems, there is an unintended left/right click in a key-buffer that leads to this behaviour.

Any idea to solve this problem?

---

### Post by matteo-dagord on 2023-12-19
I had a similar problem with my Toshiba laptop on Xubuntu 18.04, 16.04 and back... 
In my case the issue disappeared while using an usb mouse, but I never found a definitive solution.
The only workaround was installing plain Ubuntu and then install Xfce

---

