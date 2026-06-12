---
title: "how to change default font for gnome?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by bzimage on 2006-03-17
some application do not follow my configuration at menu->system->preference->font, so how to set the default?

I ever known to edit gtkrc, but doesn't exist now

---

### Post by blackrim on 2006-03-17
what apps don't change? sometimes, this can be the result of using an app from a different windowing library (Qt instead of GTK2).

---

### Post by bzimage on 2006-03-17
apps like time&date config, synaptic ...

---

### Post by Xian on 2006-03-17
[QUOTE=bzimage]apps like time&date config, synaptic ...[/QUOTE]

You'll have to change the default font(s) for the admin user.
Then it should work fine.

---

### Post by bzimage on 2006-03-18
[QUOTE=Xian]You'll have to change the default font(s) for the admin user.
Then it should work fine.[/QUOTE]

can we login into gnome as root, and change the fonts?

---

### Post by Xian on 2006-03-18
[QUOTE=bzimage]can we login into gnome as root, and change the fonts?[/QUOTE]

Heh, not a good method. You should simply run the individual programs you need as admin and that will get the job done. For example, to change the default fonts for the admin user open a terminal and issue the command below:

$ sudo gnome-font-properties

---

### Post by leech on 2006-03-18
My question would be, is this a font that you installed yourself in .fonts?  If so, then you'll need to install it in the system wide folder, unfortunately at the moment it slips my mind where that is.  It's changed too many times.  It used to be just /usr/share/fonts, or /usr/X11R6/fonts, etc.  

I do know it's the same thing with themes that you install yourself, you have to copy them into /usr/share/theme or it won't work with Synaptic.

Leech

---

### Post by bzimage on 2006-03-19
thank you all so much

---

