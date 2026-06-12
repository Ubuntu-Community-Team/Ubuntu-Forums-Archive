---
title: "Apllication menus are hidden"
date: 2009-01-16
forum: General Help
---

### Post by Keikowned on 2009-01-16
Any folder/application I open, the menus are hidden (No Minimize, Maximize, Close on the top right). How do I re-enable those features?

---

### Post by Keikowned on 2009-01-16
> **Keikowned said:**
> Any folder/application I open, the menus are hidden (No Minimize, Maximize, Close on the top right). How do I re-enable those features?

:popcorn:

---

### Post by MaindotC on 2009-01-16
It sounds to me like your window manager isn't loading.  Can you do:
```

ps auwx | grep metacity

```
Are you using Desktop Effects and if not, does this happen when you enable Desktop Effects?

---

### Post by Keikowned on 2009-01-17
> **strAlan said:**
> It sounds to me like your window manager isn't loading.  Can you do:
```

ps auwx | grep metacity

```
Are you using Desktop Effects and if not, does this happen when you enable Desktop Effects?

Yes I am using Desktop Effects, the window menus just disappeared when I booted up.

I typed in what you mentioned in the [code] and this appeared;;
You can also see the windows menu gone ``
[http://i44.tinypic.com/2r62zrq.png](http://i44.tinypic.com/2r62zrq.png)

---

### Post by DeMus on 2009-01-17
> **Keikowned said:**
> Any folder/application I open, the menus are hidden (No Minimize, Maximize, Close on the top right). How do I re-enable those features?

Could it be that your screen resolution is set wrong, so the menu's are of screen?

DeMus

---

### Post by Keikowned on 2009-01-17
> **DeMus said:**
> Could it be that your screen resolution is set wrong, so the menu's are of screen?

DeMus

Look at the above URL I posted. 
They are not off screen as far as I know.

---

### Post by ajcham on 2009-01-17
The screenshot shows that the Menus are still there, but it is the window decorations that are missing.

First thing I would suggest is switching off desktop effects.

If that doesn't work, try System » Preferences » Appearence, press the Customise button, then try selecting a different Window Border.

---

### Post by Keikowned on 2009-01-17
> **ajcham said:**
> The screenshot shows that the Menus are still there, but it is the window decorations that are missing.

First thing I would suggest is switching off desktop effects.

If that doesn't work, try System » Preferences » Appearence, press the Customise button, then try selecting a different Window Border.

Ok, I turned off/on the appearances and the "window decorations" came back. 

Thanks for the help, and thanks to everyone who replied to the thread.

---

### Post by ajcham on 2009-01-17
BTW, do you have an Nvidia graphics chip?  If so, and you would like to still be able to use the Desktop Effects, try following this guide to install Nvidia's latest beta drivers: [http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html](http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html)

If you do that, you will then be able to switch the desktop effects back on, without losing the window borders again.

---

### Post by DeMus on 2009-01-17
> **Keikowned said:**
> Ok, I turned off/on the appearances and the "window decorations" came back. 

Thanks for the help, and thanks to everyone who replied to the thread.

Please mark the thread as solve using the "thread tools" button above.
Others know a solution has been found and can learn from that.

DeMus

---

### Post by ajcham on 2009-01-17
> **DeMus said:**
> Please mark the thread as solve using the "thread tools" button above.
Others know a solution has been found and can learn from that.


According to Ryan's announcement, [thread=1039481]here[/thread], the ability to mark threads as solved is temporarily disabled at the moment, as is the 'thanks' feature.

---

### Post by DeMus on 2009-01-17
> **ajcham said:**
> According to Ryan's announcement, [thread=1039481]here[/thread], the ability to mark threads as solved is temporarily disabled at the moment, as is the 'thanks' feature.

Sorry, did not know that.

DeMus

---

### Post by MaindotC on 2009-01-17
Is your issue really "Solved"?  It sounds to me like you have to sacrifice Desktop Effects to get your window decorator working - that's not "Solved" to me...

---

### Post by ajcham on 2009-01-17
> **strAlan said:**
> Is your issue really "Solved"?  It sounds to me like you have to sacrifice Desktop Effects to get your window decorator working - that's not "Solved" to me...

That's why I redirected the OP to the article at [http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html](http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html).

The issue appears to be related to a bug in the latest Nvidia drivers.  The solution is to either do without desktop effects until Nvidia release the fixed driver, or install the beta version from the link.  Obviously, installing a beta version is not ideal, but I've been using it and it seems to be pretty stable.

---

