---
title: "Dead Desktop"
date: 2008-06-02
forum: Desktop Environments
---

### Post by MotherMayI on 2008-06-02
I don't know how else to describe my current problem with Xubuntu, besides describing it as a 'dead desktop'.

The entire operating system, and xfce besides this one problem, is working fine. The taskbar, the top bar and all its menus are all functioning correctly.

The problem is that there are no icons on the desktop, and when I right click on the deadspace on the background the right click menu does not come up. The background, on both screens, is also baby blue (my set desktop image does not show up).

What could be causing this?

---

### Post by kshane on 2008-06-02
> **MotherMayI said:**
> I don't know how else to describe my current problem with Xubuntu, besides describing it as a 'dead desktop'.

The entire operating system, and xfce besides this one problem, is working fine. The taskbar, the top bar and all its menus are all functioning correctly.

The problem is that there are no icons on the desktop, and when I right click on the deadspace on the background the right click menu does not come up. The background, on both screens, is also baby blue (my set desktop image does not show up).

What could be causing this?

This is a little over my head, but I think the problem lies with your xfce desktop manager.  Perhaps just a re-install will help?  I am unfamiliar with Xubuntu...

Kevin

---

### Post by mali2297 on 2008-06-02
Have you used the file manager Nautilus?

If so, open a terminal and kill the process with the command
```

pkill nautilus

```

Then start Xfce's desktop manager with
```

xfdesktop &

```

If you want to use Nautilus within Xfce, start it with
```

nautilus --no-desktop

```
(Change the command entry for the launcher.)

---

### Post by MotherMayI on 2008-06-02
> **mali2297 said:**
> Have you used the file manager Nautilus?

If so, open a terminal and kill the process with the command
```

pkill nautilus

```

Then start Xfce's desktop manager with
```

xfdesktop &

```

If you want to use Nautlius within Xfce, start it with
```

nautilus --no-desktop

```
(Change the command entry for the launcher.)

Thanks a lot, that worked like a charm - Good guess work heh, I forgot to mention that it occurred after running Nautilus.

---

