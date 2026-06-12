---
title: "Xbox 360 Controller with Team Fortress 2"
date: 2013-02-19
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-02-19
Hey guys, I am trying to play Team Fortress 2 using my xbox 360 controller but have been unsuccessful so far (please don't just tell me to use the keyboard, lol). I found there is a module built into the kernel called xpad but there is also a userspace driver called xboxdrv. 
All the tutorials I have read for getting a 360 controller to work in TF2 state to open a console window within the game and type
```
exec 360controller
```
that does spit out some stuff and when I look at the keybindings or key mapping it does show things like the A button and X button mapped to actions in the game but when I fire up the game the controller has no affect on my character.
When I rmmod xpad and run the following command
```
sudo xboxdrv --type xbox360 --device-by-path 002:002
```
the terminal shows a whole mess of feedback when I play with the controller so I know it's being accepted as an input BUT how do I then get TF2 to use the controller?
I would appreciate any help guys.

---

### Post by r00st3r3 on 2013-02-19
Have you changed the key bindings to point to your controller? In the settings I believe you have to switch from keyboard and mouse to joystick.

---

### Post by dannyboy79 on 2013-02-19
yes, i went into advanced settings within keyboard and checked the box for gamepad.

---

### Post by r00st3r3 on 2013-02-19
It is supported by Valve since it is a Linux port now. I would check with Steam Support and see what they say. Sounds like a weird issue. I am glad I play with keyboard and mouse.

---

