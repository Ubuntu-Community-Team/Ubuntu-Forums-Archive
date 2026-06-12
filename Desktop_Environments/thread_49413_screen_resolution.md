---
title: "screen resolution"
date: 2005-07-16
forum: Desktop Environments
---

### Post by mactabilis on 2005-07-16
Ive got the live cd of ubuntu and i cant change the screen resolution im stuck in 640x480 can somone please help me here.
Ive gone to options / sreen resolution /and there is no other choice but 640x480 its just stuck there.

---

### Post by FLeiXiuS on 2005-07-16
What you can do is modify X's configurations to see that you have more options available.  What video card do you have?  Sounds to me like your drivers aren't natively installed.

Well in other cases here you are...

Open up terminal.  From here enter the command, 

```
 sudo gedit /etc/X11/xorg.conf
```

Take scroll down to a section that looks simular to this...
```

        SubSection "Display"
                Depth           24
                **Modes           "1024x768" "800x600" "640x480"**
        EndSubSection

```

Change the modes appropriately.  If not then scroll up a bit till you find your VertRefresh/HorizSync.  Replace the defaults with the correct values of your monitor.  That'll give you that etra gain.

---

### Post by hydra on 2005-07-16
hi maybe if u have the same intel card i have this will work for u.....specially the adding  resolutions part  

[http://www.ubuntuforums.org/showthread.php?t=48761&page=2](http://www.ubuntuforums.org/showthread.php?t=48761&page=2)

---

