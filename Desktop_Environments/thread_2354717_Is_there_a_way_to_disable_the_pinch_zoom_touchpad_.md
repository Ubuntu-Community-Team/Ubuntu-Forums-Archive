---
title: "Is there a way to disable the pinch zoom touchpad gesture?"
date: 2017-03-05
forum: Desktop Environments
---

### Post by marrowm on 2017-03-05
I just got a new laptop and it runs Ubuntu perfectly, unfortunately the track pad is not the best and the zoom gesture is too sensitive for me. This means I end up zooming in and out instead of scrolling (when web browsing for example) which is very annoying. Is there a way to disable the pinch zoom gesture? Preferably for all programs but if that's not possible at least in chrome/firefox? 

The mouse & touchpad panel in system settings only let me choose primary button and double click speed.

Grateful for any advice!

---

### Post by [Knuckles] on 2017-07-10
I have exactly the same problem, and scouring the internet doesn't seem to help at all. Anyone?

---

### Post by [Knuckles] on 2017-07-23
Ok so I finally discovered a workaround.

It seems like, at least in my case, the pinch zoom touchpad gesture is being emulated somewhere along the stack or even by the touchpad itself. I mention this "emulation" because if I use an app such as "xev", I can see that when I pinch in or out, something's actually emulating ctrl + scroll up/down, and sending that to the application.

I have some suspicions that this may be the touchpad itself as if I leave X and use the virtual terminal, I still can observe the ctrl+scroll being sent. If anyone wants to help me debug or shed some light on this, I would be very thankful!

But moving on to the workaround. I discovered that the touchpad does show up both as a touchpad and as a keyboard (that's the "HAILUCK CO.,LTD Usb Touch", in my case):

```
$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; HAILUCK CO.,LTD Usb Touch                 id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M525                             id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                            id=11   [slave  keyboard (3)]
    &#8627; Intel HID events                          id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; HAILUCK CO.,LTD Usb Touch                 id=8    [slave  keyboard (3)]

```

And thus I wondered, can I just disable the fake keyboard device? It turns out that I can: "xinput disable 8" works! (The 8 comes from the id=8 that you see is used by the "usb touch" device under the "core keyboard)

This command finally disables the keyboard emulation and thus stops the ctrl being sent, and only the scroll event is sent, which turns this into a major pain point into a minor annoyance.

Hope this helps someone out there!

---

