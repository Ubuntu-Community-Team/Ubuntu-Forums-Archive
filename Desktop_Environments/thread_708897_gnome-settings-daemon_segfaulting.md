---
title: "gnome-settings-daemon segfaulting"
date: 2008-02-26
forum: Desktop Environments
---

### Post by Ambush Commander on 2008-02-26
One day, (probably after upgrading Ubuntu, though I'm not sure), an ominous window popped up, stating that the settings manager had restarted too many times, and was not able to start. My theme had changed to blue (the Ubuntu default is a coffee color), I could open my Appearance dialogue, and things looked ugly, though functional.

Annoyed, I attempt to boot up gnome-settings-daemon from the command line and was greeted with this error message:

```
*** glibc detected *** gnome-settings-daemon: free(): invalid pointer: 0x081162a8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74a6d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb74aa800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7719961]
/usr/lib/libgstreamer-0.10.so.0[0xb78574c5]
/usr/lib/libgstreamer-0.10.so.0(gst_registry_xml_read_cache+0x113)[0xb78581a3]
/usr/lib/libgstreamer-0.10.so.0[0xb77fa7c7]
/usr/lib/libgstreamer-0.10.so.0[0xb77fbd2a]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x1f1)[0xb771f8b1]
/usr/lib/libgstreamer-0.10.so.0(gst_init_check+0xb1)[0xb77fb791]
/usr/lib/libgstreamer-0.10.so.0(gst_init+0x32)[0xb77fb912]
gnome-settings-daemon[0x806bd0b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb77ced41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x98a)[0xb77b529a]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb77b578f]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb77b5940]
gnome-settings-daemon(acme_volume_new+0x33)[0x806b8e3]
gnome-settings-daemon[0x805e52b]
gnome-settings-daemon(gnome_settings_module_start+0x6d)[0x805cd2d]
gnome-settings-daemon[0x8058923]
gnome-settings-daemon[0x805898f]
/usr/lib/libglib-2.0.so.0[0xb7710551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb771211c]
/usr/lib/libglib-2.0.so.0[0xb771555f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7715909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b2a9e4]
gnome-settings-daemon(main+0x164)[0x8055bd4]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7453050]
gnome-settings-daemon[0x8054a81]
======= Memory map: ========
08048000-08072000 r-xp 00000000 08:06 1884780    /usr/lib/gnome-control-center/gnome-settings-daemon
08072000-08074000 rw-p 00029000 08:06 1884780    /usr/lib/gnome-control-center/gnome-settings-daemon
08074000-0811d000 rw-p 08074000 00:00 0          [heap]
b6200000-b6221000 rw-p b6200000 00:00 0 
b6221000-b6300000 ---p b6221000 00:00 0 
b6317000-b6321000 r-xp 00000000 08:06 2195523    /lib/libgcc_s.so.1
b6321000-b6322000 rw-p 0000a000 08:06 2195523    /lib/libgcc_s.so.1
b6322000-b6366000 r--p 00000000 08:06 1638571    /home/ezyang/.gstreamer-0.10/registry.i486.xml
b6366000-b636d000 r-xp 00000000 08:06 1869302    /usr/lib/libfam.so.0.0.0
b636d000-b636e000 rw-p 00006000 08:06 1869302    /usr/lib/libfam.so.0.0.0
b636e000-b6374000 r-xp 00000000 08:06 2195482    /lib/libacl.so.1.1.0
b6374000-b6375000 rw-p 00005000 08:06 2195482    /lib/libacl.so.1.1.0
b6375000-b6378000 r-xp 00000000 08:06 2195488    /lib/libattr.so.1.1.0
b6378000-b6379000 rw-p 00002000 08:06 2195488    /lib/libattr.so.1.1.0
b6388000-b6394000 r-xp 00000000 08:06 1916956    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6394000-b6395000 rw-p 0000b000 08:06 1916956    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6395000-b6396000 rw-p b6395000 00:00 0 
b6396000-b6397000 ---p b6396000 00:00 0 
b6397000-b6b97000 rw-p b6397000 00:00 0 
b6b97000-b6b98000 r-xp 00000000 08:06 1886586    /usr/lib/gconv/ISO8859-1.so
b6b98000-b6b9a000 rw-p 00000000 08:06 1886586    /usr/lib/gconv/ISO8859-1.so
b6b9a000-b6bd9000 r--p 00000000 08:06 1917818    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6bd9000-b6bda000 r--p 00000000 08:06 1917823    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6bda000-b6bdb000 r--p 00000000 08:06 1917826    /usr/lib/locale/en_US.utf8/LC_TIME
b6bdb000-b6cbb000 r--p 00000000 08:06 1917817    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6cbb000-b6cc4000 r-xp 00000000 08:06 2229352    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6cc4000-b6cc6000 rw-p 00008000 08:06 2229352    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6cc6000-b6cce000 r-xp 00000000 08:06 2229354    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6cce000-b6cd0000 rw-p 00007000 08:06 2229354    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6cd0000-b6cd7000 r-xp 00000000 08:06 2229350    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b6cd7000-b6cd9000 rw-p 00006000 08:06 2229350    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b6cd9000-b6cdd000 rw-p b6cd9000 00:00 0 
b6cdd000-b6d13000 r-xp 00000000 08:06 2195581    /lib/libsepol.so.1
b6d13000-b6d14000 rw-p 00035000 08:06 2195581    /lib/libsepol.so.1
b6d14000-b6d1e000 rw-p b6d14000 00:00 0 
b6d1e000-b6d6d000 r-xp 00000000 08:06 2244613    /usr/lib/libgcrypt.so.11.2.3
b6d6d000-b6d6f000 rw-p 0004e000 08:06 2244613    /usr/lib/libgcrypt.so.11.2.3
b6d6f000-b6d70000 rw-p b6d6f000 00:00 0 
b6d70000-b6d73000 r-xp 00000000 08:06 2244720    /usr/lib/libgpg-error.so.0.3.0
b6d73000-b6d74000 rw-p 00002000 08:06 2244720    /usr/lib/libgpg-error.so.0.3.0
b6d74000-b6d83000 r-xp 00000000 08:06 2245088    /usr/lib/libtasn1.so.3.0.9
b6d83000-b6d84000 rw-p 0000e000 08:06 2245088    /usr/lib/libtasn1.so.3.0.9
b6d84000-b6d88000 r-xp 00000000 08:06 1869082    /usr/lib/libORBitCosNaming-2.so.0.1.0
b6d88000-b6d89000 rw-p 00003000 08:06 1869082    /usr/lib/libORBitCosNaming-2.so.0.1.0
b6d89000-b6d90000 r-xp 00000000 08:06 1869320    /usr/lib/libgailutil.so.18.0.1
b6d90000-b6d91000 rw-p 00006000 08:06 1869320    /usr/lib/libgailutil.so.18.0.1
b6d91000-b6d92000 rw-p b6d91000 00:00 0 
b6d92000-b6db0000 r-xp 00000000 08:06 1869298    /usr/lib/libexpat.so.1.0.0
b6db0000-b6db2000 rw-p 0001e000 08:06 1869298    /usr/lib/libexpat.so.1.0.0
b6db2000-b6ddf000 r-xp 00000000 08:06 1869714    /usr/lib/libpangoft2-1Aborted (core dumped)

```

What do I need to do?

**Update**: I reinstalled glib and gtk, and now my background doesn't work, and the trash, fast user switch and deskbar applets stopped working (the panel tells me that the applet has errors, and asks me if I'd like to remove them). The daemon still segfaults.

---

