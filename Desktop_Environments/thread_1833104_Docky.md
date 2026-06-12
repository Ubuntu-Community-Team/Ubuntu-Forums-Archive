---
title: "Docky"
date: 2011-08-25
forum: Desktop Environments
---

### Post by nomko on 2011-08-25
Hi,

Problem solved about appearing and disappearing of Docky, i used the stable PPA of Launchpad. But now i've got some weird issue.
See this link: [http://img685.imageshack.us/img685/357/werkblad1001.png](http://img685.imageshack.us/img685/357/werkblad1001.png)

Does anyone know how that black part can be that big and covers at least 20% of my desktop??? Changing settings of Docky has no result what so ever. I'm using 64-bit Ubuntu version 10.04.3.

---

### Post by kerry_s on 2011-08-25
You need to enable compositing.

---

### Post by nomko on 2011-08-25
It would be nice if you explain to me how. Just saying i have to enable something doesn't mean i understand what you mean. Thanks!

---

### Post by n6yga on 2011-08-25
You need to enable Desktop Effects.

Right-click on the desktop, select change background, desktop effects is one of the tabs on the dialog box that opens up. 

Sorry, I'm not on my Ubuntu machine right now, or I would be able to tell you exactly which one. I'm pretty sure you will find it!

Mark.

---

### Post by kerry_s on 2011-08-25
> **nomko said:**
> It would be nice if you explain to me how. Just saying i have to enable something doesn't mean i understand what you mean. Thanks!

It doesn't hurt to google. I'm on my iPod touch, so I can't check exactly how to do it.

the quickest way, run this command in terminal.
```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

---

### Post by claracc on 2011-08-26
If you use metacity as windows manager, you can activate compositing through gconf-editor.

You open an xterm and write gconf-editor; in the the window opened you select apps, metacity, general; then you click on composiring_manager in the right side of the window.

---

