---
title: "Multiple Strange Problems"
date: 2007-10-04
forum: Desktop Environments
---

### Post by dedtr9 on 2007-10-04
I am having several different problems with Ubuntu:

1. There are several new logins i haven't added - they are named ossec, ossece, ossecm, ossecr.

2. Music and videos wont play - the application freezes 

3. Firefox crashes ?randomly?. I have noticed it crash on gmail, and radiohead's website, but it was worked sometimes, and not others.  It just closes itself, and acts like nothing happened

4. Akregator has crashed twice. It pops up the window with something about bug reports.

5. As a side-note -I cannot get VMware to install using the package manager. It downloads, then says please uninstall vmware fully. I cannot find their forums or anything of that sort on their website, and nothing I do will work. 

Thanks 
   dedtr9

---

### Post by overlord.gaurav on 2007-10-04
Which version of Ubuntu are you using?

---

### Post by dedtr9 on 2007-10-04
sorry - Ubuntu 7.04, fiesty

Update-

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ded"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ded-desktop:/tmp/.ICE-unix/12445
Initializing gnome-mount extension

** (nautilus:12510): WARNING **: Failed to initialize libhal context: (null) : (null)

** (nautilus:12510): WARNING **: Could not initialize hal context


(nautilus:12510): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(nautilus:12510): GLib-GObject-CRITICAL **: g_object_weak_ref: assertion `G_IS_OBJECT (object)' failed
Shutting down gnome-mount extension
Stacktrace:


Native stacktrace:

	mono [0x818f7de]
	mono [0x8171be4]
	[0xffffe440]
	mono(mono_method_signature+0xdd) [0x8109334]
	mono [0x81117eb]
	mono [0x8112399]
	mono(mono_class_init+0xa26) [0x8112dd9]
	mono(mono_class_init+0x331) [0x81126e4]
	mono(mono_class_vtable+0x131) [0x80b21c3]
	mono(mono_object_new+0x18) [0x80b51bd]
	mono(mono_type_get_object+0x297) [0x819e8f6]
	mono(mono_class_vtable+0x820) [0x80b28b2]
	mono(mono_class_vtable+0x809) [0x80b289b]
	mono(mono_object_new+0x18) [0x80b51bd]
	mono(mono_runtime_init+0xf2) [0x80ee80a]
	mono [0x8172e7f]
	mono(mono_main+0x1324) [0x805bafa]
	mono [0x80596c6]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d8bebc]
	mono [0x8059621]

(gnome-panel:12509): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -20 and height 24
kdeinit: Shutting down running client.

(process:12541): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed

(gnome-cups-icon:12513): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

But now it logs on all the way...


Edit2: Firefox stopped opening ;when i run it in a command line, it says "segmentation fault (core dumped)". It works if i run it in safe mode and disable extensions, but only if i do things slowly.

Could someone help?

---

