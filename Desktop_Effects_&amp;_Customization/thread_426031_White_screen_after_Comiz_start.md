---
title: "White screen after Comiz start"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by totix800 on 2007-04-28
Hi,
I got a problem with compiz.
I first installed the NVIDIA-Linux-x86-1.0-9631-pkg1.run  drivers for my GeForce 2 MX 400.
After this I installed Xgl and its working fine by starting it at the Login in the session menu.

After this I installed the packages compiz and compiz-kde and tried to run compiz by this command:

compiz --indirect-rendering --strict-binding --replace kconf &
kde-window-decorator --replace & 

Like I red in a Wiki. After I ran this my Screen turns in White and the only way to turn him back to normal is by restarting X by pressing Crt+Alt+Del.
Is this a ordinary problem with a simple solution which you could give me?

Composite Managers are a total new area for me so if you need any specific Informations let me now I will give them to you. 

Thanks for reading

---

### Post by rolf-c on 2007-05-01
Try adding 

```
Option "AddARGBGLXVisuals" "True"
```
To your Screen section of xorg.conf.

Also reviewing this thread may shed some light - [http://ubuntuforums.org/showthread.php?t=425836&highlight=compiz+white+screen](http://ubuntuforums.org/showthread.php?t=425836&highlight=compiz+white+screen)

---

