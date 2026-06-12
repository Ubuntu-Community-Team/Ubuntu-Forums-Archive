---
title: "Splash screens in Linux?"
date: 2005-06-08
forum: Desktop Environments
---

### Post by erik-the-red on 2005-06-08
How does configuring a splash screen work in Ubuntu?

[http://art.gnome.org/themes/splash_screens/780](http://art.gnome.org/themes/splash_screens/780)

---

### Post by tread on 2005-06-08
[http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)

---

### Post by erik-the-red on 2005-06-10
It turns out that I was looking for the wrong thing.

I thought a splash screen was like the Windows "boot up splash screen."

Do those even exist in Linux?

---

### Post by Rickie on 2005-06-10
[QUOTE=erik-the-red]It turns out that I was looking for the wrong thing.

I thought a splash screen was like the Windows "boot up splash screen."

Do those even exist in Linux?[/QUOTE]
 I'm sure they do, i remember when i used to use Mandrake it had one :)

---

### Post by tread on 2005-06-10
Trp splashy.

---

### Post by Xian on 2005-06-11
Just FYI, [Splashy](http://wiki.nanofreesoft.org/index.php/Splashy) has forked into [Upower](http://wiki.nanofreesoft.org/index.php/Upower).

---

### Post by aysiu on 2005-06-12
You need to [create](http://home.nyc.rr.com/computertaijutsu/grub.html) or find a splash image in the form splash.xpm.gz (it's just an image created in GIMP with an xmp extension that's gzipped). Then, you need to add a line in the /boot/grub/menu.lst:

splashimage (hd0,1)/boot/grub/splash.xpm.gz

I'm assuming your Ubuntu installation is actually at (hd0,1). You can look at other parts of the menu.lst file to see what partition it's at.

---

