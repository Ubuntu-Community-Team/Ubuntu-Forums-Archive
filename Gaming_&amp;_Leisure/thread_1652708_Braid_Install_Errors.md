---
title: "Braid Install Errors"
date: 2010-12-25
forum: Gaming &amp; Leisure
---

### Post by sleapz on 2010-12-25
So I installed Braid (.bin) using the following commands:

[B]chmod a+x braid-linux-build2.run.bin 
sudo ./braid-linux-build2.run.bin [/B]

And got the following output in the terminal window:

[B]/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(<unknown>:17324): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:17324): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:17324): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:17324): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:17324): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:17324): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
[/B]
Failures and errors are never a good thing but I went ahead and tried to run the game anyway and all that happened is my screen went blank for a couple seconds, returned to the desktop, went blank for a couple of seconds, and then returned to the desktop at which point nothing else happened.  I'm a 'nix newb so be gentle please. :)

---

### Post by pagemaker on 2010-12-27
Exactly the same problem here... except the game runs fine.

But when I log off and then back on, the shortcut dissapears from the "Games" menu...

---

### Post by clayton2 on 2010-12-28
I got the same errors, on Maverick 64-bit.

---

### Post by Perfect Storm on 2010-12-28
ELF Class errors means you're using the wrong libraries. Braid is a 32-bit game. So you have to install the 32-libs on your 64-bit system.

Install ia32-libs should do it.

---

