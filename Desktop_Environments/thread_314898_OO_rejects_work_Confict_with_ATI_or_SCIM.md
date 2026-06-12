---
title: "OO rejects work? Confict with ATI or SCIM?"
date: 2006-12-08
forum: Desktop Environments
---

### Post by ScowlKnight on 2006-12-08
the whole thing is that, after i have installed the offical driver(8.31.5) for my ATI card, my oo then rejected to work, after the splash, nothing displayed. i also tried using console to start

[email]song@syh-thinkpad:~/.AbiS[/email]uite/templates$ ooffice
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080c9b30 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6c808bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb6c80a44]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb729237d]
/usr/lib/openoffice/program/soffice.bin[0x808f17e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x808f1b6]
/usr/lib/libscim-1.0.so.8[0xadd816ac]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xadd828c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xadd7d0c5]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xade14346]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xade16960]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5e26c71]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa0b)[0xb5e0d31b]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5e0d73f]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5e0d8f0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xade083a7]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xade194ac]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb591c3e9]
/usr/lib/libgtk-x11-2.0.so.0[0xb591cf9b]
/usr/lib/libgtk-x11-2.0.so.0[0xb591d199]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb591a5ce]
/usr/lib/libgtk-x11-2.0.so.0[0xb58c4262]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5e14b29]
/usr/lib/libgobject-2.0.so.0[0xb5e05fb9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5e0779b]
/usr/lib/libgobject-2.0.so.0[0xb5e1802a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5e190b7]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5e19279]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb5a5748a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb5a57a6e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb58f16e3]
/usr/lib/libgtk-x11-2.0.so.0[0xb58f1728]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5e14039]
/usr/lib/libgobject-2.0.so.0[0xb5e05fb9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5e0779b]
/usr/lib/libgobject-2.0.so.0[0xb5e1802a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5e190b7]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5e19279]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb58a7fdc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5b77227]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5b7e1eb]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5b8266d]
/usr/lib/openoffice/program/libvcl680li.so[0xb7edbf25]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e6bb6b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7e6d437]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb797e7ce]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb795125a]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb794dfff]
/usr/lib/openoffice/program/libspl680li.so[0xadf1cc1a]
/usr/lib/openoffice/program/libspl680li.so[0xadf14054]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806cfe9]
/usr/lib/openoffice/program/libvcl680li.so[0xb7d03c2c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7d03d35]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x43)[0x805fdc3]
/usr/lib/openoffice/program/soffice.bin(main+0x36)[0x805fe46]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6c2f8cc]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x3d)[0x805fcf1]
======= Memory map: ========
08048000-0809a000 r-xp 00000000 08:03 1309229    /usr/lib/openoffice/program/soffice.bin
0809a000-0809b000 rw-p 00051000 08:03 1309229    /usr/lib/openoffice/program/soffice.bin
0809b000-0840d000 rw-p 0809b000 00:00 0          [heap]
adc00000-adc21000 rw-p adc00000 00:00 0 
adc21000-add00000 ---p adc21000 00:00 0 
add19000-addee000 r-xp 00000000 08:03 1211944    /usr/lib/libscim-1.0.so.8.1.0
addee000-addfc000 rw-p 000d5000 08:03 1211944    /usr/lib/libscim-1.0.so.8.1.0
addfc000-ade1f000 r-xp 00000000 08:03 1275822    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
ade1f000-ade20000 rw-p 00022000 08:03 1275822    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
ade20000-ade80000 rw-s 00000000 00:08 11075611   /SYSV00000000 (deleted)
ade80000-ade91000 r-xp 00000000 08:03 1309032    /usr/lib/openoffice/program/libfileacc.so
ade91000-ade92000 rw-p 00011000 08:03 1309032    /usr/lib/openoffice/program/libfileacc.so
ade92000-adeec000 r-xp 00000000 08:03 1309089    /usr/lib/openoffice/program/libpackage2.so
adeec000-adef0000 rw-p 00059000 08:03 1309089    /usr/lib/openoffice/program/libpackage2.so
adef0000-adf01000 r-xp 00000000 08:03 1275815    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
adf01000-adf02000 rw-p 00011000 08:03 1275815    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
adf02000-adf33000 r-xp 00000000 08:03 1309126    /usr/lib/openoffice/program/libspl680li.so
adf33000-adf35000 rw-p 00031000 08:03 1309126    /usr/lib/openoffice/program/libspl680li.so
adf35000-adf75000 rw-p adf35000 00:00 0 
adf75000-adf82000 r-xp 00000000 08:03 1309042    /usr/lib/openoffice/program/libgcc3_uno.so
adf82000-adf83000 rw-p 0000c000 08:03 1309042    /usr/lib/openoffice/program/libgcc3_uno.so
adf83000-ae245000 r-xp 00000000 08:03 1309039    /usr/lib/openoffice/program/libfwk680li.so
ae245000-ae253000 rw-p 002c2000 08:03 1309039    /usr/lib/openoffice/program/libfwk680li.so
ae253000-ae255000 rw-p ae253000 00:00 0 
ae255000-ae2ec000 r-xp 00000000 08:03 1309166    /usr/lib/openoffice/program/libxcr680li.so
ae2ec000-ae2f1000 rw-p 00096000 08:03 1309166    /usr/lib/openoffice/program/libxcr680li.so
ae2f1000-ae400000 r-xp 00000000 08:03 1309106    /usr/lib/openoffice/program/libsb680li.so
ae400000-ae40f000 rw-p 0010f000 08:03 1309106    /usr/lib/openoffice/program/libsb680li.so
ae40f000-ae4a0000 r-xp 00000000 08:03 1309037    /usr/lib/openoffice/program/libfwe680li.so
ae4a0000-ae4a4000 rw-p 00091000 08:03 1309037    /usr/lib/openoffice/program/libfwe680li.so
ae4a4000-ae863000 r-xp 00000000 08:03 1309119    /usr/lib/openoffice/program/libsfx680li.so
ae863000-ae87e000 rw-p 003be000 08:03 1309119    /usr/lib/openoffice/program/libsfx680li.so
ae87e000-ae8d5000 r-xp 00000000 08:03 1309148    /usr/lib/openoffice/program/libucpfile1.so
ae8d5000-ae8d7000 rw-p 00057000 08:03 1309148    /usr/lib/openoffice/program/libucpfile1.so
ae8d7000-ae8d8000 rw-p ae8d7000 00:00 0 
ae8d8000-ae90f000 r-xp 00000000 08:03 1309038    /usr/lib/openoffice/program/libfwi680li.so
ae90f000-ae911000 rw-p 00037000 08:03 1309038    /usr/lib/openoffice/program/libfwi680li.so
ae911000-ae933000 r-xp 00000000 08:03 1309040    /usr/lib/openoffice/program/libfwl680li.so
ae933000-ae934000 rw-p 00021000 08:03 1309040    /usr/lib/openoffice/program/libfwl680li.so
ae934000-ae966000 r-xp 00000000 08:03 1684371    /lib/libsepol.so.1
ae966000-ae967000 rw-p 00031000 08:03 1684371    /lib/libsepol.so.1
ae967000-ae971000 rw-p ae967000 00:00 0 
ae971000-ae974000 r-xp 00000000 08:03 1211657    /usr/lib/libgpg-error.so.0.2.0
ae974000-ae975000 rw-p 00002000 08:03 1211657    /usr/lib/libgpg-error.so.0.2.0
ae975000-ae9c1000 r-xp 00000000 08:03 1211539    /usr/lib/libgcrypt.so.11.2.1
ae9c1000-ae9c3000 rw-p 0004b000 08:03 1211539    /usr/lib/libgcrypt.so.11.2.1
ae9c3000-ae9d5000 r-xp 00000000 08:03 1211990    /usr/lib/libtasn1.so.3.0.5
ae9d5000-ae9d6000 rw-p 00011000 08:03 1211990    /usr/lib/libtasn1.so.3.0.5
ae9d6000-ae9d8000 r-xp 00000000 08:03 1717811    /lib/tls/i686/cmov/libutil-2.4.so
ae9d8000-ae9da000 rw-p 00001000 08:03 1717811    /lib/tls/i686/cmov/libutil-2.4.so
ae9da000-ae9ec000 r-xp 00000000 08:03 1684370    /lib/libselinux.so.1
ae9ec000-ae9ee000 rw-p 00011000 08:03 1684370    /lib/libselinux.so.1
ae9ee000-ae9fd000 r-xp 00000000 08:03 1717805    /lib/tls/i686/cmov/libresolv-2.4.so
ae9fd000-ae9ff000 rw-p 0000f000 08:03 1717805    /lib/tls/i686/cmov/libresolv-2.4.so
ae9ff000-aea01000 rw-p ae9ff000 00:00 0 
aea07000-aea09000 r-xp 00000000 08:03 1211948    /usr/lib/libscim-x11utils-1.0.so.8.1.0
aea09000-aea0a000 rw-p 00001000 08:03 1211948    /usr/lib/libscim-x11utils-1.0.so.8.1.0
aea0a000-aea10000 r-xp 00000000 08:03 1309065    /usr/lib/openoffice/program/libj680li_g.so
aea10000-aea11000 rw-p 00005000 08:03 1309065    /usr/lib/openoffice/program/libj680li_g.so
aea11000-aea1f000 r-xp 00000000 08:03 1210370    /usr/lib/libavahi-client.so.3.2.0
aea1f000-aea20000 rw-p 0000e000 08:03 1210370    /usr/lib/libavahi-client.so.3.2.0
aea20000-aea2a000 r-xp 00000000 08:03 1210610    /usr/lib/libavahi-common.so.3.4.2
aea2a000-aea2b000 rw-p 00009000 08:03 1210610    /usr/lib/libavahi-common.so.3.4.2
aea2b000-aea2d000 r-xp 00000000 08:03 1210646    /usr/lib/libavahi-glib.so.1.0.1
aea2d000-aea2e000 rw-p 00002000 08:03 1210646    /usr/lib/libavahi-glib.so.1.0.1
aea2e000-aea97000 r-xp 00000000 08:03 1211653    /usr/lib/libgnutls.so.13.0.5
aea97000-aea9d000 rw-p 00068000 08:03 1211653    /usr/lib/libgnutls.so.13.0.5
aea9d000-aeaf2000 r-xp 00000000 08:03 1211647    /usr/lib/libgnomevfs-2.so.0.1600.1
aeaf2000-aeaf5000 rw-p 00054000 08:03 1211647    /usr/lib/libgnomevfs-2.so.0.1600.1
aeaf5000-aeb18000 r-xp 00000000 08:03 1309245    /usr/lib/openoffice/program/ucpgvfs1.uno.so
aeb18000-aeb1a000 rw-p 00022000 08:03 1309245    /usr/lib/openoffice/program/ucpgvfs1.uno.so
aeb1a000-aeb58000 r-xp 00000000 08:03 1309144    /usr/lib/openoffice/program/libucb1.so
aeb58000-aeb5b000 rw-p 0003d000 08:03 1309144    /usr/lib/openoffice/program/libucb1.so
aeb5b000-aeb60000 r-xp 00000000 08:03 1309127    /usr/lib/openoffice/program/libspl_unx680li.so
aeb60000-aeb61000 rw-p 00004000 08:03 1309127    /usr/lib/openoffice/program/libspl_unx680li.so
aeb61000-aeb62000 ---p aeb61000 00:00 0 
aeb62000-aeb82000 rwxp aeb62000 00:00 0 
aeb82000-aeb94000 r-xp 00000000 08:03 1309253    /usr/lib/openoffice/program/uriproc.uno.so
aeb94000-aeb96000 rw-p 00011000 08:03 1309253    /usr/lib/openoffice/program/uriproc.uno.so
aeb96000-aeb97000 ---p aeb96000 00:00 0 
aeb97000-af397000 rwxp aeb97000 00:00 0 
af397000-af39f000 r-xp 00000000 08:03 1309178    /usr/lib/openoffice/program/localebe1.uno.so
af39f000-af3a0000 rw-p 00008000 08:03 1309178    /usr/lib/openoffice/program/localebe1.uno.so
af3a0000-af3bc000 r-xp 00000000 08:03 1309211    /usr/lib/openoffice/program/sax.uno.so
af3bc000-af3bd000 rw-p 0001c000 08:03 1309211    /usr/lib/openoffice/program/sax.uno.so
af3bd000-af3c6000 r-xp 00000000 08:03 1308941    /usr/lib/openoffice/program/behelper.uno.so
af3c6000-af3c7000 rw-p 00009000 08:03 1308941    /usr/lib/openoffice/program/behelper.uno.so
af3c7000-af40e000 r-xp 00000000 08:03 1211284    /usr/lib/libORBit-2.so.0.1.0
af40e000-af418000 rw-p 00046000 08:03 1211284    /usr/lib/libORBit-2.so.0.1.0
af418000-af446000 r-xp 00000000 08:03 1211537    /usr/lib/libgconf-2.so.4.1.0
af446000-af449000 rw-p 0002e000 08:03 1211537    /usr/lib/libgconf-2.so.4.1.0
af449000-af459000 r-xp 00000000 08:03 1308961    /usr/lib/openoffice/program/gconfbe1.uno.so
af459000-af45a000 rw-p 00010000 08:03 1308961    /usr/lib/openoffice/program/gconfbe1.uno.so
af45a000-af45e000 r-xp 00000000 08:03 1308955    /usr/lib/openoffice/program/desktopbe1.uno.so
af45e000-af45f000 rw-p 00003000 08:03 1308955    /usr/lib/openoffice/program/desktopbe1.uno.so
af45f000-af46b000 r-xp 00000000 08:03 1309237    /usr/lib/openoffice/program/sysmgr1.uno.so
af46b000-af46c000 rw-p 0000b000 08:03 1309237    /usr/lib/openoffice/program/sysmgr1.uno.so
af46c000-af475000 r-xp 00000000 08:03 1309241    /usr/lib/openoffice/program/typeconverter.uno.so
af475000-af476000 rw-p 00008000 08:03 1309241    /usr/lib/openoffice/program/typeconverter.uno.so
af476000-af69d000 r-xp 00000000 08:03 1308950    /usr/lib/openoffice/program/configmgr2.uno.so
af69d000-af6b0000 rw-p 00227000 08:03 1308950    /usr/lib/openoffice/program/configmgr2.uno.so
af6b0000-af6b1000 rw-p af6b0000 00:00 0 
af6b1000-af6e9000 r-xp 00000000 08:03 1309209    /usr/lib/openoffice/program/regtypeprov.uno.so
af6e9000-af6ed000 rw-p 00037000 08:03 1309209    /usr/lib/openoffice/program/regtypeprov.uno.so
af6ed000-afb45000 r--s 00000000 08:03 1309219    /usr/lib/openoffice/program/services.rdb
afb45000-b019d000 r--s 00000000 08:03 1309243    /usr/lib/openoffice/program/types.rdb
b019d000-b01b9000 r-xp 00000000 08:03 1309216    /usr/lib/openoffice/program/security.uno.so
b01b9000-b01bb000 rw-p 0001b000 08:03 1309216    /usr/lib/openoffice/program/security.uno.so
b01bb000-b01ce000 r-xp 00000000 08:03 1308969    /usr/lib/openoffice/program/implreg.uno.so
b01ce000-b01cf000 rw-p 00013000 08:03 1308969    /usr/lib/openoffice/program/implreg.uno.so
b01cf000-b01f7000 r-xp 00000000 08:03 1309242    /usr/lib/openoffice/program/typemgr.uno.so
b01f7000-b01f9000 rw-p 00027000 08:03 1309242    /usr/lib/openoffice/program/typemgr.uno.so
b01f9000-b0208000 r-xp 00000000 08:03 1309183    /usr/lib/openoffice/program/nestedreg.uno.so
b0208000-b0209000 rw-p 0000f000 08:03 1309183    /usr/lib/openoffice/program/nestedreg.uno.so
b0209000-b021a000 r-xp 00000000 08:03 1309224    /usr/lib/openoffice/program/simplereg.uno.so
b021a000-b021b000 rw-p 00010000 08:03 1309224    /usr/lib/openoffice/program/simplereg.uno.so
b021b000-b023a000 r-xp 00000000 08:03 1309218    /usr/lib/openoffice/program/servicemgr.uno.so
b023a000-b023c000 rw-p 0001e000 08:03 1309218    /usr/lib/openoffice/program/servicemgr.uno.so
b023c000-b0253000 r-xp 00000000 08:03 1309129    /usr/lib/openoffice/program/libstore.so.3
b0253000-b0254000 rw-p 00017000 08:03 1309129    /usr/lib/openoffice/program/libstore.so.3
b0254000-b0273000 r-xp 00000000 08:03 1309101    /usr/lib/openoffice/program/libreg.so.3
b0273000-b0274000 rw-p 0001f000 08:03 1309101    /usr/lib/openoffice/program/libreg.so.3
b0274000-b0285000 r-xp 00000000 08:03 1309029    /usr/lib/openoffice/program/libexlink680li.so
b0285000-b0286000 rw-p 00011000 08:03 1309029    /usr/lib/openoffice/program/libexlink680li.so
b0286000-b0386000 rw-s 00013000 00:0d 9869       /dev/dri/card0
b0386000-b09c6000 rw-s 00007000 00:0d 9869       /dev/dri/card0
b09c6000-b0ac6000 rw-s 00006000 00:0d 9869       /dev/dri/card0
b0ac6000-b0ad6000 rw-s 00004000 00:0d 9869       /dev/dri/card0
b0ad6000-b4ab6000 rw-s 00003000 00:0d 9869       /dev/dri/card0
b4ab6000-b4b66000 r-xp 00000000 08:03 1211983    /usr/lib/libstdc++.so.5.0.7
b4b66000-b4b6b000 rw-p 000af000 08:03 1211983    /usr/lib/libstdc++.so.5.0.7
b4b6b000-b4b70000 rw-p b4b6b000 00:00 0 
b4b70000-b5380000 r-xp 00000000 08:03 1291826    /usr/lib/dri/fglrx_dri.so
b5380000-b53c9000 rw-p 00810000 08:03 1291826    /usr/lib/dri/fglrx_dri.so
b53c9000-b5453000 rw-p b53c9000 00:00 0 
b5453000-b54eb000 r-xp 00000000 08:03 1220369    /usr/lib/libGL.so.1.2.backup
b54eb000-b54f0000 rw-p 00098000 08:03 1220369    /usr/lib/libGL.so.1.2.backup
b54f0000-b54f3000 rw-p b54f0000 00:00 0 
b54f3000-b54fc000 r-xp 00000000 08:03 1717794    /lib/tls/i686/cmov/libnss_files-2.4.so
b54fc000-b54fe000 rw-p 00008000 08:03 1717794    /lib/tls/i686/cmov/libnss_files-2.4.so
b54fe000-b5506000 r-xp 00000000 08:03 1717798    /lib/tls/i686/cmov/libnss_nis-2.4.so
b5506000-b5508000 rw-p 00007000 08:03 1717798    /lib/tls/i686/cmov/libnss_nis-2.4.so
b5508000-b550f000 r-xp 00000000 08:03 1717790    /lib/tls/i686/cmov/libnss_compat-2.4.so
b550f000-b5511000 rw-p 00006000 08:03 1717790    /lib/tls/i686/cmov/libnss_compat-2.4.so
b5512000-b5513000 rwxp b5512000 00:00 0 
b5513000-b5519000 r-xp 00000000 08:03 1309223    /usr/lib/openoffice/program/shlibloader.uno.so
b5519000-b551a000 rw-p 00005000 08:03 1309223    /usr/lib/openoffice/program/shlibloader.uno.so
b551a000-b5521000 rwxp b551a000 00:00 0 
b5521000-b55f8000 r--p 00000000 08:03 1277028    /usr/lib/locale/en_US.utf8/LC_COLLATE
b55f8000-b5642000 r-xp 00000000 08:03 1211341    /usr/lib/libXt.so.6.0.0
b5642000-b5646000 rw-p 00049000 08:03 1211341    /usr/lib/libXt.so.6.0.0
b5646000-b5685000 r-xp 00000000 08:03 1211261    /usr/lib/libFLAC.so.7.0.0
b5685000-b5686000 rw-p 0003f000 08:03 1211261    /usr/lib/libFLAC.so.7.0.0
b5686000-b568d000 r-xp 00000000 08:03 1211981    /usr/lib/libstartup-notification-1.so.0.0.0
b568d000-b568e000 rw-p 00006000 08:03 1211981    /usr/lib/libstartup-notification-1.so.0.0.0
b568e000-b56a3000 r-xp 00000000 08:03 1211378    /usr/lib/libaudio.so.2.4
b56a3000-b56a4000 rw-p 00014000 08:03 1211378    /usr/lib/libaudio.so.2.4
b56a4000-b56f8000 r-xp 00000000 08:03 1211965    /usr/lib/libsndfile.so.1.0.16
b56f8000-b56f9000 rw-p 00054000 08:03 1211965    /usr/lib/libsndfile.so.1.0.16
b56f9000-b56fe000 rw-p b56f9000 00:00 0 
b56fe000-b5710000 r-xp 00000000 08:03 1717788    /lib/tls/i686/cmov/libnsl-2.4.so
b5710000-b5712000 rw-p 00011000 08:03 1717788    /lib/tls/i686/cmov/libnsl-2.4.so
b5712000-b5716000 rw-p b5712000 00:00 0 
b5716000-b5717000 rw-s 00005000 00:0d 9869       /dev/dri/card0
b5717000-b5719000 rw-s 00002000 00:0d 9869       /dev/dri/card0
b5719000-b571a000 r-xp 00000000 08:03 1243444    /usr/lib/gconv/ISO8859-1.so
b571a000-b571c000 rw-p 00001000 08:03 1243444    /usr/lib/gconv/ISO8859-1.so
b571c000-b571d000 r-xp 00000000 08:03 1259246    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b571d000-b571e000 rw-p 00000000 08:03 1259246    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b571e000-b571f000 r--p 00000000 08:03 1277034    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b571f000-b5720000 r--p 00000000 08:03 1277037    /usr/lib/locale/en_US.utf8/LC_TIME
b5720000-b5721000 r--p 00000000 08:03 1277032    /usr/lib/locale/en_US.utf8/LC_MONETARY
b5721000-b5722000 r--p 00000000 08:03 1308172    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b5722000-b5723000 r--p 00000000 08:03 1277035    /usr/lib/locale/en_US.utf8/LC_PAPER
b5723000-b5724000 r--p 00000000 08:03 1277033    /usr/lib/locale/en_US.utf8/LC_NAME
b5724000-b5792000 r-xp 00000000 08:03 1309162    /usr/lib/openoffice/program/libvclplug_gen680li.so
b5792000-b579a000 rw-p 0006e000 08:03 1309162    /usr/lib/openoffice/program/libvclplug_gen680li.so
b579a000-b579b000 rw-p b579a000 00:00 0 
b579b000-b57ca000 r-xp 00000000 08:03 1211436    /usr/lib/libdbus-1.so.3.0.0
b57ca000-b57cb000 rw-p 0002f000 08:03 1211436    /usr/lib/libdbus-1.so.3.0.0
b57cb000-b57e5000 r-xp 00000000 08:03 1211438    /usr/lib/libdbus-glib-1.so.2.0.0
b57e5000-b57e6000 rw-p 00019000 08:03 1211438    /usr/lib/libdbus-glib-1.so.2.0.0
b57e6000-b57fe000 r-xp 00000000 08:03 1211374    /usr/lib/libatk-1.0.so.0.1213.0
b57fe000-b5800000 rw-p 00017000 08:03 1211374    /usr/lib/libatk-1.0.so.0.1213.0
b5800000-b5b49000 r-xp 00000000 08:03 1211710    /usr/lib/libgtk-x11-2.0.so.0.1000.6
b5b49000-b5b4f000 rw-p 00349000 08:03 1211710    /usr/lib/libgtk-x11-2.0.so.0.1000.6
b5b4f000-b5b50000 rw-p b5b4f000 00:00 0 
b5b50000-b5b94000 r-xp 00000000 08:03 1309163    /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5b94000-b5b9a000 rw-p 00044000 08:03 1309163    /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5b9a000-b5ba1000 r--s 00000000 08:03 1243496    /usr/lib/gconv/gconv-modules.cache
b5ba1000-b5bd4000 r--p 00000000 08:03 1277029    /usr/lib/locale/en_US.utf8/LC_CTYPE
b5bd4000-b5bd7000 rw-p b5bd4000 00:00 0 
b5bd7000-b5bde000 r-xp 00000000 08:03 1717807    /lib/tls/i686/cmov/librt-2.4.so
b5bde000-b5be0000 rw-p 00006000 08:03 1717807    /lib/tls/i686/cmov/librt-2.4.so
b5be0000-b5be1000 rw-p b5be0000 00:00 0 
b5be1000-b5c04000 r-xp 00000000 08:03 1211515    /usr/lib/libpng12.so.0.1.2.8
b5c04000-b5c05000 rw-p 00023000 08:03 1211515    /usr/lib/libpng12.so.0.1.2.8
b5c05000-b5c21000 r-xp 00000000 08:03 1211496    /usr/lib/libexpat.so.1.0.0
b5c21000-b5c23000 rw-p 0001c000 08:03 1211496    /usr/lib/libexpat.so.1.0.0
b5c23000-b5c4d000 r-xp 00000000 08:03 1211887    /usr/lib/libpangoft2-1.0.so.0.1400.5
b5c4d000-b5c4e000 rw-p 00029000 08:03 1211887    /usr/lib/libpangoft2-1.0.so.0.1400.5
b5c4e000-b5d61000 r-xp 00000000 08:03 1212030    /usr/lib/libxml2.so.2.6.26
b5d61000-b5d66000 rw-p 00113000 08:03 1212030    /usr/lib/libxml2.so.2.6.26
b5d66000-b5d68000 rw-p b5d66000 00:00 0 
b5d68000-b5df9000 r-xp 00000000 08:03 1211603    /usr/lib/libglib-2.0.so.0.1200.4
b5df9000-b5dfa000 rw-p 00091000 08:03 1211603    /usr/lib/libglib-2.0.so.0.1200.4
b5dfa000-b5dfd000 r-xp 00000000 08:03 1211615    /usr/lib/libgmodule-2.0.so.0.1200.4
b5dfd000-b5dfe000 rw-p 00002000 08:03 1211615    /usr/lib/libgmodule-2.0.so.0.1200.4
b5dfe000-b5e37000 r-xp 00000000 08:03 1211655    /usr/lib/libgobject-2.0.so.0.1200.4
b5e37000-b5e38000 rw-p 00038000 08:03 1211655    /usr/lib/libgobject-2.0.so.0.1200.4
b5e38000-b5e98000 r-xp 00000000 08:03 1211407    /usr/lib/libcairo.so.2.9.2
b5e98000-b5e9a000 rw-p 0005f000 08:03 1211407    /usr/lib/libcairo.so.2.9.2
b5e9a000-b5ed2000 r-xp 00000000 08:03 1211883    /usr/lib/libpango-1.0.so.0.1400.5
b5ed2000-b5ed4000 rw-p 00037000 08:03 1211883    /usr/lib/libpango-1.0.so.0.1400.5
b5ed4000-b5ed5000 rw-p b5ed4000 00:00 0 
b5ed5000-b5ed9000 r-xp 00000000 08:03 1211317    /usr/lib/libXfixes.so.3.1.0
b5ed9000-b5eda000 rw-p 00003000 08:03 1211317    /usr/lib/libXfixes.so.3.1.0
b5eda000-b5ee2000 r-xp 00000000 08:03 1211307    /usr/lib/libXcursor.so.1.0.2
b5ee2000-b5ee3000 rw-p 00007000 08:03 1211307    /usr/lib/libXcursor.so.1.0.2
b5ee3000-b5ee5000 r-xp 00000000 08:03 1211335    /usr/lib/libXrandr.so.2.0.0
b5ee5000-b5ee6000 rw-p 00002000 08:03 1211335    /usr/lib/libXrandr.so.2.0.0
b5ee6000-b5eed000 r-xp 00000000 08:03 1211323    /usr/lib/libXi.so.6.0.0
b5eed000-b5eee000 rw-p 00006000 08:03 1211323    /usr/lib/libXi.so.6.0.0
b5eee000-b5ef0000 r-xp 00000000 08:03 1211325    /usr/lib/libXinerama.so.1.0.0
b5ef0000-b5ef1000 rw-p 00001000 08:03 1211325    /usr/lib/libXinerama.so.1.0.0
b5ef1000-b5ef8000 r-xp 00000000 08:03 1211337    /usr/lib/libXrender.so.1.3.0
b5ef8000-b5ef9000 rw-p 00006000 08:03 1211337    /usr/lib/libXrender.so.1.3.0
b5ef9000-b5efa000 rw-p b5ef9000 00:00 0 
b5efa000-b5f23000 r-xp 00000000 08:03 1211502    /usr/lib/libfontconfig.so.1.0.4
b5f23000-b5f28000 rw-p 00028000 08:03 1211502    /usr/lib/libfontconfig.so.1.0.4
b5f28000-b5f29000 rw-p b5f28000 00:00 0 
b5f29000-b5f30000 r-xp 00000000 08:03 1211885    /usr/lib/libpangocairo-1.0.so.0.1400.5
b5f30000-b5f31000 rw-p 00006000 08:03 1211885    /usr/lib/libpangocairo-1.0.so.0.1400.5
b5f31000-b5f46000 r-xp 00000000 08:03 1211556    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b5f46000-b5f47000 rw-p 00015000 08:03 1211556    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b5f47000-b5fc8000 r-xp 00000000 08:03 1211554    /usr/lib/libgdk-x11-2.0.so.0.1000.6
b5fc8000-b5fcb000 rw-p 00081000 08:03 1211554    /usr/lib/libgdk-x11-2.0.so.0.1000.6
b5fcb000-b683f000 r--p 00000000 08:03 1211749    /usr/lib/libicudata.so.34.1
b683f000-b6840000 rw-p 00873000 08:03 1211749    /usr/lib/libicudata.so.34.1
b6840000-b6841000 rw-p b6840000 00:00 0 
b6841000-b6845000 r-xp 00000000 08:03 1211311    /usr/lib/libXdmcp.so.6.0.0
b6845000-b6846000 rw-p 00003000 08:03 1211311    /usr/lib/libXdmcp.so.6.0.0
b6846000-b6848000 r-xp 00000000 08:03 1211302    /usr/lib/libXau.so.6.0.0
b6848000-b6849000 rw-p 00001000 08:03 1211302    /usr/lib/libXau.so.6.0.0
b6849000-b684e000 r-xp 00000000 08:03 1717781    /lib/tls/i686/cmov/libcrypt-2.4.so
b684e000-b6850000 rw-p 00004000 08:03 1717781    /lib/tls/i686/cmov/libcrypt-2.4.so
b6850000-b6877000 rw-p b6850000 00:00 0 
b6877000-b687e000 r-xp 00000000 08:03 1684351    /lib/libpam.so.0.79
b687e000-b687f000 rw-p 00006000 08:03 1684351    /lib/libpam.so.0.79
b687f000-b6880000 rw-p b687f000 00:00 0 
b6880000-b6883000 r-xp 00000000 08:03 1309155    /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b6883000-b6884000 rw-p 00003000 08:03 1309155    /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b6884000-b689b000 r-xp 00000000 08:03 1309073    /usr/lib/openoffice/program/libjvmfwk.so.3
b689b000-b689c000 rw-p 00017000 08:03 1309073    /usr/lib/openoffice/program/libjvmfwk.so.3
b689c000-b68ba000 r-xp 00000000 08:03 1211778    /usr/lib/libjpeg.so.62.0.0
b68ba000-b68bb000 rw-p 0001d000 08:03 1211778    /usr/lib/libjpeg.so.62.0.0
b68bb000-b694c000 r-xp 00000000 08:03 1309097    /usr/lib/openoffice/program/libpsp680li.so
b694c000-b6995000 rw-p 00090000 08:03 1309097    /usr/lib/openoffice/program/libpsp680li.so
b6995000-b6997000 rw-p b6995000 00:00 0 
b6997000-b69aa000 r-xp 00000000 08:03 1212042    /usr/lib/libz.so.1.2.3
b69aa000-b69ab000 rw-p 00012000 08:03 1212042    /usr/lib/libz.so.1.2.3
b69ab000-b69ac000 rw-p b69ab000 00:00 0 
b69ac000-b6a13000 r-xp 00000000 08:03 1211512    /usr/lib/libfreetype.so.6.3.10
b6a13000-b6a16000 rw-p 00067000 08:03 1211512    /usr/lib/libfreetype.so.6.3.10
b6a16000-b6a1a000 r-xp 00000000 08:03 1309072    /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b6a1a000-b6a1b000 rw-p 00003000 08:03 1309072    /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b6a1b000-b6a53000 r-xp 00000000 08:03 1211755    /usr/lib/libicule.so.34.1
b6a53000-b6a55000 rw-p 00037000 08:03 1211755    /usr/lib/libicule.so.34.1
b6a55000-b6b4f000 r-xp 00000000 08:03 1211761    /usr/lib/libicuuc.so.34.1
b6b4f000-b6b56000 rw-p 000f9000 08:03 1211761    /usr/lib/libicuuc.so.34.1
b6b56000-b6b57000 rw-p b6b56000 00:00 0 
b6b57000-b6bbe000 r-xp 00000000 08:03 1308989    /usr/lib/openoffice/program/libbasegfx680li.so
b6bbe000-b6bbf000 rw-p 00066000 08:03 1308989    /usr/lib/openoffice/program/libbasegfx680li.so
b6bbf000-b6c16000 r-xp 00000000 08:03 1309123    /usr/lib/openoffice/program/libsot680li.so
b6c16000-b6c19000 rw-p 00057000 08:03 1309123    /usr/lib/openoffice/program/libsot680li.so
b6c19000-b6c1a000 rw-p b6c19000 00:00 0 
b6c1a000-b6d47000 r-xp 00000000 08:03 1717777    /lib/tls/i686/cmov/libc-2.4.so
b6d47000-b6d49000 r--p 0012c000 08:03 1717777    /lib/tls/i686/cmov/libc-2.4.so
b6d49000-b6d4b000 rw-p 0012e000 08:03 1717777    /lib/tls/i686/cmov/libc-2.4.so
b6d4b000-b6d4e000 rw-p b6d4b000 00:00 0 
b6d4e000-b6d58000 r-xp 00000000 08:03 1684323    /lib/libgcc_s.so.1
b6d58000-b6d59000 rw-p 00009000 08:03 1684323    /lib/libgcc_s.so.1
b6d59000-b6d7d000 r-xp 00000000 08:03 1717785    /lib/tls/i686/cmov/libm-2.4.so
b6d7d000-b6d7f000 rw-p 00023000 08:03 1717785    /lib/tls/i686/cmov/libm-2.4.so
b6d7f000-b6e53000 r-xp 00000000 08:03 1211985    /usr/lib/libstdc++.so.6.0.8
b6e53000-b6e56000 r--p 000d4000 08:03 1211985    /usr/lib/libstdc++.so.6.0.8
b6e56000-b6e58000 rw-p 000d7000 08:03 1211985    /usr/lib/libstdc++.so.6.0.8
b6e58000-b6e5e000 rw-p b6e58000 00:00 0 
b6e5e000-b6f19000 r-xp 00000000 08:03 1211986    /usr/lib/libstlport_gcc.so.4.6
b6f19000-b6f1d000 rw-p 000bb000 08:03 1211986    /usr/lib/libstlport_gcc.so.4.6
b6f1d000-b6f1e000 rw-p b6f1d000 00:00 0 
b6f1e000-b6f2d000 r-xp 00000000 08:03 1717803    /lib/tls/i686/cmov/libpthread-2.4.so
b6f2d000-b6f2f000 rw-p 0000f000 08:03 1717803    /lib/tls/i686/cmov/libpthread-2.4.so
b6f2f000-b6f32000 rw-p b6f2f000 00:00 0 
b6f32000-b6f34000 r-xp 00000000 08:03 1717783    /lib/tls/i686/cmov/libdl-2.4.so
b6f34000-b6f36000 rw-p 00001000 08:03 1717783    /lib/tls/i686/cmov/libdl-2.4.so
b6f36000-b6f37000 r--p 00000000 08:03 1277027    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b6f37000-b6f38000 r--p 00000000 08:03 1277036    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b6f38000-b6f39000 r--p 00000000 08:03 1277031    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b6f39000-b6f3a000 r--p 00000000 08:03 1277030    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b6f3a000-b6f40000 r-xp 00000000 08:03 1211914    /usr/lib/libportaudio.so.0.0.18
b6f40000-b6f41000 rw-p 00005000 08:03 1211914    /usr/lib/libportaudio.so.0.0.18
b6f41000-b6f45000 r-xp 00000000 08:03 1211707    /usr/lib/libgthread-2.0.so.0.1200.4
b6f45000-b6f46000 rw-p 00003000 08:03 1211707    /usr/lib/libgthread-2.0.so.0.1200.4
b6f46000-b700c000 r-xp 00000000 08:03 1211296    /usr/lib/libX11.so.6.2.0
b700c000-b700f000 rw-p 000c5000 08:03 1211296    /usr/lib/libX11.so.6.2.0
b700f000-b7024000 r-xp 00000000 08:03 1211274    /usr/lib/libICE.so.6.3.0
b7024000-b7025000 rw-p 00014000 08:03 1211274    /usr/lib/libICE.so.6.3.0
b7025000-b7027000 rw-p b7025000 00:00 0 
b7027000-b702f000 r-xp 00000000 08:03 1211292    /usr/lib/libSM.so.6.0.0
b702f000-b7030000 rw-p 00007000 08:03 1211292    /usr/lib/libSM.so.6.0.0
b7030000-b703c000 r-xp 00000000 08:03 1211315    /usr/lib/libXext.so.6.4.0
b703c000-b703d000 rw-p 0000c000 08:03 1211315    /usr/lib/libXext.so.6.4.0
b703d000-b7245000 r-xp 00000000 08:03 1309141    /usr/lib/openoffice/program/libtk680li.so
b7245000-b7269000 rw-p 00208000 08:03 1309141    /usr/lib/openoffice/program/libtk680li.so
b7269000-b726c000 rw-p b7269000 00:00 0 
b726c000-b7418000 r-xp 00000000 08:03 1309154    /usr/lib/openoffice/program/libuno_sal.so.3
b7418000-b742b000 rw-p 001ac000 08:03 1309154    /usr/lib/openoffice/program/libuno_sal.so.3
b742b000-b742d000 rw-p b742b000 00:00 0 
b742d000-b7458000 r-xp 00000000 08:03 1309152    /usr/lib/openoffice/program/libuno_cppu.so.3
b7458000-b7459000 rw-p 0002a000 08:03 1309152    /usr/lib/openoffice/program/libuno_cppu.so.3
b7459000-b74c4000 r-xp 00000000 08:03 1309153    /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b74c4000-b74c7000 rw-p 0006a000 08:03 1309153    /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b74c7000-b74e8000 r-xp 00000000 08:03 1309164    /usr/lib/openoffice/program/libvos3gcc3.so
b74e8000-b74ea000 rw-p 00020000 08:03 1309164    /usr/lib/openoffice/program/libvos3gcc3.so
b74ea000-b7562000 r-xp 00000000 08:03 1309145    /usr/lib/openoffice/program/libucbhelper3gcc3.so
b7562000-b7566000 rw-p 00077000 08:03 1309145    /usr/lib/openoffice/program/libucbhelper3gcc3.so
b7566000-b7567000 rw-p b7566000 00:00 0 
b7567000-b764b000 r-xp 00000000 08:03 1308995    /usr/lib/openoffice/program/libcomphelp4gcc3.so
b764b000-b7653000 rw-p 000e3000 08:03 1308995    /usr/lib/openoffice/program/libcomphelp4gcc3.so
b7653000-b7654000 rw-p b7653000 00:00 0 
b7654000-b7658000 r-xp 00000000 08:03 1309049    /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b7658000-b7659000 rw-p 00004000 08:03 1309049    /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b7659000-b76f4000 r-xp 00000000 08:03 1309142    /usr/lib/openoffice/program/libtl680li.so
b76f4000-b76f7000 rw-p 0009a000 08:03 1309142    /usr/lib/openoffice/program/libtl680li.so
b76f7000-b7780000 r-xp 00000000 08:03 1309159    /usr/lib/openoffice/program/libutl680li.so
b7780000-b7785000 rw-p 00088000 08:03 1309159    /usr/lib/openoffice/program/libutl680li.so
b7785000-b7b43000 r-xp 00000000 08:03 1309133    /usr/lib/openoffice/program/libsvt680li.so
b7b43000-b7b67000 rw-p 003bd000 08:03 1309133    /usr/lib/openoffice/program/libsvt680li.so
b7b67000-b7b68000 rw-p b7b67000 00:00 0 
b7b68000-b7c6d000 r-xp 00000000 08:03 1309132    /usr/lib/openoffice/program/libsvl680li.so
b7c6d000-b7c72000 rw-p 00105000 08:03 1309132    /usr/lib/openoffice/program/libsvl680li.so
b7c72000-b7c74000 rw-p b7c72000 00:00 0 
b7c74000-b7fb0000 r-xp 00000000 08:03 1309161    /usr/lib/openoffice/program/libvcl680li.so
b7fb0000-b7fc4000 rw-p 0033b000 08:03 1309161    /usr/lib/openoffice/program/libvcl680li.so
b7fc4000-b7fc7000 rw-p b7fc4000 00:00 0 
b7fc7000-b7fe0000 r-xp 00000000 08:03 1684278    /lib/ld-2.4.so
b7fe0000-b7fe2000 rw-p 00018000 08:03 1684278    /lib/ld-2.4.so
bfc6c000-bfcb0000 rwxp bfc6c000 00:00 0          [stack]
bfcb0000-bfcb1000 rw-p bfcb0000 00:00 0 
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

** (process:10124): WARNING **: Unknown error forking main binary / abnormal early exit ...

can anyone show me a hand? many thanks:)
another, my environment is : edgy, gnome, ati x300, using en local and scim  typing method fully because i come from China:)

---

### Post by ScowlKnight on 2006-12-08
i'd rather need your help, please

---

