---
title: "Top bar in ubuntu classic (no effects) Help me."
date: 2011-06-22
forum: Desktop Environments
---

### Post by 1337_N1NJ4 on 2011-06-22
I am running Ubuntu Classic (No Effects) 11.04 Linux 2.6.38-10-generic. I currently have my Ubuntu Mac'd out with OSX 10.x Snow Leopard theme and I like having the menu bar of windows in the top bar of Ubuntu just like it does it in Mac but the only way it does that is if I run Unity but then I don't get a transparent grey top bar. so in short I want to keep it in classic mode so I get the grey transparent bar but I want it to become a menu bar for open windows. so far the only time it becomes a menu bar is for native Ubuntu programs such as evolution mail. But i want it to do it for all programs on the computer. any help would be appreciated thank you :)

---

### Post by Frogs Hair on 2011-06-22
There is a global menu ppa the for gnome panel in 10.10 , but it has not been updated to include 11.04 classic gnome . I think this is because unity has a global menu already . I don't think the unity global menu package will work with the gnome panel.

---

### Post by Seq on 2011-06-22
> **Frogs Hair said:**
> There is a global menu ppa the for gnome panel in 10.10 , but it has not been updated to include 11.04 classic gnome . I think this is because unity has a global menu already . I don't think the unity global menu package will work with the gnome panel.

No need for the "globalmenu" approach.

Install "indicator-applet-appmenu". This will install the "classic" gnome panel applet for doing in-panel menus the same way unity does. This is included already in Ubuntu, but not installed by default.

You will have to add the applet to your panel. This may require log out/in for the panel to see a newly available applet (or HUP it).

---

### Post by Frogs Hair on 2011-06-22
> **Seq said:**
> No need for the "globalmenu" approach.

Install "indicator-applet-appmenu". This will install the "classic" gnome panel applet for doing in-panel menus the same way unity does. This is included already in Ubuntu, but not installed by default.

You will have to add the applet to your panel. This may require log out/in for the panel to see a newly available applet (or HUP it).
Thanks Seq

---

### Post by 1337_N1NJ4 on 2011-06-23
hey seq could you give me the terminal code to install it thank you. i have learned almost everything about my ubuntu but the terminal is still something i'm working on mastering. or if there is a way to find it in the software center that would work too. :)

---

