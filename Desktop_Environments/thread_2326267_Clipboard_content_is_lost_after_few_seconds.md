---
title: "Clipboard content is lost after few seconds"
date: 2016-05-30
forum: Desktop Environments
---

### Post by ami7878 on 2016-05-30
In the past month the content of my clipboard (after doing CTRL-C) is saved for pasting for only a few seconds. If I logout and login again, this is fixed but after some time it happens again.

Is there a setting for the clipboard?

I'm using Ubuntu 14.04.4

Thanks.

---

### Post by oldrocker99 on 2016-05-30
Try this:```
apt-get install diodon
```

Diodon is a clipboard manager, which does save your last few clipboard selections.

---

### Post by ami7878 on 2016-06-01
I've installed diodon but it doesn't seems to work. It shows in the taskbar but history list stays empty. I'm back with my original problem.

---

### Post by CantankRus on 2016-06-01
Diodon seems to be a bit buggy here.
Try glipper...
```
sudo apt-get install glipper
```
May not show in dash.
To run hit alt+F2 and run the command "glipper".

---

### Post by ami7878 on 2016-06-02
I've installed glipper and it works but my original issue wasn't solved. I have the history of the clipboard but after few seconds, the current CTRL-C is empty. Glipper lets me select it again what ease a bit but still annoying.

---

### Post by CantankRus on 2016-06-02
The only time I see that behaviour is when this dconf setting returns "false" (default is true) 
and then only when I close the application where I copied from.
```
gsettings get org.gnome.settings-daemon.plugins.clipboard active
```

Set to true...
```
gsettings reset org.gnome.settings-daemon.plugins.clipboard active
```

---

### Post by vasa1 on 2016-06-02
> **CantankRus said:**
> The only time I see that behaviour is when this dconf setting returns "false" (default is true) 
and then only when I close the application where I copied from.
```
gsettings get org.gnome.settings-daemon.plugins.clipboard active
```
...
Is "active" needed at the end of that code?

---

### Post by CantankRus on 2016-06-02
> **vasa1 said:**
> Is "active" needed at the end of that code?

Yes. :P

---

### Post by vasa1 on 2016-06-02
Thanks, the only "daemon" ones I see in Lubuntu 16.04 are these:```
$ gsettings list-recursively | grep -i daemon
org.blueman.general notification-daemon true
org.blueman.general notification-daemon true
org.gnome.settings-daemon.plugins.gdu-sd active true
org.gnome.settings-daemon.plugins.gdu-sd priority 1

```But the main application for me that causes issues without a proper clipboard manager is LibreOffice. Its devs are trying to fix that: [https://bugzilla.redhat.com/show_bug.cgi?id=1240591#c1](https://bugzilla.redhat.com/show_bug.cgi?id=1240591#c1).

---

