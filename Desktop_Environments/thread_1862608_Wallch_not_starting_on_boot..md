---
title: "Wallch not starting on boot."
date: 2011-10-16
forum: Desktop Environments
---

### Post by darkskye on 2011-10-16
So I haven't seen anyone else with this issue.

I have a clean install of 11.10, and I've installed Wallch.

I can get into preferences, and I can change the startup options. However, after I save the preferences, the startup option is unchecked again.

It's odd, as my other preferences are saved. Only the automatic boot preference doesn't save.

Any help would be greatly appreciated!

-Chris

---

### Post by darkskye on 2011-10-17
Hello all, here's an update. I ran wallch in terminal and tried to adjust the startup options, and it spat back this error.


christopher@christopher-laptop:~$ wallch

(wallch:8797): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(wallch:8797): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(wallch:8797): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(wallch:8797): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
sh: cannot create /home/christopher/.config/autostart/WallchOnBootConstantApp.desktop: Directory nonexistent
Error creating ~/.config/autostart/WallchOnBootConstantApp.desktop. Please check file existnce and permissions.


I'm still not sure what to do, if anyone could help I'd be appreciative.

---

### Post by hakermania on 2011-10-28
Hello darkskey, sorry for the inconvenience, this is a known bug of Wallch and we've already fixed it, although not released it yet. The problem is that Wallch doesn't create itself the path ~/.config/autostart if it doesn't exist.
The solution is very simple. Run this in a terminal:
```

mkdir ~/.config/autostart

```
and then retry adding a start-up option.

---

### Post by lsk3993 on 2011-10-28
> **hakermania said:**
> Hello darkskey, sorry for the inconvenience, this is a known bug of Wallch and we've already fixed it, although not released it yet. The problem is that Wallch doesn't create itself the path ~/.config/autostart if it doesn't exist.
The solution is very simple. Run this in a terminal:
```

mkdir ~/.config/autostart

```and then retry adding a start-up option.
I was also having this problem, this seems to have fixed it. Thanks! :)

---

### Post by hakermania on 2011-10-29
> **lsk3993 said:**
> I was also having this problem, this seems to have fixed it. Thanks! :)

I hope the OP will see this fix too.

---

### Post by dcstar on 2012-02-07
I reported this in Launchpad, so if anyone else searches for it there then they should now find it:

[https://bugs.launchpad.net/ubuntu/+source/wallch/+bug/928211](https://bugs.launchpad.net/ubuntu/+source/wallch/+bug/928211)

---

