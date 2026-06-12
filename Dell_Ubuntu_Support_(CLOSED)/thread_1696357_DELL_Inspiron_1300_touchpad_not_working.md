---
title: "DELL Inspiron 1300 touchpad not working"
date: 2011-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pottonian on 2011-02-27
Hi all

I'm an extremely wet behind the ears newby to Ubuntu having now had the sum total of some 3 days' experience using it on an old DELL laptop which I'm trying to recondition for use as an additional web browsing laptop for the family to use.

All is working well apart from one thing - the dreaded touchpad - it's completely dead and when I try and work through the various fixes I've found both here and elsewhere on Google, this has had no effect whatsoever.

I can see from looking at other posts around that people *can* get their touchpads to work with DELL laptops and I know that there's nothing inherently wrong with it from when I was using it with Windows - therefore if someone could please point me in the right direction so I can find an idiot-proof guide on what I should try from scratch to get this problem resolved, it would be MUCH appreciated! :D

FWIW - I'm using Ubuntu 10.10.

Thanks in anticipation -

Ian

---

### Post by Slave2Metal on 2011-02-27
There are quite a few threads on this and I'm reluctant to suggest anything.  Seems it's not working for everyone.  Several posts down, look at [SOLVED]Dell XPS15 (or similar) and see if you can make it work.  You would download the deb file in the first link, then copy/paste the code in terminal and reboot.  Then go to system>preferences>mouse>touchpad.  Works for some and not others.

---

### Post by RyanMarcus on 2011-03-01
This is may be due to loose cable connector try to re-attach the cable inside the laptop or may be the driver required for touchpad function get deleted or removed. Reinstall it using original driver CD.

---

### Post by pottonian on 2011-03-01
Thank you for your responses so far - I've tried following the suggestions posted but have not managed to get anywhere.  I don't have a driver for the touchpad and so won't be able to follow that route at this stage.

FWIW, I've managed to run xinput list which I'm attaching below which *doesn't* recognise the touchpad but does show a PS/2 Optical Mouse (is this because I've got my USB mouse connected?)

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

Interestingly, on running sudo tpconfig -i, this *does* recognise the touchpad (so I'm therefore hoping that there's no physical problem with the touchpad connection)

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;        no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

All very confusing......:confused:

---

