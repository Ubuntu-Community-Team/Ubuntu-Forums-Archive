---
title: "Gnome theme inconsistency"
date: 2006-09-30
forum: Desktop Environments
---

### Post by SirPecanGum on 2006-09-30
Why do some windows not adhere to the same theme as other windows in Gnome. For example, I am using the Gilouche theme with Tango icons but Synaptic, Opera, Gedit (sometimes) and a few others do not or do not always present themselves with this theme. Any ideas?

---

### Post by chavo on 2006-09-30
You run synaptic as root, so it will use the theme in root user's preference. I'm also assuming the gedit theme changes when you run it as root. You can change the root theme I think by running gnome-theme-manager as root. I personally prefer apps run as root to use a different theme and color scheme, it reminds me that I'm running as root and to be careful.
Opera uses QT to draw it's widgets so it can't use the GTK theme.

---

### Post by SirPecanGum on 2006-09-30
You know what? I'm a real dummy! I have noticed that root windows are different and like you, prefer it that way to keep things clear on the desktop. It didn't even occur to me the Synaptic is running as root. Doh! What a dummy.

Thank you very much for your help. It probably would have taken me weeks/months/years to figure it out!

---

### Post by ardchoille on 2006-09-30
If you wanted root apps to run with the same theme as the user is using, you can always launch:

```

gksu gnome-theme-manager

```

and set up the same theme as the user is using. That way, the root apps will look the same as user apps.

---

### Post by SirPecanGum on 2006-09-30
Thank you, I have just installed gtk2-engines-gtk-qt and it has (I think I am right in crediting it) much improved the appearance of Opera and Skype.

---

