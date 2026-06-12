---
title: "How can I use the analog sticks in a wii classic controller to move mouse [wminput]"
date: 2013-04-09
forum: Gaming &amp; Leisure
---

### Post by RefinedCode on 2013-04-09
I learned today that wine has really advanced since I last had ubuntu, my entire steam library works in Ubuntu.  I have wminput installed and it's working great.  I have portal 2 working amazingly,  and it relies heavily on mouse movement.  I know how to map keyboard keys in wminput like:

```

Wiimote.<button> = <button_symbol>
```

I have a classic controller with analog sticks and I want to try mapping the left analog stick on the wii classic controller to be mouse movement.  Does anyone know how to do this?  It would make my ubuntu gaming setup complete!  I completely got rid of windows when I found out portal 2 ran flawlessly under wine so Im happy today!  Thanks for any suggestions.

---

### Post by RefinedCode on 2013-04-09
Well I solved my own problem.  I didn't read the following:
> An event device is always created.  A mouse device is created if REL_X,  REL_Y, and BTN_LEFT symbols are mapped (~ABS_X and ~ABS_Y effectively  map REL_X and REL_Y, respectively).  A joystick device is created if  ABS_X is mapped.

From [http://abstrakraft.org/cwiid/wiki/wminput](http://abstrakraft.org/cwiid/wiki/wminput) If anyone is interested.

---

