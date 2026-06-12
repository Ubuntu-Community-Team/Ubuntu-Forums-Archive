---
title: "how to change from Unity3D to Unity2D in 12.04"
date: 2012-05-14
forum: Desktop Environments
---

### Post by hopefulkayaker on 2012-05-14
Because of a really obnoxious hardware issue which I'll address in another thread, I am currently running 12.04 with Unity3D using a video card which is not capable of handling the 3D version of Unity.

I know that you can change which desktop environment on the login screen, but I have it set up to login automatically, so the login screen doesn't even appear. How do I get back to Unity 2D?

---

### Post by rai4shu2 on 2012-05-14
If you can't log out from the GUI, you could always press Ctrl+Alt+F1 and login from there. Then:

```
sudo restart lightdm
```

should get you to the graphical login.

---

### Post by hopefulkayaker on 2012-05-14
That caused the desktop to reload, without displaying the login screen.

---

### Post by markbl on 2012-05-14
Can't you just log out from the top right user menu? Then select Ubuntu 2D from the login screen option list.

---

### Post by JohnAadams on 2012-05-14
you need to do a graphical adviser they will suggest you.

---

### Post by hopefulkayaker on 2012-05-14
Aha! Yes, markbl, apparently so. Thanks a lot.

---

