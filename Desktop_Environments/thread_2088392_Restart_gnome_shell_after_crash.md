---
title: "Restart gnome shell after crash"
date: 2012-11-26
forum: Desktop Environments
---

### Post by 5ulo on 2012-11-26
Oh no, something went wrong.. you saw it too? I don't like that message because if I haven't external monitor I'm not able to save my work. With my external monitor plugged in I switch to tty2 and restart gnome shell as follows:
```
gnome-shell --display :0 --replace &
```then I'm able to move all hidden windows behind the OH NO message to my second monitor and save my work & logout. The whole shell works fine, so I'm able to continue working as usually BUT the black screen on external monitor with logout button.
The question is, how to remove/quit/disable/kill/whatever that OH NO message after gnome-shell restart from tty[x] ???
Thanks

---

### Post by Frogs Hair on 2012-11-26
The simple restart command is from the command prompt  Alt + F2   ```
r
```

---

### Post by 5ulo on 2012-11-26
nope.. if gnome shell crashes youcan't use alt+f2 . there is only the black screen with the OH NO! Message, so you can only logout. so if I want to save my work I must restart the GS as I wrote in first post. then GS will work but still there will be the black message.

---

