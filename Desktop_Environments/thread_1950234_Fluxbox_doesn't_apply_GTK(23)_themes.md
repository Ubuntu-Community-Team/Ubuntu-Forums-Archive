---
title: "Fluxbox doesn't apply GTK(2/3) themes"
date: 2012-03-31
forum: Desktop Environments
---

### Post by basp on 2012-03-31
Hello people,

I don't usually post my problems with Linux in forums, but this problem has been bothering me for years now and no solution has ever worked perfectly.

I have Ubuntu 11.10 with Fluxbox and GTK3.0 installed. I want to use GTK themes, but whatever I do, new themes never apply to my windows.  If I check .gtkrc-2.0 or 3.0, both seem to use the themes I want, but apparently these files don't apply. The themes I've tried were both GTK2 and 3, with same results. LXappearance, gtk-theme-switch2 and gtk-chtheme are capable of changing the icons in my fbpanel so it has to be working to some extent, but all other GTK windows remain the same default. The closest I got was with LXappearance, which could actually make it's own window change theme, but not a single other window.

I think I have read about every single topic ever written about this problem, but most are old and only work for GTK2. Does anyone have suggestions for a solution?

---

### Post by xelion on 2012-08-07
> **basp said:**
> Hello people,

I don't usually post my problems with Linux in forums, but this problem has been bothering me for years now and no solution has ever worked perfectly.

I have Ubuntu 11.10 with Fluxbox and GTK3.0 installed. I want to use GTK themes, but whatever I do, new themes never apply to my windows.  If I check .gtkrc-2.0 or 3.0, both seem to use the themes I want, but apparently these files don't apply. The themes I've tried were both GTK2 and 3, with same results. LXappearance, gtk-theme-switch2 and gtk-chtheme are capable of changing the icons in my fbpanel so it has to be working to some extent, but all other GTK windows remain the same default. The closest I got was with LXappearance, which could actually make it's own window change theme, but not a single other window.

I think I have read about every single topic ever written about this problem, but most are old and only work for GTK2. Does anyone have suggestions for a solution?

bump :(


I am having the exact same issue here. I use Ubuntu 12.04 LTS with FluxBox. I was able to get the good old GTK2 themes to work back in the days, but this fancy GTK3 **** doesn't seem to be working with FluxBox for some reason?
I've installed the gnome-shell environment as well but with no luck:( I'm stuck with "Ambiance" no matter what client I try to switch theme with.
I have even tried to edit the configurations manually through gconf-editor.. but again with no effect!

Please help us out folks!

Jesper

---

### Post by scorpiosnake on 2012-09-05
I am running Ubuntu 12.04 and here is what I do to get gtk3 themes to work in fluxbox.

Go to ~/.fluxbox and open the file startup with gedit (or your favorite text editor).

Add the following line to the file:

```
gnome-settings-daemon &
```

Make sure this is before the line that says:

```
exec fluxbox
```

Save the file. Exit fluxbox and log back in and it should be using the gtk3 theme you have set. To change it you can use system settings - appearance just like you would if you were in Unity. Though if you are using the default Ubuntu Fluxbox menu you can find this in Applications - System - Administration - Gnome Control Center.

---

