---
title: "top and bottom bars have disappeared"
date: 2009-04-04
forum: Desktop Environments
---

### Post by kitfer on 2009-04-04
Hello

I'm quite new to Ubuntu to I don't know what everything is called nor do I know my way around it very well, basically my problem is I installed the 283 reccomended updates plus a few other programs like k3b and some games and now the bars along the top and bottom of the screen that let me do everything have both disappeared, they aren't on auto-hide.
I'd prefer to not reformat the laptop so any help fixing this problem would be greatly appreciated.


Cheers

---

### Post by vegetarianshrimp on 2009-04-04
press Alt+F2, type in "gnome-panel" (without the quotes), and click run

---

### Post by UbuntuNerd on 2009-04-04
if the command above didn't work you can try this one, it should restore your panels:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by kitfer on 2009-04-04
Hi there

alt f2 didn't seem to do anything

---

### Post by vegetarianshrimp on 2009-04-04
> **kitfer said:**
> Hi there

alt f2 didn't seem to do anything
Do you mean pressing alt f2 on the keyboard or entering gnome-panel and clicking run?
If you  mean the first one, you have to press the both down at the same time.
If you mean the second one, do what UbuntuNerd suggested.

---

### Post by UbuntuNerd on 2009-04-04
> **kitfer said:**
> Hi there

alt f2 didn't seem to do anything

try Ctrl+Alt+f1 and if you get the command prompt. Log in and use the commands, hit Alt+f7 to get back to your desktop

---

### Post by kitfer on 2009-04-04
tried going into the text-line user interface by useing Ctrl+Alt+F1 and typed in the commands ubuntunerd said but still no joy, I also removed a couple of programs (like skype and other programs I figured I wouldn't use) is it possible I accidently removed the panel? if so how can I install it from the text-line interface?

---

### Post by kitfer on 2009-04-04
turns out I deleted it when I deleted evolution email client, so I used the apt-get command to reinstall gnome-panel, rebooted and everything worked.
Thanks for your help

---

### Post by UbuntuNerd on 2009-04-04
if you uninstalled evolution your probably removed part of your desktop which is closely integrate with evolution.

---

