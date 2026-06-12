---
title: "Laptop keyboard caps-lock!!!!"
date: 2011-04-25
forum: Desktop Environments
---

### Post by micha8l on 2011-04-25
Hello, I use my laptop keyboard when on the move, but when I'm home I plug my keyboard into laptop's USB port for easier typing. I noticed that if leave the caps-lock on on the USB keyboard and unplug the keyboard then then caps-lock will still be in effect on the laptop. Is this Ubuntu's default behaviour, or should a signal be sent to Ubutnu, once the USB keyboard is unplugged, reseting keyboard functionality to its default state (as it is when you login)?

---

### Post by Krytarik on 2011-04-25
Because the state of CapsLock is stored by the OS, not by the keyboard itself (like, for example, the state of the Fn-key row), you really need to do something to tell the OS to disable CapsLock, usually by just pressing CapsLock. Don't you have a CapsLock key at your laptop's keyboard?

---

### Post by micha8l on 2011-04-25
Thanks for the reply and yes I do have caps-lock key on my keyboard thank you! But when I press it it will invert the selection i.e. if the caps-lock light key was off and I typed then it would be in caps, and if it was on, the opposite. I could probably write a small program to reset key functionality but I don't know how a keyboard is referenced.

To fix the problem, I have to plug my USB keyboard back into the laptop, hit the caps-lock key and unplug it. I know this isn't trivial to do -- not a reason to switch OS -- but when I leave my home with this inverted-caps behaviour then the only way to fix is with logout/login (quite a measure to fix, if you ask me!)

Kind Regard,
Mike

---

### Post by Krytarik on 2011-04-25
Ok, I understand. You can use "xdotool" to toggle the state of CapsLock without affecting the LED indicator at your keyboard. I just yet tested it.

To install "xdotool":
```
sudo apt-get install xdotool
```The command to toggle the state of CapsLock:
```
xdotool key Caps_Lock
```

---

### Post by micha8l on 2011-04-25
That's perfect, exactly the sort of thing I was looking for. Thanks [Krytarik]("http://ubuntuforums.org/member.php?u=1187548")!

---

