---
title: "Dell Inspiron ONE2205 - More touch support"
date: 2013-03-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ntzrmtthihu777 on 2013-03-17
Well I recently made the full switch from win$ to linux, installing Precise x64 on the above named machine. Now while touch does in fact work, I should like to be able to get more functionality out of it with ginn or something to that effect, but problem is I haven't the faintest idea how to go about it XD

Any user with some experience would be a welcome poster, and anyone else for that matter.

---

### Post by tigerjack89 on 2013-03-19
I'm interested to. I have the Inspiron 17RSE and I'm trying to enable multitouch/gesture touchpad functions.
I tried to follow [these 3d]("https://bbs.archlinux.org/viewtopic.php?id=144118&p=1"), but without results :(
Here are the result of xinput list command

```
xinput list 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=14    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]

```
Thanks in advance :)

---

