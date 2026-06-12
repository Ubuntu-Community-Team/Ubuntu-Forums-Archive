---
title: "HP Probook 440 G3: WiFi switch not working any more after login (rfkill issue?)"
date: 2017-12-28
forum: Desktop Environments
---

### Post by nuschii2 on 2017-12-28
Hello,

I've come across an annoying problem with my Ubuntu 17.10 installation - this was still working with Ubuntu GNOME 17.04.

My HP Probook 440 G3 has a hardware WiFi switch right next to the mute button. After some testing I found that the button works fine on the framebuffer-console as well as in the GNOME greeter (login screen), i. e. it turns WiFi+Bluetooth off and on.
But as soon as I log into the GNOME Shell session, it stops working - it doesn't matter what session I choose:
[LIST]
[*]GNOME 
[*]GNOME on X.org 
[*]Ubuntu 
[*]Ubuntu on X.org 
[/LIST]

Whenever I login (or switch to a GNOME Shell session), I get the following on dmesg:
```
rfkill: input handler disabled
```

Whenever I logout (or switch to console or GNOME greeter), I get the following on dmesg:
```
rfkill: input handler enabled
```

Where does this come from? Is this a bug or can it be configured in any way? I really want to be able to turn WiFi off by the push of a button - like it worked in Ubuntu GNOME 17.04.

Thanks in advance.

---

