---
title: "Strange desktop problem with Xubuntu Dapper Drake (yeah am a n00b!)"
date: 2007-04-25
forum: Desktop Environments
---

### Post by asfaq on 2007-04-25
Installed Ubuntu 6.06 yesterday and then installed Xfce 4.3.90.2, when I installed it, it looked something akin to this image:

[IMG]http://www.xubuntu.org/files/edgy3.jpeg[/IMG]

while playing and customising the desktop i unintentionally did something which made my desktop items dissapear.. now, i have a desktop that looks something like this:

[IMG]http://img138.imageshack.us/img138/7716/screenshotkw1.png[/IMG]

I cant, for the life of me, revert it back to default settings. Another thing is that i cant right click on the desktop or edit anything on it anymore.. could someone be kind enough to help please?

Oh and am a complete n00b (but i learn fast, if thats any consolation) so please be very specific.. thnx in advance :)

---

### Post by xopher on 2007-04-25
Try removing ~/.config/xfce4 (or whatever version of xfce you have) and ~/.cache/xfce4

```
rm -rf ~/.config/xfce4; rm -rf ~/.cache/xfce4
```

---

### Post by asfaq on 2007-04-26
Entered the code in.. nothing happened, as far as i can tell.. still stuck.

Sorry for the late reply.. was held up with work yesterday.. today i'll reply much faster if someone's willing to help.

- Asfaq.

---

