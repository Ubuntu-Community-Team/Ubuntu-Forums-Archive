---
title: "synclient MaxTapTime=0"
date: 2011-08-13
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-08-13
This has got to be blindingly easy, but all my google searches turn up needlessly complex explanations for how to write a startup script. The command in the subject heading turns off the Linux touchpad *tap to click* insanity.](*,)

So if any of you would be kind enough help me create a startup script that incorporates this command, I will resist introducing my Touchpad to my 25 pound Makita Hammer Drill. Respectfully.

---

### Post by Toz on 2011-08-13
Try this. Create a new startup entry (Settings Manager->Session and Startup->Application Autostart) where the command is:
```
bash -c "synclient MaxTapTime=0"
```

---

### Post by neu5eeCh on 2011-08-13
Thanks Toz, I just put it in Startup. Hopefully this will work.

---

