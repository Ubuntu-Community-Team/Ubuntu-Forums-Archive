---
title: "Delayed pics in camorama"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Randomskk on 2006-01-28
Heya
I use camorama to take pictures using my webcam, and that works fine, but I'd really like a way of being able to take them a few seconds after I press the button.
I don't see any option in the program itself, but is there any way to do this? A command line switch, a way to delay sending the button press, a way to have a mouse click after a few seconds, whatever...

Something like that would be really great :)

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=Randomskk]Heya
I use camorama to take pictures using my webcam, and that works fine, but I'd really like a way of being able to take them a few seconds after I press the button.
I don't see any option in the program itself, but is there any way to do this? A command line switch, a way to delay sending the button press, a way to have a mouse click after a few seconds, whatever...

Something like that would be really great :)[/QUOTE]
If you can make the program take a picture from the command line, you can delay it by using sleep.  For example:
```

$ sleep 5; echo "Hello"

```
Causes the terminal to sleep for 5 seconds and then print "Hello" to the terminal.  If camorama can be made to "snap the shutter" from the command line, you could just delay it that way.

---

