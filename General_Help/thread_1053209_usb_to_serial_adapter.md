---
title: "usb to serial adapter"
date: 2009-01-28
forum: General Help
---

### Post by hockeyhead019 on 2009-01-28
ok guys so i just picked up a Port Authority 2 usb to serial cable and there isn't any driver that i can find that works as i've done a quick search of the web and haven't come up with anything... so i was wondering if anybody knew what to do in order to get they system to recognize it as a serial port... any questions let me know please... and for ur information i'm on ubuntu 8.10 and i want this for the parallax basic stamp programming tool as it need to be attached via a serial port

---

### Post by samborambo on 2009-01-28
Should work using the standard usb serial class driver. Have you plugged it in and tried it?

At the terminal type:

```
ls -la /dev/tty*

```

That should show /dev/ttyUSB0 if HAL detected the adaptor OK.

Otherwise, type dmesg and post up the output.

Sam.

---

### Post by hockeyhead019 on 2009-01-29
thanks i just didn't know where to find it but now i got it... thanks ;)

---

