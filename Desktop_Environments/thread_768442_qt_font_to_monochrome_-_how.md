---
title: "qt font to monochrome - how?"
date: 2008-04-26
forum: Desktop Environments
---

### Post by itarato on 2008-04-26
Hi!

I've got a problem with Ubuntu 8.04 at qt-config section. I have an lcd display, so i installed msttfonts properly, and use those types in everywhere. (monochrome) But some application use cleartype fonts: (Skype, xine ... (qt) and terminal(!))
I set the reliable fonts in qt3-config and qt4-config, but those are still cleartype. (Even the qt-config panles too.) I modify my root's font config, but it didt work.

Its a bug, or if not, how can i set monochrome fonts for all apps?

Thanks!

---

### Post by necromanga on 2009-08-15
you just need .fonts.conf file in your home/user/ folder.

here is my .fonts.conf :

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="rgba" mode="assign">
<const>rgb</const>
</edit>
<edit name="hinting" mode="assign">
<bool>true</bool>
</edit>
<edit name="hintstyle" mode="assign">
<const>hintfull</const>
</edit>
<edit mode="assign" name="antialias" >
<bool>false</bool>
</edit>
</match>
</fontconfig>

```

---

