---
title: "Adobe Air Crashing on Jaunty x64"
date: 2009-04-29
forum: General Help
---

### Post by xrecar on 2009-04-29
Hey everyone, I would like to see if anyone is able to help me here. I managed to install Adobe Air on my ubuntu jaunty x64 today, however, it still has a problem: it crashes when it's about to install an app. When I open AIR via terminal this is the output I get:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/share/themes/Dust/gtk-2.0/gtkrc:709: error: unexpected identifier `highlight_shade', expected character `}'
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

```

I tried by prefixing the launch with 'GTK_PATH=/usr/lib32/gtk-2.0' which didn't work via termianl and made my sytem crash when aded the prefix to the launcher as "GTK_PATH=/usr/lib32/gtk-2.0" "launcher goes here"

Anyone has an Idea? I really want to try tweetdeck and twhirl.

thank a lot in advance.

---

### Post by xrecar on 2009-04-30
Ok, so I'm not happy with this... I have tried everything that has compe up to my head and followed the tutorials placed here... keep on getting these errors

---

### Post by xrecar on 2009-04-30
Oh something else I had to add: whe trying to install any app from the website it downloads, but fails to open the installer

---

### Post by sistarbliss on 2009-05-23
> **xrecar said:**
> Oh something else I had to add: whe trying to install any app from the website it downloads, but fails to open the installer

I'm having the same problem.  Hmmm...

---

### Post by xrecar on 2009-12-25
Update: Adobe AIR 2 came out. It's still in beta, but it adresses this. Works excellent here.

---

