---
title: "Top panel menu - disappear"
date: 2009-04-19
forum: General Help
---

### Post by slickuser on 2009-04-19
I'm not sure what happen but my top panel menu has disappeared.

I right click on the top screen, go to Menu editor, load the previous menu. Add a new entry and save it.

But I don't see it pop back.

What did I do wrong? Thanks.

---

### Post by northern lights on 2009-04-19
Run```
gnome-panel
```If it disappears again after a reboot/re-login, add *gnome-panel* to *Startup Programs* under *Sessions*.

---

### Post by mali2297 on 2009-04-19
> **northern lights said:**
> Run```
gnome-panel
```If it disappears again after a reboot/re-login, add *gnome-panel* to *Startup Programs* under *Sessions*.

As I understand, slickuser uses Xubuntu and has a panel, but not an applications menu.

@slickuser:
Can you reach the menu by right-clicking on the desktop?

---

### Post by slickuser on 2009-04-19
> **mali2297 said:**
> As I understand, slickuser uses Xubuntu and has a panel, but not an applications menu.

@slickuser:
Can you reach the menu by right-clicking on the desktop?

Hi,
I use Xubuntu, latest stable release.
It does have the panel when I right click on the desktop any where. And it still show all that applications menu like a regular at the top panel. I can launch the application from here too.
But I would like it show as the top panel.

The bottom panel is hidden too, I can't see which applications I'm running until I use Alt+Tab to switch to a different application.

Restart will not help even I uncheck save sessions.

---

### Post by mali2297 on 2009-04-19
> **slickuser said:**
> Hi,
I use Xubuntu, latest stable release.
It does have the panel when I right click on the desktop any where. And it still show all that applications menu like a regular at the top panel. I can launch the application from here too.
But I would like it show as the top panel.

The bottom panel is hidden too, I can't see which applications I'm running until I use Alt+Tab to switch to a different application.

Restart will not help even I uncheck save sessions.

I guess I don't quite understand after all. Do you have panels or don't you? (Right-click menus aren't panels.)

If not, launch the run dialog with Alt+F2 and type
```

xfce4-panel

```
On logout, remember to save the session.

---

### Post by slickuser on 2009-04-20
Right click gives me the top menu panel (Networ, Settings, etc...).

But how do make it stay fix at the top (all applications & quit button) without the right click like when I first install it.

The bottom panel will not show all my current running applications (like firefox, terminal, can't see from my monitor). I have to use alt+tab to switch between application.

---

### Post by mali2297 on 2009-04-20
Let me put it this way: What *can* you see on the desktop? (Without right-clicking.)

Do you have the bottom panel visible? In such case, right-click on it, choose *Add New Item* in the menu that appears and then pick Window List. To get an applications menu, pick *Launcher* instead.

Alternatively, you should be able to reset all Xfce settings to default by removing the hidden directories **.config** and **.cache** in your home folder.

---

### Post by slickuser on 2009-04-21
> **mali2297 said:**
> Let me put it this way: What *can* you see on the desktop? (Without right-clicking.)

Do you have the bottom panel visible? In such case, right-click on it, choose *Add New Item* in the menu that appears and then pick Window List. To get an applications menu, pick *Launcher* instead.

Alternatively, you should be able to reset all Xfce settings to default by removing the hidden directories **.config** and **.cache** in your home folder.

On my desktop, I can see File system, trash can, desktop icons.

The bottom panel is not visible. If I right click, it will give me the menu items such as Firefox, network, settings, etc...

I thought the default was in .config. If I remove this, it will probably show nothing right?

---

### Post by mali2297 on 2009-04-22
> **slickuser said:**
> On my desktop, I can see File system, trash can, desktop icons.

The bottom panel is not visible. If I right click, it will give me the menu items such as Firefox, network, settings, etc...

Did you try my suggestion in post #5? That solution has worked for others with the same problem. If it doesn't work, you can also try typing xfce4-panel in a terminal window; then you might see an error message.

> 
I thought the default was in .config. If I remove this, it will probably show nothing right?

If you remove those directories, then new ones will be created when you restart the desktop environment. By this, the settings should be back to default.

---

