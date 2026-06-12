---
title: "Top menu bar - GTK problem!"
date: 2009-08-09
forum: Desktop Environments
---

### Post by xX-Felipao-Xx on 2009-08-09
Hi everyone!

Im using a GTK theme and an emerald theme, and if you look at the screenshot I took, in the top bar, in the top-right corner, where my username is shown, there's a mistake in the bar's graphic... you know, It should look black like the rest of the bar.

Any idea on how to fix this?

Thanks in advance :)

[ATTACH]123980[/ATTACH]

---

### Post by arky on 2009-08-09
Looks like the fast-user-switch-applet doesn't like your theme.

---

### Post by bobmendon on 2009-08-09
> **arky said:**
> Looks like the fast-user-switch-applet doesn't like your theme.


Unless you really need it, just remove it from the taskbar.

---

### Post by xX-Felipao-Xx on 2009-08-09
Well, finally did that and removed it from the bar as it seemed to be the only solution.

Thank you :)

---

### Post by gjoellee on 2009-08-09
I son't use GNOME, so could you maybe try this for me...

I have a feeling that the user-switcher applet is a sudo applet, and because of that you have to run the commands shown on the user-switcher applet.

Here are the commands:
```

sudo ln -s ~/.themes /root/.themes

sudo ln -s ~/.icons /root/.icons


```
and plz tell me if it works or not :)

---

