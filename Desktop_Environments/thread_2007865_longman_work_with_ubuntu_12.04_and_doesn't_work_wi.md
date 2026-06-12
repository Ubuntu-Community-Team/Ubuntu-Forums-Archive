---
title: "longman work with ubuntu 12.04 and doesn't work with kubuntu 12.04"
date: 2012-06-21
forum: Desktop Environments
---

### Post by forsubhi on 2012-06-21
I have this error when I try to run longman dictionary on kubuntu 12.04 
```
subhi@subhi-pc:~/ldoce5$ ./ldoce5
*** glibc detected *** ./ldoce5-bin: free(): invalid pointer: 0x0936e6d0 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x73e42)[0xf6b2ee42]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZdlPv+0x1f)[0xf533251f]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1b)[0xf531999b]
/usr/lib/i386-linux-gnu/libstdc++.so.6(+0x909dc)[0xf53199dc]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZNSsD1Ev+0x2e)[0xf5319a4e]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(_ZN6Oxygen3Gtk2RC4initEv+0x141)[0xf5415071]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(_ZN6Oxygen10QtSettingsC2Ev+0x408)[0xf540f2b8]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(_ZN6Oxygen5Style8instanceEv+0x77)[0xf5433d37]
/usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so(theme_init+0x2f)[0xf547da5f]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x2136b6)[0xf734a6b6]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_type_module_use+0x99)[0xf6fc97e9]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_theme_engine_get+0x42)[0xf734a7f2]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18dafd)[0xf72c4afd]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e673)[0xf72c5673]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e7e1)[0xf72c57e1]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e11d)[0xf72c511d]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e673)[0xf72c5673]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x18e7e1)[0xf72c57e1]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_rc_reparse_all_for_settings+0xee)[0xf72c5d2e]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_settings_get_for_screen+0xe4)[0xf72e67b4]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_settings_get_default+0x24)[0xf72e6824]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x1c7f0a)[0xf72fef0a]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0x11b)[0xf6fc671b]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x12508)[0xf6fa9508]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x811)[0xf6fab231]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_new+0xa8)[0xf6fab7c8]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_style_new+0x24)[0xf72ff354]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_widget_get_default_style+0x25)[0xf73ab065]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x274118)[0xf73ab118]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0xce)[0xf6fc66ce]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x12508)[0xf6fa9508]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(+0x121cb6)[0xf7258cb6]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x811)[0xf6fab231]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_new+0xa8)[0xf6fab7c8]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_invisible_new+0x24)[0xf72591d4]
/home/subhi/ldoce5/components/libwidget_gtk2.so(+0x143e7)[0xf59243e7]
/home/subhi/ldoce5/components/libwidget_gtk2.so(+0x12b43)[0xf5922b43]
./libxpcom_core.so(+0x3f9c1)[0xf77039c1]
./libxpcom_core.so(+0x7afb5)[0xf773efb5]
./libxpcom_core.so(+0x7b301)[0xf773f301]
./libxpcom_core.so(_Z14CallGetServiceRK4nsIDS1_PPv+0x42)[0xf7701122]
./libxpcom_core.so(_ZNK17nsGetServiceByCIDclERK4nsIDPPv+0x2b)[0xf7701493]
./libxpcom_core.so(_ZN13nsCOMPtr_base18assign_from_gs_cidE17nsGetServiceByCIDRK4nsID+0x2b)[0xf7700f5d]
./ldoce5-bin[0x804c251]
./ldoce5-bin[0x804ce1f]
./ldoce5-bin[0x804db2b]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xf6ad44d3]
======= Memory map: ========
08048000-08073000 r-xp 00000000 08:06 799635                             /home/subhi/ldoce5/ldoce5-bin
08073000-08074000 rw-p 0002b000 08:06 799635                             /home/subhi/ldoce5/ldoce5-bin
0925f000-0938a000 rw-p 00000000 00:00 0                                  [heap]
f5289000-f5361000 r-xp 00000000 08:06 2228737                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f5361000-f5362000 ---p 000d8000 08:06 2228737                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f5362000-f5366000 r--p 000d8000 08:06 2228737                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f5366000-f5367000 rw-p 000dc000 08:06 2228737                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
f5367000-f536e000 rw-p 00000000 00:00 0 
f536e000-f54b2000 r-xp 00000000 08:06 2512340                            /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f54b2000-f54b3000 ---p 00144000 08:06 2512340                            /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f54b3000-f54b6000 r--p 00144000 08:06 2512340                            /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f54b6000-f54b8000 rw-p 00147000 08:06 2512340                            /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
f54b8000-f54c2000 r-xp 00000000 08:06 2228343                            /lib/i386-linux-gnu/libnss_nis-2.15.so
f54c2000-f54c3000 r--p 00009000 08:06 2228343                            /lib/i386-linux-gnu/libnss_nis-2.15.so
f54c3000-f54c4000 rw-p 0000a000 08:06 2228343                            /lib/i386-linux-gnu/libnss_nis-2.15.so
f54c4000-f54da000 r-xp 00000000 08:06 2228338                            /lib/i386-linux-gnu/libnsl-2.15.so
f54da000-f54db000 r--p 00015000 08:06 2228338                            /lib/i386-linux-gnu/libnsl-2.15.so
f54db000-f54dc000 rw-p 00016000 08:06 2228338                            /lib/i386-linux-gnu/libnsl-2.15.so
f54dc000-f54de000 rw-p 00000000 00:00 0 
f5506000-f554c000 r-xp 00000000 08:06 799473                             /home/subhi/ldoce5/components/libdocshell.so
f554c000-f554f000 rw-p 00046000 08:06 799473                             /home/subhi/ldoce5/components/libdocshell.so
f554f000-f559f000 r-xp 00000000 08:06 799433                             /home/subhi/ldoce5/components/libhtmlpars.so
f559f000-f55a6000 rw-p 00050000 08:06 799433                             /home/subhi/ldoce5/components/libhtmlpars.so
f55a6000-f565f000 r-xp 00000000 08:06 799398                             /home/subhi/ldoce5/components/libuconv.so
f565f000-f5665000 rw-p 000b9000 08:06 799398                             /home/subhi/ldoce5/components/libuconv.so
f5665000-f566f000 rw-p 00000000 00:00 0 
f566f000-f56b6000 r-xp 00000000 08:06 2228744                            /lib/i386-linux-gnu/libdbus-1.so.3.5.8
f56b6000-f56b7000 r--p 00046000 08:06 2228744                            /lib/i386-linux-gnu/libdbus-1.so.3.5.8
f56b7000-f56b8000 rw-p 00047000 08:06 2228744                            /lib/i386-linux-gnu/libdbus-1.so.3.5.8
f56b8000-f56dc000 r-xp 00000000 08:06 2251738                            /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
f56dc000-f56dd000 r--p 00023000 08:06 2251738                            /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
f56dd000-f56de000 rw-p 00024000 08:06 2251738                            /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2Aborted (core dumped)

```
However  it is work with ubuntu 12.04 
):P

---

### Post by Erik1984 on 2012-06-22
If it works on Ubuntu (Gnome) but not on KDE it usually has something to do with GTK+. Maybe you could try a different GTK+ theme (System Setting > Application Appearance > GTK+ Appearance) and check if the program starts then.

---

### Post by forsubhi on 2012-06-23
I changed widget  style from  oxygen-gtk to clearlooks so  the program work as a result , however the sound doesn't work in ubuntu and kubuntu 
```

subhi@subhi-pc:~/ldoce5$ ./ldoce5
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(ldoce5-bin:11401): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(ldoce5-bin:11401): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
```


I think that 
```
wrong ELF class
```

related to 32-64 bit problem , how can I solve sound problem now ?

---

