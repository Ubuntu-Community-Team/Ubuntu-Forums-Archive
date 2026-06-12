---
title: "Simple XFCE special effects question."
date: 2008-02-24
forum: Desktop Environments
---

### Post by solarwind on 2008-02-24
There are several effects captured in this image: [http://upload.wikimedia.org/wikipedia/commons/7/71/Xfce-4.4.png](http://upload.wikimedia.org/wikipedia/commons/7/71/Xfce-4.4.png)

1. How do I get the window drop shadow effect working?
2. How do I get transparent windows and panels working?
3. Is there a way to get an application's menu bar to show up top like Mac OS? (Like [this]("http://upload.wikimedia.org/wikipedia/en/c/c0/Leopard_Desktop.png"))

---

### Post by santiagoward2000 on 2008-02-24
Most Effects on Xfce are under **System/Preferences/Window Manager Tweaks**. I know the shadow effect is for sure, but I'm not so sure about transparencies. Right now I can't open it to see because I'm uing Compiz, but give it a try!
About number 3, I haven't seen that on Linux... Would be cool though. :D
Cheers!

---

### Post by solarwind on 2008-02-24
> **santiagoward2000 said:**
> Most Effects on Xfce are under **System/Preferences/Window Manager Tweaks**. I know the shadow effect is for sure, but I'm not so sure about transparencies. Right now I can't open it to see because I'm uing Compiz, but give it a try!
About number 3, I haven't seen that on Linux... Would be cool though. :D
Cheers!

There is no such option in my *window manager tweaks* dialog. As for number 3, it is very easy in KDE as there is an option to do it. For Gnome, there is a simple hack and can also be easily done. I have no idea for XFCE though but I really want to know how to do it.

---

### Post by aimran on 2008-02-24
Hey there. The transparent effects is in one of the more advanced window settings. I can't remember off the top of my head but roughly that windows that are not focused will be less opaque.

Secondly I recommend setting up xcompmgr for drop shadows: [http://ubuntuforums.org/showthread.php?t=75527&highlight=vista+effect+xcompmgr](http://ubuntuforums.org/showthread.php?t=75527&highlight=vista+effect+xcompmgr)

---

### Post by santiagoward2000 on 2008-02-24
> **solarwind said:**
> There is no such option in my *window manager tweaks* dialog.

Hi!
I just turned Compiz off to see, and I have them. They're under the **Compositor** tab. You need to check the **Enable display compositing** box and then enable the options you want. There are 2 check boxes for shadows and some scroll bars for the opacity options.
I attatched an image to make it clearer.
Tell us if you can find the options now.
Good luck!

---

### Post by solarwind on 2008-02-24
> **aimran said:**
> Hey there. The transparent effects is in one of the more advanced window settings. I can't remember off the top of my head but roughly that windows that are not focused will be less opaque.

Secondly I recommend setting up xcompmgr for drop shadows: [http://ubuntuforums.org/showthread.php?t=75527&highlight=vista+effect+xcompmgr](http://ubuntuforums.org/showthread.php?t=75527&highlight=vista+effect+xcompmgr)

Thanks for this, but the most important thing for me right now is the global menu up top. In Gnome, it can be done like [this]("https://wiki.ubuntu.com/global_menu"). But I don't know how to do it in XFCE.

---

### Post by solarwind on 2008-02-24
> **santiagoward2000 said:**
> Hi!
I just turned Compiz off to see, and I have them. They're under the **Compositor** tab. You need to check the **Enable display compositing** box and then enable the options you want. There are 2 check boxes for shadows and some scroll bars for the opacity options.
I attatched an image to make it clearer.
Tell us if you can find the options now.
Good luck!

Hey, thanks for your reply. I do not have the compositing tab at all... This is all I have:
 [[IMG]http://img401.imageshack.us/img401/2984/screenshotmu8.th.png[/IMG]](http://img401.imageshack.us/img401/2984/screenshotmu8.png)

---

### Post by solarwind on 2008-02-24
I was reading [this]("http://xubuntublog.wordpress.com/2008/02/15/design-your-own-desktop-with-xfce-44-part-2/") and came across [this]("http://ubuntuforums.org/showpost.php?p=1586951") but the pages don't seem to exist.

---

### Post by santiagoward2000 on 2008-02-24
> **solarwind said:**
> Hey, thanks for your reply. I do not have the compositing tab at all... This is all I have:


Hmm... Perhaps you need to edit your **xorg.config** file.
Try this:
```
sudo /etc/X11/xorg.config
```

and enter:
```
Section "Extensions"
Option “Composite” “Enable”
EndSection
```

at the end of the file. Then, restart your session and try again.
I didn't have to do all this, but i don't know...

---

### Post by santiagoward2000 on 2008-02-24
> **solarwind said:**
> I was reading [this]("http://xubuntublog.wordpress.com/2008/02/15/design-your-own-desktop-with-xfce-44-part-2/") and came across [this]("http://ubuntuforums.org/showpost.php?p=1586951").

:guitar: Cool! That looks good! :)

---

### Post by solarwind on 2008-02-24
> **santiagoward2000 said:**
> :guitar: Cool! That looks good! :)

Yeah, unfortunately the pages are gone...

---

### Post by solarwind on 2008-02-24
> **santiagoward2000 said:**
> Hmm... Perhaps you need to edit your **xorg.config** file.
Try this:
```
sudo /etc/X11/xorg.config
```

and enter:
```
Section "Extensions"
Option “Composite” “Enable”
EndSection
```

at the end of the file. Then, restart your session and try again.
I didn't have to do all this, but i don't know...

Wow, guess what was at the end of that file...

```
Section "Extensions"
Option “Composite” "0"
EndSection
```

I replaced that ^ with your new code. Time to test.

---

### Post by santiagoward2000 on 2008-02-24
> **solarwind said:**
> Wow, guess what was at the end of that file...

```
Section "Extensions"
Option “Composite” "0"
EndSection
```

I replaced that ^ with your new code. Time to test.

I'm crossing my fingers (what makes it REALLY hard to type) :lolflag:
Good luck!

---

### Post by solarwind on 2008-02-24
> **santiagoward2000 said:**
> I'm crossing my fingers (what makes it REALLY hard to type) :lolflag:
Good luck!

Ok that got the compositor working, thanks a LOT!

---

### Post by santiagoward2000 on 2008-02-24
> **solarwind said:**
> Ok that got the compositor working, thanks a LOT!

You are welcome! :KS
I'm glad to help!

---

### Post by solarwind on 2008-02-24
> **santiagoward2000 said:**
> You are welcome! :KS
I'm glad to help!

Thanks again. The compositing is causing wierd glitches like this:

[[IMG]http://img171.imageshack.us/img171/986/screenshotrg7.th.png[/IMG]](http://img171.imageshack.us/img171/986/screenshotrg7.png)

but that's probably because of my ATI integrated graphics card (which everyone knows, sucks on Linux). I wont enable compositing now since it's not all that important but I'm still looking for that global menu thing.

---

### Post by Ptero-4 on 2008-02-24
The GTK2 hack for the menubar works also for Xfce, all you need is the xfce panel applet instead of the gnome one (note, this works only on the old hack, the new one is gnome-only ATM, but the old one is more elegant anyway).

---

### Post by santiagoward2000 on 2008-02-24
> **solarwind said:**
> Thanks again. The compositing is causing wierd glitches like this:

but that's probably because of my ATI integrated graphics card (which everyone knows, sucks on Linux). I wont enable compositing now since it's not all that important but I'm still looking for that global menu thing.

That's weird... I'm using an ATI too, and I'm not having that kind of problems...
Perhaps that's because I have turned Compiz off, but not XGL. But I'm just guessing here.

---

### Post by solarwind on 2008-02-25
> **Ptero-4 said:**
> The GTK2 hack for the menubar works also for Xfce, all you need is the xfce panel applet instead of the gnome one (note, this works only on the old hack, the new one is gnome-only ATM, but the old one is more elegant anyway).

Thanks, where do you get the xfce panel applet though? By the way, love the quote in your sig ;)

> **santiagoward2000 said:**
> That's weird... I'm using an ATI too, and I'm not having that kind of problems...
Perhaps that's because I have turned Compiz off, but not XGL. But I'm just guessing here.

It could be that. How do you turn off Compiz but not XGL? Sorry for the dumb questions, I'm a noob with all the new compositing stuff...

---

### Post by santiagoward2000 on 2008-02-25
> **solarwind said:**
> It could be that. How do you turn off Compiz but not XGL? Sorry for the dumb questions, I'm a noob with all the new compositing stuff...

Don't worry!
If you are in Gusty, once you installed XGL it stays enable, unless you create the following file:
**~/.config/xserver-xgl/disable**
So, even if you close Compiz, you still have XGL.

---

### Post by solarwind on 2008-02-25
> **santiagoward2000 said:**
> Don't worry!
If you are in Gusty, once you installed XGL it stays enable, unless you create the following file:
**~/.config/xserver-xgl/disable**
So, even if you close Compiz, you still have XGL.

I installed XGL but it made my XFCE unable to start up and just hang at the loading screen so I disabled XGL. It's not that important anyway. Thanks for your help!

---

### Post by santiagoward2000 on 2008-02-25
> **solarwind said:**
> I installed XGL but it made my XFCE unable to start up and just hang at the loading screen so I disabled XGL. It's not that important anyway. Thanks for your help!

You're welcome!

---

