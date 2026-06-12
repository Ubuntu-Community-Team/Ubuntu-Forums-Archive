---
title: "No 'header bars' for the windows"
date: 2009-06-07
forum: General Help
---

### Post by Jaded Misanthrope on 2009-06-07
For some reason (probably uninstalling a package I wasn't meant to by accident), the windows in my Ubuntu 8.10 installation no longer have what I've coined 'header bars' -- the things with the window's title, the minimise, maximise and close buttons, and so on. xkill from the terminal doesn't close them, nor does alt+f4. I can, however, open new windows from either the applications, places or system menus or through GNOME do.

How would I restore the 'header bars'?

---

### Post by Tipped OuT on 2009-06-07
Have you tried alt+f4 ```
compiz --replace
```  Also, try installing emerald and do alt+f4 ```
 emerald --replace
```

---

### Post by Jaded Misanthrope on 2009-06-07
I installed Compiz and ran compiz --replace, and I have the header bars back, which is great. Unfortunately, I can't enable compositing using xcompmgr for GNOME-do and I'm stuck with the default GNOME-do appearance. I don't think I'll be able to uninstall Compiz again without losing the bars. I'll try it, since it's a simple matter to fix, but I'm not too hopeful. :(

edit: well, some experiments in Synaptic and a little studying of the package descriptions leads me to believe that removing compiz-gnome causes the issue of the missing title bars. This changes the issue somewhat: how might I remove Compiz under Ubuntu 8.10?

---

### Post by Tipped OuT on 2009-06-08
> **Jaded Misanthrope said:**
> I installed Compiz and ran compiz --replace, and I have the header bars back, which is great. Unfortunately, I can't enable compositing using xcompmgr for GNOME-do and I'm stuck with the default GNOME-do appearance. I don't think I'll be able to uninstall Compiz again without losing the bars. I'll try it, since it's a simple matter to fix, but I'm not too hopeful. :(

edit: well, some experiments in Synaptic and a little studying of the package descriptions leads me to believe that removing compiz-gnome causes the issue of the missing title bars. This changes the issue somewhat: how might I remove Compiz under Ubuntu 8.10?

Compiz helps manage the window borders (headers) with the decoration plug-in. This is why when you uninstall Compiz, the window borders (headers) go away. I really don't see why you'd want to uninstall it, if you do not want any effects, just disable the plug-ins. If you can't enable compositing for GNOME-DO, then I don't see how removing Compiz would help, because Compiz enables compositing.

---

### Post by Jaded Misanthrope on 2009-06-08
For whatever reason, the compositing provided by Compiz doesn't work with GNOME-do (unless it's not enabled by default; I assumed it was and couldn't find an option for it).

---

### Post by nothingspecial on 2009-06-08
I don`t like window decoration so I remove it. You can manage your windows quicker with the keyboard.

Alt + spacebar                   opens the window menu
Alt + F9                         minimizes
Alt + F4                         closes
Alt + F5                         unmaximizes
Alt + F10                        maximizes
Alt + F8                         resizes (with arrow keys or mouse)
Ctrl + Shift + D                 minimizes all windows
Alt + Tab                        Switches between windows
Ctrl + Alt + Shift + Arrow       Move window to next workspace

Use along with gnome-do and you can chuck your mouse away.

---

### Post by Jaded Misanthrope on 2009-06-08
> **nothingspecial said:**
> I don`t like window decoration so I remove it. You can manage your windows quicker with the keyboard.

Alt + spacebar                   opens the window menu
Alt + F9                         minimizes
Alt + F4                         closes
Alt + F5                         unmaximizes
Alt + F10                        maximizes
Alt + F8                         resizes (with arrow keys or mouse)
Ctrl + Shift + D                 minimizes all windows
Alt + Tab                        Switches between windows
Ctrl + Alt + Shift + Arrow       Move window to next workspace

Use along with gnome-do and you can chuck your mouse away.

While using the keyboard is quicker, I prefer to have the window decoration if only because it looks slightly better.

---

### Post by Keith Hedger on 2009-06-08
If you don't want to use compiz try```
metacity --replace
```
metacity should be the default window manager you may have corrupted it or accidentally uninstalled it.

---

### Post by Rallg on 2009-06-08
Since you raised the topic: Using compiz, how can I make the header bars go away? I have a Dell mini 9, which has limited vertical screen pixels. Gaining the 20 or so pixels occupied by the header bars might be helpful. I can manage the windows by other means. I don't want to remove compiz. Is there a compiz or Gnome setting that I can change (reversible, if I don't like the result)?

---

### Post by Slim Odds on 2009-06-08
Just FYI, they are called "Title Bars".

That might make it easier to find the information that you're looking for.

---

