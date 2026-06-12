---
title: "Change gnome application icon"
date: 2007-04-02
forum: Desktop Environments
---

### Post by jej2003 on 2007-04-02
How can you change the gnome applications menu icon?  I tried to right cick and edit the menu, that didn't work and I tried to change the fie in /usr/share/icons/hicolor/48x48/apps/distributor-logo.png and no go, and I changed /usr/share/hwdb-client/ubuntu-logo.png and again no go.  Is there a way to change this?

---

### Post by aysiu on 2007-04-02
I don't know what version you're using (5.10, 6.06, 6.10), but maybe [this](http://ubuntuforums.org/showthread.php?t=167658) might help.

---

### Post by ComplexNumber on 2007-04-03
> **jej2003 said:**
> How can you change the gnome applications menu icon?  I tried to right cick and edit the menu, that didn't work and I tried to change the fie in /usr/share/icons/hicolor/48x48/apps/distributor-logo.png and no go, and I changed /usr/share/hwdb-client/ubuntu-logo.png and again no go.  Is there a way to change this?
the application menu icon comes from the start-here icon in the icon theme that you're using, not the distributor logo. the distributor-logo is merely a link to the start-here icon in most themes. however, some themes don't have the start-here icon, but use that of the theme that it inherits. if not, it uses that of hicolor or gnome.
what theme are you currently using?

---

### Post by jej2003 on 2007-04-03
currently I am using an icon theme called OSX and a theme called T-ish-Ubuntulooks

---

### Post by ComplexNumber on 2007-04-03
> **jej2003 said:**
> currently I am using an icon theme called OSX and a theme called T-ish-Ubuntulooks
there seems to be something slightly wrong with the OS X icon theme. for example, when i change the line "Inherit=..." to "inherit=SnowIsh", it seems to use the snowish icon for folders even though it has its own. thats not right. it also has its own start-here icon, but it doesn't use it. thats also not right. i can't pinpoint the error.
HOWEVER, what you need to do is change the following icon to what you want the application menu to be:
/usr/share/icons/Tango/scalable/places/start-here.svg

---

### Post by jej2003 on 2007-04-04
Thanks, are there any places that provide svg icons?  everything I have are png

---

### Post by mrmonday on 2007-04-04
Search the internet, or use inkscape, and import it. Try the bitmap tracer, as it will give better results, but needs a lot of tweaking. If you don't use the bitmap tracer it makes a link, so you will have to keep the files together.

---

### Post by mrmonday on 2007-04-04
.

---

