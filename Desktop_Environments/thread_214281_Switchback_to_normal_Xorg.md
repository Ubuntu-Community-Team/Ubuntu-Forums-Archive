---
title: "Switchback to normal Xorg???"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Lugia on 2006-07-12
Hi there, a day ago I installed XGL using the wiki instructions, and everything works fine, but since video support is still choppy when playing in full screen I wanted to switch back to normal GDM, so since I used the method "A" for XGL (XGL session instead overwriting the full xorg) I just tried to start a normal session, but it didn't work.

It just loads, and when it shows the desktop it hangs and gets me back to the login screen T_T

I did not install anything appart from the written in the wiki, no plugins, no CVS update :\

Any idea?

---

### Post by Lugia on 2006-07-13
*bump*

---

### Post by Lugia on 2006-07-15
*last bump* help please :S

---

### Post by tturrisi on 2006-07-15
The video issues may not be caused by xgl but may be due to the vido app & its settings.  What app are you using that plays choppy video?

---

### Post by rubso on 2006-07-15
i deleted xgl+compiz because its making many problems with power managment and WMV files playing in Totem.
so if you want to delete it completely from your ubuntu.
uninstall these packages
```
compiz (0.0.2-4ubuntu2)
compiz-gnome (0.0.2-4ubuntu2)
libglitz-glx1 (0.5.3-0ubuntu2)
libglitz1 (0.5.3-0ubuntu2)
libxcomposite1 (1:0.2.2.2-0ubuntu2)
xserver-xgl (7.0.0-0ubuntu4)

```
and remember that you need to edit the file gdm.conf-custom and get it back to its previous state. :)

---

### Post by Lugia on 2006-07-15
Thx man, will try ^^

---

### Post by slimdog360 on 2006-08-17
> **rubso said:**
> i deleted xgl+compiz because its making many problems with power managment and WMV files playing in Totem.
so if you want to delete it completely from your ubuntu.
uninstall these packages
```
compiz (0.0.2-4ubuntu2)
compiz-gnome (0.0.2-4ubuntu2)
libglitz-glx1 (0.5.3-0ubuntu2)
libglitz1 (0.5.3-0ubuntu2)
libxcomposite1 (1:0.2.2.2-0ubuntu2)
xserver-xgl (7.0.0-0ubuntu4)

```
**and remember that you need to edit the file gdm.conf-custom and get it back to its previous state. **:)
yeah thats really handy, lol, I just uninstalled compiz removing the files like you said but forgot to change the gdm.conf-custom file. 
That was fun changing it from the console, I had to install lynx to bring up the ubunu forums (I dont like w3m) then search the forums to see what file to modify in this horrible interface. The modify it, luckily it all worked.

---

