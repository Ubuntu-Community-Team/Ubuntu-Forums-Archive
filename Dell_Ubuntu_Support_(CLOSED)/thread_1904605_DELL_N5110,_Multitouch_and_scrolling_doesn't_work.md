---
title: "DELL N5110, Multitouch and scrolling doesn't work"
date: 2012-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ndkhoiits on 2012-01-05
I've just bought new laptop, N5110 and install Ubuntu 11.10 on it. Everything are ok, however multitouch and scrolling doesn't work, it became a normal mouse.

I don't know how to get driver for that, help me find a solution.


Thank so much.


I also attach list of devices in my laptop by command 

```
cat /proc/bus/input/devices > ~/devices.txt
```
[ATTACH]210277[/ATTACH]

---

### Post by blackmail on 2012-05-18
As i see no one has yet responded so i will do the hard thing and tell you the cold truth...
The type of touchpad that you have is the alps touchpad, and it is a bummer cause the people making it did not release any hw specs about it so the people kindly making the drivers for linux don't have on what to start that is why the thouchpad system has fallen back on some generic mouse drivers... now the thing is that this works on some machines and it doesn't on many many of them, also i own a Dell n5110 and i have had no success on finding the appropriate drivers or making them work...
give a google for alps touchpad drivers for ubuntu and you will have quite a few threads related, also there is something like synaptics touchpad drivers but i still had no luck...
If you have some information or you can find somethng on your own then please post back maybe somehow we will be able to solve this problem.

I am also wondering if the X could not be configured to make the touchpads right side act like a scroll bar at least...

---

### Post by HPA on 2012-08-31
I've got the same problem on a Dell Inspiron Q15R N5110 with Ubuntu 12.04 64bit installed.
Edge scrolling is disabled.
My touchpad is recognized as a PS/2 Generic Mouse.   
```
..@..-Dell:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   **&#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]**
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
```Is there any solution now?
Do we have any progress?
Thanks.

---

