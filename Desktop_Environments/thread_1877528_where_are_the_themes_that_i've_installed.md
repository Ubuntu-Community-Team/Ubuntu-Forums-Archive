---
title: "where are the themes that i've installed?"
date: 2011-11-08
forum: Desktop Environments
---

### Post by Sifro on 2011-11-08
Hello,

i installed some gnome themes through 

> apt-get install gnome-themes*

but i can't find them under Settings -> Themes (may be a little different, i'm transliatin from italian)... i just have the default Adwaita, Highcontrast and HighcontrastInverse...

Where are they? How can i enable them?

I'm using Gnome SHell

THanks!

---

### Post by mcduck on 2011-11-08
If you want to select individual theme components to use (for GTK, icons, and window borders) you need to use the [Gnome Tweak Tool]("apt:gnome-tweak-tool").

However it's quite likely that the theme package you installed contains GTK2 themes, while most of your programs are actually using GTK3 now. So the old themes are unlikely to work. You might want to look for some interesting themes from the GTK3 section at gnome-look.org instead. (if possible, get ones that include both GTK2 and GTK3 support so both old and new programs will look the same)

---

### Post by Sifro on 2011-11-09
perfect, very clear, thanks =)

---

### Post by carloslosgrande on 2011-11-09
McDuck - thank you very much, that gnome tweak tool is just what I was looking for!

---

