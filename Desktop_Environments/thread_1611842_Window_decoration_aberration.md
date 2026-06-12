---
title: "Window decoration aberration"
date: 2010-11-02
forum: Desktop Environments
---

### Post by GlennW on 2010-11-02
I've got a bit of an issue. It's nothing that hinders functionality but it's one of inconsistency. As you can see from the first screenshot, I have window decoration (drop shadows) on all the windows. However, the popupmenu (right click on empty desktop) has none. It responds to compiz animations for opening and closing, etc., but has no shadow.

Screenshot 2 displays the dropdownmenu from the panel menu with the appropriate shadow. 

Can anyone shed some light on this?

Thanks.

---

### Post by GlennW on 2010-11-03
The problem has resolved itself!

For some reason, a partial upgrade was required. Of course, wanting to keep my linux box up to date, I accepted. Compiz then promptly crashed and left me totally frustrated. After some research, I discovered that removing the Compiz PPA should solve the crash issue. Upon removal, a restart, Compiz was up! I had to go through some of the settings and reset some things. 

Then I discovered the offending popupmenu has its shadow! Nice...

I have no advice to declare this thread solved but it is now mute.

Thanks anyway!

---

### Post by GlennW on 2010-11-16
In my previous post I guess I was a bit too hasty. 

For some unknown reason, I am back to the shadow/no shadow inconsistency once again. I removed the shadow on the panel menu (bar across the top of desktop) by accessing Compiz>Window Decorations>Shadow Windows>(any) & !(type=Dock). I changed it back to "any" hoping that it might make a change but nope! It's the same. 

Just to be clear, any application that I open (Firefox, Gimp, Audacity, etc.) has shadowed drop down menus and right click menus. On the other troubled hand, right click on the desktop or any menu, and subsequent drop down menu or right click menu, from "Places," produces a shadowless menu selection box. 

Any ideas???

---

### Post by deconstrained on 2010-11-16
I've gotten plenty of window decor problems with Compiz in the past. They all ended when I ditched emerald and instead tried using 'compiz-decorator' or 'gtk-window-decorator --replace' as the decoration command (under "Window Decoration" in CompizConfig). Emerald is notoriously glitchy, at least in my experience.

---

### Post by GlennW on 2010-11-17
> **deconstrained said:**
> I've gotten plenty of window decor problems with Compiz in the past. They all ended when I ditched emerald and instead tried using 'compiz-decorator' or 'gtk-window-decorator --replace' as the decoration command (under "Window Decoration" in CompizConfig). Emerald is notoriously glitchy, at least in my experience.

I tried both commands in the Windows Decorator. With both I lost all shadows in every instance. I guess I can wait until Emerald becomes more stable. The interesting thing is that I have a laptop running 10.04 with virtually all of the same settings as my desktop and its effects are consistently the way they should be. 

Is there a version of Emerald that is causing the problem?

Or is the theme that I'm using? (105185 Scaled Black Glass, v. 0.5, created by vincentpsp2, use with MurrinaDBO)

---

### Post by Frogs Hair on 2010-11-17
Could be a combination of theme + Emerald + Compiz . I used Emerald on 9.10 with out problems but it was flaky on 10.04 and removed. I have not tried it on 10.10. I use proprietary drivers as well so it was hard to figure what was making it behave badly in 10.04 and I know Emerald works fine for many users.

---

### Post by stinkeye on 2010-11-17
> **GlennW said:**
> I've got a bit of an issue. It's nothing that hinders functionality but it's one of inconsistency. As you can see from the first screenshot, I have window decoration (drop shadows) on all the windows. However, the popupmenu (right click on empty desktop) has none. It responds to compiz animations for opening and closing, etc., but has no shadow.

Screenshot 2 displays the dropdownmenu from the panel menu with the appropriate shadow. 

Can anyone shed some light on this?

Thanks.

```
(any) & !(type=Dock) & (type=PopupMenu | menu | DropdownMenu)
```

---

### Post by GlennW on 2010-11-17
> **stinkeye said:**
> ```
(any) & !(type=Dock) & (type=PopupMenu | menu | DropdownMenu)
```

I implemented your code suggestion and rebooted to be sure. The attached screenshot displays "My Computer" and the DropdownMenu that has no shadow.

You can see that there is the proper shadow on the upper left corner of the window (it's too dark to see it anywhere else).

Thanks for your attention to this.

---

### Post by stinkeye on 2010-11-17
Are you using nautilus-elementary by any chance?
If the **enable rgba transparency** setting in 
edit > preferences > tweaks
is ticked it stops the menu from being shadowed for me.

If it is enabled, disable it.

You need to run in the terminal
```
pkill nautilus
```
before it takes effect.

---

### Post by GlennW on 2010-11-18
Congrats stinkeye!

It worked!

System wide consistency!

Thanks for your time on this issue.

---

### Post by stinkeye on 2010-11-18
No problem, I'm learning at the same time.
;)

---

