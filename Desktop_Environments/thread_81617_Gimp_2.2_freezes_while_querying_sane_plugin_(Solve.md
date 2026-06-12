---
title: "Gimp 2.2 freezes while querying sane plugin (Solved, just be patient on first boot.)"
date: 2005-10-24
forum: Desktop Environments
---

### Post by nbcthreat on 2005-10-24
Fresh install of Breezy, with updates, I attempt to open Gimp and it locks up while attempting to query sane. Here's the CLI output before lockup.

```
david@eris:~$ gimp --verbose
INIT: gimp_load_config
Parsing '/etc/gimp/2.0/gimprc'
Parsing '/home/david/.gimp-2.2/gimprc'
gimp_composite: use=yes, verbose=no
Processor instruction sets: +mmx +sse +sse2 -3dnow -altivec -vis
Adding theme 'Default' (/usr/share/gimp/2.0/themes/Default)
Adding theme 'Small' (/usr/share/gimp/2.0/themes/Small)
Writing '/home/david/.gimp-2.2/themerc'
INIT: gimp_initialize
INIT: gimp_real_initialize
INIT: gui_initialize_after_callback
INIT: gimp_restore
INIT: gui_restore_callback
GimpClipboard: writable pixbuf format: image/png
GimpClipboard: writable pixbuf format: image/x-icon
GimpClipboard: writable pixbuf format: image/bmp
GimpClipboard: writable pixbuf format: image/x-bmp
GimpClipboard: writable pixbuf format: image/x-MS-bmp
GimpClipboard: writable pixbuf format: image/jpeg
INIT: gimp_real_restore
Querying plug-in: '/usr/lib/gimp/2.0/plug-ins/xsane'


```

OK. Well, I'm an idiot. It finished starting while I was writing this. :-) Patience, grasshopper. I'll leave this as a warning for the impatient.

---

### Post by Irony on 2005-10-25
I get the same message but patience doesn't work.

I've uninstalled xsane which solves the problem, however ubuntu-desktop is also uninstalled. Reinstalling ubuntu-desktop however reinstalls xsane which stops gimp again.

What does ubuntu-desktop actually do?

---

### Post by Maggot on 2006-04-26
Not to bump an old Thread but after a fresh install of 5.10 and updates, my GIMP was freezing at the xsane plugin.

I noticed in /usr/lib/gimp/2.0/plug-ins the symbolic link to xsane was ../../../bin/xsane

a whereis xsane yielded /usr/bin/xsane so I created a symbolic link in /bin

Still froze.

I just simply removed the link in the plug-ins directory because I didn't need it anyway.

Weird stuff.

edit:  Oh wait...just realized ../../../bin was probably /usr/bin 

Duh. :D

---

### Post by louca on 2006-04-26
exactly.. how long did this take?

i got it in another workspace stuck there and nothing is coming up inside the window when i check back.

i just made a copy of the xsane file called xsanebackup and then deleted the xsane file. works like a dream

what was it for anyway? :?

---

