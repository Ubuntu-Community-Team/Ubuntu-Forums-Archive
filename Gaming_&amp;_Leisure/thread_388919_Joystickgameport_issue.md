---
title: "Joystick/gameport issue"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by Patrick K on 2007-03-20
Is there a way to tell if the gameport is seen by Ubuntu (Edgy)?

I have a MSI MoBo with built in sound and gameport. The sound module is turn off (in the BIOS) in favor of a M-Audio PCI board. The gameport is on in the BIOS at int 201. The joystick is seen and can be calibrated by W98 without issue.

I have tried a couple different "How To's" (mainly this one [http://www.ubuntuforums.org/showthread.php?t=330607&highlight=gamepad+joystick](http://www.ubuntuforums.org/showthread.php?t=330607&highlight=gamepad+joystick)) but haven't had any success. Running jscalibrator and jscal both produce errors saying "unable to open joystick device dev/js0" 

lsmod shows this for the gameport:```
gameport               17160  1 analog

```

I don't know how to search the interrupts for int 201. Don't know if that would be of use. At this point I don't know if the OS can even see the gameport. 

Stick is CH Flightstick (2 buttons). About as basic as it gets.

---

