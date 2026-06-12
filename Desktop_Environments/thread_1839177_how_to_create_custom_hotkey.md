---
title: "how to create custom hotkey?"
date: 2011-09-05
forum: Desktop Environments
---

### Post by goodbye-windows(tm) on 2011-09-05
Hi All,

I have a laptop with the intermittent black screen video problem. Occasionally, the screen just turns black, but the processor still runs. So, I need some method of shutting down the computer while the screen is black.

I think the answer is to open the terminal emulator, type in xfce4-session-logout, hit enter, hit the right arrow twice, then hit enter. That series of keystrokes will powerdown the computer properly.

I'd like to have a single hotkey to complete all the above steps, but I don't know how to assign the hotkey and make it do all the above steps.

Is there a step by step guide (hotkey 101 or similar) in the documentation or in this forum that explains now to make it happen? Needless to say, I'm new to xubuntu.

TY

Art

---

### Post by kerry_s on 2011-09-05
It would be easier to press ctrl+alt+f2, then ctrl+alt+delete

You could do a shortcut to run shutdown, but your going to have to set it up to run without password.

---

### Post by kerry_s on 2011-09-05
i just thought of a easier way, just set the power manager to shutdown when the power button is pushed.

---

### Post by raja.genupula on 2011-09-05
hey this thing gonna help you . 
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

---

### Post by goodbye-windows(tm) on 2011-09-05
**For Kerry-**

ctrl+alt+f2, then ctrl+alt+delete works ok, ty.

I worked out a series of commands which can be run in the terminal..they require typing the root password. I do not want to run without a password and I can't give the root password to my daughter, the other user on my system. The password can be typed in the blind, with practice though. But 'ctrl+alt+f2, then ctrl+alt+delete' works just as well and doesn't prompt for a password.

========
[B]
For Kerry-[/B]

The power manager solution does not work, possibly a quirk on the Dell laptop. I also can't run hibernate.

========

**For Raja-**

I think this solution is a little dated (written in 2007) since there is now a built in keyboard editor for creating custom shortcuts (menu>settings manager>keyboard>applications(tab). But, I did notice that conf-editor is available in the software center, so it can be loaded. I'll play with it later this evening.

========
 
TY to all.

Art

---

