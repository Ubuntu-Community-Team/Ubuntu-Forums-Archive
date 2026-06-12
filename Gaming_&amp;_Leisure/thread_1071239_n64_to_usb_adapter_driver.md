---
title: "n64 to usb adapter driver?"
date: 2009-02-15
forum: Gaming &amp; Leisure
---

### Post by brad99 on 2009-02-15
Does anybody have any driver suggestions for this [adapter]("http://www.4triangles.com/catalog/ps2-to-usb-adapter-playstation-to-pc-p-37.html") 
I'm running Ubuntu 8.10 intrepid ibex

---

### Post by brad99 on 2009-02-16
bump

---

### Post by GerbilSoft on 2009-02-16
That adapter appears to be a standard USB HID device, so it shouldn't need a specialized driver. It should automatically show up as a joystick device.

---

### Post by brad99 on 2009-03-06
yes it does recognize my adapter, but when I connect my N64 controller, I don't receive full range of the analog stick.

---

### Post by AdamShumpisxXx on 2009-03-06
Have you tried...
```

sudo apt-get install jscalibrator

```
?

---

### Post by trlkly on 2009-03-06
Oh. I have one of those.

I found that jscalibrator didn't work, and I have to use the joystick kcontrol module. I already had kubuntu installed, so this is no problem for me. I don't know if you can install the joystick program independently, though...

---

### Post by grossaffe on 2009-03-06
jscalibrator is the sucks.  jstest is made of win.

---

### Post by brad99 on 2009-03-08
thanks for the advice, ill try them out and get back to you

---

### Post by trlkly on 2009-04-18
Bit of a necropost, but hey.

I've finally found that jstest comes with jscal, which, although a command line program, works the best. You see, it will output your configuration settings, which you can save and apply again the next time you use the controller.

All the KDE Joystick program seems to be is a graphical version of jscal. jscalibrator just hasn't been updated in forever, and just doesn't work.

---

