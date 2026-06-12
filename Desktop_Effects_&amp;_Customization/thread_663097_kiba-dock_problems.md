---
title: "kiba-dock problems"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by Phil420 on 2008-01-09
when i try to install the kiba-dock plugins i get this
```

        then mv -f ".deps/dbus.Tpo" ".deps/dbus.Plo"; else rm -f ".deps/dbus.Tpo"; exit 1; fi
rm: cannot remove `.libs/dbus.o': Permission denied
rm: cannot remove `.libs/dbus.o': Permission denied
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libxml2 -I/usr/include/akamaru -I/usr/include/librsvg-2 -I/usr/local/include/kiba-dock -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -I../dock -I/usr/local/include -g -O2 -MT dbus.lo -MD -MP -MF .deps/dbus.Tpo -c dbus.c  -fPIC -DPIC -o .libs/dbus.o
Assembler messages:
Fatal error: can't create .libs/dbus.o: Permission denied
make[3]: *** [dbus.lo] Error 1
make[3]: Leaving directory `/home/phil/kiba-dock/kiba-plugins/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/phil/kiba-dock/kiba-plugins/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/phil/kiba-dock/kiba-plugins'
make: *** [all] Error 2

```
Any idea?
thanks!

---

### Post by rune0077 on 2008-01-09
You probably need to run the install command with sudo

---

### Post by Phil420 on 2008-01-09
> **rune0077 said:**
> You probably need to run the install command with sudo

yea i did that but with that error it didn't install properly and kiba-dock doesn't work good.

---

### Post by rune0077 on 2008-01-09
Weird. Your best bet is to search for something like "installing kiba dock" here on the forums. There's a How to guide somewhere that I used once, when I still used the dock.

Edit: here it is: [http://ubuntuforums.org/showthread.php?t=554127&highlight=installing+kiba+dock](http://ubuntuforums.org/showthread.php?t=554127&highlight=installing+kiba+dock)

---

### Post by Phil420 on 2008-01-09
> **rune0077 said:**
> Weird. Your best bet is to search for something like "installing kiba dock" here on the forums. There's a How to guide somewhere that I used once, when I still used the dock.

Edit: here it is: [http://ubuntuforums.org/showthread.php?t=554127&highlight=installing+kiba+dock](http://ubuntuforums.org/showthread.php?t=554127&highlight=installing+kiba+dock)

lol thats exactly what i used! it's really a great how to it worked well until this error.

---

### Post by rune0077 on 2008-01-09
Oh okay, that's strange, I'm pretty sure that one worked for me. Try posting your problem in that thread and hope somebody still reads it.

---

