---
title: "XBOX controller not working, any ideas?"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by Siph0n on 2007-06-03
Hi, I tried following a tutorial to make my xbox controller (the old one, NOT 360) work with my computer. I connected all 4 wires in the usb cable to their respective colors in the xbox controller, and left the yellow wire untouched. Then I put the heatshrink over it all , and plugged it into my computer. A js0, or any jsX, did not show up in /dev/ , and i have no idea what else to try. I have the xpad driver in the right directory, and did the modprobe command on it. Is there anything I can try to maybe troubleshoot this problem???

Siph0n

---

### Post by po0f on 2007-06-04
Siph0n,

Remove the controller and run the following commands from a terminal:

```
$ sudo modprobe -r xpad
$ sudo tail -fn0 /var/log/messages
```

Now replug the controller and post what the output is (^C to quit that command, or just  close the terminal window).

---

### Post by Siph0n on 2007-06-05
There is no output from that command, it just waits and waits for something, and does nothing... :( Maybe my xbox controller is done wrong?

Siph0n

---

### Post by po0f on 2007-06-05
Siph0n,

It could be.  You might want to try plugging the controller into a different USB port if you haven't already.

---

### Post by Siph0n on 2007-06-06
yup, no usb ports work, plus it doesnt even work on windows. Thats why I think theres something wrong with the controller :( I will try to use a different controller, and if that doesnt work, i'll just buy one pre-made! :)

---

