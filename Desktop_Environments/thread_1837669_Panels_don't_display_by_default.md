---
title: "Panels don't display by default"
date: 2011-09-02
forum: Desktop Environments
---

### Post by jfed on 2011-09-02
Hello. I recently installed Xfce4 with Compiz on my laptop in 10.10 to try and get used to it, so I can use it an an alternative to Unity and Gnome 3. Compiz doesn't start by default so I have to manually start it and reload the window manager each time I bootup by going to system>compiz. Before doing that, I have no window manager. Today when I turned my laptop on and loaded into Xfce, for some reason all three of my panels were gone. So I had no way of starting Compiz, and had no window manager, along with no way to start a terminal. Great.

I managed to get Thunar up by insterting a DvD, and opened a terminal that way. Turns out all I had to do was run

```
xfce4 panel
```

Then I could start up compiz and everything was fine. My question is how can I fix it so that "xfce4 panel" runs by default on login, as well as compiz?

---

### Post by saltmarshlamb on 2011-09-02
Have you tried saving the session?

Setting Manager - Session Startup - Session tab - you can edit the restart style by clicking on it - then save.

---

### Post by raja.genupula on 2011-09-02
> **jfed said:**
> Hello. I recently installed Xfce4 with Compiz on my laptop in 10.10 to try and get used to it, so I can use it an an alternative to Unity and Gnome 3. Compiz doesn't start by default so I have to manually start it and reload the window manager each time I bootup by going to system>compiz. Before doing that, I have no window manager. Today when I turned my laptop on and loaded into Xfce, for some reason all three of my panels were gone. So I had no way of starting Compiz, and had no window manager, along with no way to start a terminal. Great.

I managed to get Thunar up by insterting a DvD, and opened a terminal that way. Turns out all I had to do was run

```
xfce4 panel
```

Then I could start up compiz and everything was fine. My question is how can I fix it so that "xfce4 panel" runs by default on login, as well as compiz?


at login window in system settings after unlocking it you can choose what session you want . i'm sure this gonna help you . there you can choose the session what you want. from the next login its going to be what you have selected .

---

### Post by jfed on 2011-09-02
> **saltmarshlamb said:**
> Have you tried saving the session?



By default for some reason it would save my session when I shut down without closing all the current windows. I don't know why.

And that didn't really change much. When I restarted I still had no window manager, and had to kill all the windows with Alt+f4 and start compiz manually.


> **raja.genupula said:**
> at login window in system settings after unlocking it you can choose what session you want . i'm sure this gonna help you . there you can choose the session what you want. from the next login its going to be what you have selected .
Yes, I know this already, and do this. When I boot up it brings me to the log in screen, and after selecting which user I am, on the bottom there is a panel, and you can select the currently installed GUIs. There is GNOME, and Xfce. Thats not the issue. The issue is that for some reason, when I boot into Xfce, my panels aren't activated by default, and I must activate them manually. Everything is peachy in gnome, just for some reason not in Xfce.

---

### Post by hhh on 2011-09-02
Xfce has several options for starting/saving sessionss, they'reall in the same manager but on different screens. I'm using Debian so their location may differ in Xubuntu, but running it from a terminal or run dialog should bring you to it...```
xfce4-settings-manager
```
~Choose "Sessions and Startup", under General click either "Prompt on logout" or "Save automatically".
~Choose "Session". Make sure Compiz is listed and that "Restart Style" is set to "Immediately". Click the "Save Session" button in the lower left corner. Check if "xfce4-settings-helper" is listed to start Immediately too, as I think this is what will bring up your panels. If not...
~Choose "Application Autostart", check the box next to "Xfce Settings Helper"

Now when you log out, make sure the box is checked to "Save this session" if you had earlier set it to "prompt".

---

### Post by jfed on 2011-09-02
> **hhh said:**
> Xfce has several options for starting/saving sessionss, they'reall in the same manager but on different screens. I'm using Debian so their location may differ in Xubuntu, but running it from a terminal or run dialog should bring you to it...```
xfce4-settings-manager
```
~Choose "Sessions and Startup", under General click either "Prompt on logout" or "Save automatically".
~Choose "Session". Make sure Compiz is listed and that "Restart Style" is set to "Immediately". Click the "Save Session" button in the lower left corner. Check if "xfce4-settings-helper" is listed to start Immediately too, as I think this is what will bring up your panels. If not...
~Choose "Application Autostart", check the box next to "Xfce Settings Helper"

Now when you log out, make sure the box is checked to "Save this session" if you had earlier set it to "prompt".

Thanks! This did the trick, now when I start up everything is normal.

---

