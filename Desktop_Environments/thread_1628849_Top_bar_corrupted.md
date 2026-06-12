---
title: "Top bar corrupted"
date: 2010-11-23
forum: Desktop Environments
---

### Post by awe on 2010-11-23
Hello,

Every now and then I get the following:
[IMG]http://www.immsa.info/ubuntu/topbar.png[/IMG]
If you check the right of the picture, you can see that the power button is gone. Clicking in that area does nothing. Sometimes I get something similar with other parts of the panel; for instance, I may have a missing or partially visible Network-Manager applet, or mail icon, etc. When the NM icon is not present I cannot connect to my VPN which is very inconvenient. Appearance may vary after some time. Sometimes it corrects, other times it changes to a blank area (plain panel bar with nothing on it).

This happened to me in 10.04 (can't remember if it happened before that). It still happens in 10.10. It happens on my personal computers with 10.10 (one it 32-bit and the other is 64-bit) as well as at the office where all boxes run 10.04 (again, some 32-bit and some 64-bit).

I have to turn the computer off from the console. Quite annoying when I have to go to the computer of an employee and turn it off myself.

Anyone else with the same problem? Any suggestion? Regards.

---

### Post by nilarimogard on 2010-11-23
Run the following command and it should be ok:
```
killall gnome-panel
```

---

### Post by awe on 2010-11-23
Yep! It does work thank you. Maybe should I put this in the startup applications? I'll try and see if this cures the problem without having to type the command manually at every session the problem shows up.

---

