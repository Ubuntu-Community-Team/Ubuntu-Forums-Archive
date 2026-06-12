---
title: "composite and kde"
date: 2006-01-14
forum: General Help
---

### Post by tikal26 on 2006-01-14
I was reading about composite in linux and started looking for tut on this forum,but everytime I look they always make mention to kde built in compositor but I don't know what they mean or how to use it any ones could let me know how to do compostie on kde.

---

### Post by Laterix on 2006-01-17
First you should enable composite extension from your **xorg.conf** file. After that you must restart X, because conf file is read only when starting up. Now, if all went ok, you can go **System Settings** -> **Desktop** -> **Windows Behavior** -> **Transcluency**. There you can enable transcluency and shadows and set some parameters for them.

If you're not sure how to add composite to your xorg.conf ask and I explain it to you. By the way, I found KDE's composite (or whatever it is called) very unstable. :(

---

### Post by chadwick359 on 2006-01-17
> By the way, I found KDE's composite (or whatever it is called) very unstable. 

Really now? With the latest nvidia drivers and Kde3.5, I have found composite to be nearly rock solid. I am also onw, however using Xorg7, but even with 6.whatever, compositing support was pretty good to me. By the way the forum thread you want to read to get composite working well is here. 

[http://www.ubuntuforums.org/showthread.php?t=75527](http://www.ubuntuforums.org/showthread.php?t=75527)

---

### Post by Laterix on 2006-01-17
Perhaps I need to install new Nvidia drivers from somewhere else than repository? I installed my drivers with apt. I have to do some research, because composite is just so cool :).

---

### Post by chadwick359 on 2006-01-17
Yeah, the drivers in apt are oooold, Nvidia is now in the 8000 series drivers, and while dapper has the latest ones in repositories already, Breezy users will have to go to the nvidia site to download them and follow [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074) to get them installed correctly. Good luck and good hunting.

---

### Post by tikal26 on 2006-01-19
so maybe I should wait until dapper to try this. I had a problem when doign the xorg.conf think and now I can get  my screen resolution back to myold one I get a crappy one. Any ideas wat might have cause this, and by the way I also don't know what I have to change so that I can enable composite.
by the way thanks for you help

---

### Post by Laterix on 2006-01-21
[QUOTE=tikal26]I also don't know what I have to change so that I can enable composite.
by the way thanks for you help[/QUOTE]

You must add three lines to **/etc/X11/xorg.conf** -file
these lines are
```

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```
You can add these lines for example right before line
```

Section "Module"

```

I suggest you to look this thread that was already linked above: [http://www.ubuntuforums.org/showthread.php?t=75527](http://www.ubuntuforums.org/showthread.php?t=75527)

---

