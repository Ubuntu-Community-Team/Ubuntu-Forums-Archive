---
title: "X can't go through video hub, monitor turns off"
date: 2007-05-07
forum: Desktop Environments
---

### Post by m_bridge on 2007-05-07
Hello, i recenly bought a video hub,
it's a small box with 2 video input and 1 video output so i can use my only monitor 
- as main screen for my desktop pc
- as a secondary screen for my laptop
just touching the switch on the hub, (the tingy model is: Aten "Master View KVM Switch" cs-82a)

ubuntu (feisty) is connected as main desktop and while it boots everything is fine
[U][B]but as soon as the x server starts the monitor goes to sleep!
[/B][/U]
it seems really related to the window manager since if i go to the console with ctrl+alt+F1 the monitor turns back on :confused: 

i also tried to force the monitor on with  ```
xset -display :0 dpms force on
```
in this case the monitor stays wake (the led is on) but it's black

any suggestion?

---

