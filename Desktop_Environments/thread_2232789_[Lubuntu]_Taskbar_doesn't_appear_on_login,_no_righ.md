---
title: "[Lubuntu] Taskbar doesn't appear on login, no right-click menu"
date: 2014-07-04
forum: Desktop Environments
---

### Post by whyigotta on 2014-07-04
I was trying to install LibreOffice and in the process, the system crashed, when I rebooted there was no taskbar. I rebooted again to no change. I tried  'lxpanel restart' in the terminal and got the error 'Gtk-Warning cannot open display',trying  'pcmanfm' returns the same error, 'killall lxpanel' returns 'no process  found'.

I also tried a command beginning with 'cp and then listing two directories', I'm not sure what it's intent was, but it didn't work anyway, I forget the error, if someone posts the command again I'll post the error. Everything I read online I either didn't understand or didn't work. 

The computer is a Dell Latitude Labtop, Pentium M, 1.2 GB RAM. Sorry if I broke any of the forum rules, I'm a Linux noob, can anyone help me get the taskbar back?

Thanks for any help

---

### Post by ibjsb4 on 2014-07-04
The command is not 'lxpanel restart', but just ..

```
lxpanel
```

---

### Post by whyigotta on 2014-07-04
That gives the same 'Gtk-Warning' error

---

### Post by Bucky Ball on 2014-07-04
Odd. Depending on what spin you are using, you may be using xfdesktop4. Try that in a terminal, just that. If you have no icons and no taskbar it is possibly to do with your desktop manager. If not xfdesktop4, see if you can discover what it's using. lxdesktop?

```
xfdesktop
```

---

### Post by whyigotta on 2014-07-04
Finally fixed it. For some reason it didn't load the taskbar because the disk was full from the attempt to install LibreOffice. I ran apt-get autoremove (though first I had to run apt-get update), that removed the remnants of LibreOffice, then I rebooted and the taskbar was there.

Thanks for the help guys, if I hadn't tried what you said I never would have seen the 'disk full' error

---

