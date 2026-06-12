---
title: "OpenOffice.org Invalid Pointer Error"
date: 2007-04-29
forum: Desktop Environments
---

### Post by Kenji Miyamoto on 2007-04-29
I'm having a bit of a problem with the OpenOffice.org Writer released with 7.04. It happens at startup regardless of the situation, while the splash screen is still present.  Is this an error that can be fixed without having to edit and compile the source instead of using the package?```
 *** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d0540 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6ce67cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6ce9e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb733c0bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xad7c9156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xad7c9f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xad7c4f05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xad868f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5cefb41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5cd61cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5cd65ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5cd67a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xad85db57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xad86d27c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb57ced29]
/usr/lib/libgtk-x11-2.0.so.0[0xb57cf93b]
/usr/lib/libgtk-x11-2.0.so.0[0xb57cfb39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb57ccf0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb577671f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5cdd9d9]
/usr/lib/libgobject-2.0.so.0[0xb5ccee49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5cd062b]
/usr/lib/libgobject-2.0.so.0[0xb5ce159a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5ce2627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5ce27e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb590abea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb590b1ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb57a3ec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb57a3f08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5cdcee9]
/usr/lib/libgobject-2.0.so.0[0xb5ccee49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5cd062b]
/usr/lib/libgobject-2.0.so.0[0xb5ce159a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5ce2627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5ce27e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb575a1bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a3b2bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a3d043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a47abd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e97ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e2509b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7e25ac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb78f299e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb78c41da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb78c155f]
/usr/lib/openoffice/program/libspl680li.so[0xad971926]
/usr/lib/openoffice/program/libspl680li.so[0xad968024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7ca5c3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7ca5d45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6c94ebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 03:03 12576      /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 03:03 12576      /usr/lib/openoffice/program/soffice.bin
0809e000-083a6000 rw-p 0809e000 00:00 0          [heap]
ad600000-ad621000 rw-p ad600000 00:00 0 
ad621000-ad700000 ---p ad621000 00:00 0 
ad761000-ad835000 r-xp 00000000 03:03 7879       /usr/lib/libscim-1.0.so.8.1.0
ad835000-ad843000 rw-p 000d4000 03:03 7879       /usr/lib/libscim-1.0.so.8.1.0
ad851000-ad872000 r-xp 00000000 03:03 9919       /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
ad872000-ad873000 rw-p 00021000 03:03 9919       /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
ad873000-ad8d3000 rw-s 00000000 00:08 1638418    /SYSV00000000 (deleted)
ad8d3000-ad8e3000 r-xp 00000000 03:03 12369      /usr/lib/openoffice/program/libfileacc.so
ad8e3000-ad8e4000 rw-p 00010000 03:03 12369      /usr/lib/openoffice/program/libfileacc.so
ad8e4000-ad941000 r-xp 00000000 03:03 12426      /usr/lib/openoffice/program/libpackage2.so
ad941000-ad944000 rw-p 0005d000 03:03 12426      /usr/lib/openoffice/program/libpackage2.so
ad944000-ad956000 r-xp 00000000 03:03 9912       /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
ad956000-ad957000 rw-p 00011000 03:03 9912       /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
ad957000-ad989000 r-xp 00000000 03:03 12464      /usr/lib/openoffice/program/libspl680li.so
ad989000-ad98b000 rw-p 00032000 03:03 12464      /usr/lib/openoffice/program/libspl680li.so
ad98b000-ad9cb000 rw-p ad98b000 00:00 0 
ad9cb000-ad9d9000 r-xp 00000000 03:03 12379      /usr/lib/openoffice/program/libgcc3_uno.so
ad9d9000-ad9da000 rw-p 0000e000 03:03 12379      /usr/lib/openoffice/program/libgcc3_uno.so
ad9da000-adcbe000 r-xp 00000000 03:03 12376      /usr/lib/openoffice/program/libfwk680li.so
adcbe000-adcce000 rw-p 002e3000 03:03 12376      /usr/lib/openoffice/program/libfwk680li.so
adcce000-adccf000 rw-p adcce000 00:00 0 
adccf000-add6a000 r-xp 00000000 03:03 12505      /usr/lib/openoffice/program/libxcr680li.so
add6a000-add6f000 rw-p 0009a000 03:03 12505      /usr/lib/openoffice/program/libxcr680li.so
add6f000-aded2000 r-xp 00000000 03:03 12444      /usr/lib/openoffice/program/libsb680li.so
aded2000-adee3000 rw-p 00163000 03:03 12444      /usr/lib/openoffice/program/libsb680li.so
adee3000-adee4000 rw-p adee3000 00:00 0 
adee4000-adf7e000 r-xp 00000000 03:03 12374      /usr/lib/openoffice/program/libfwe680li.so
adf7e000-adf82000 rw-p 0009a000 03:03 12374      /usr/lib/openoffice/program/libfwe680li.so
adf82000-ae32c000 r-xp 00000000 03:03 12457      /usr/lib/openoffice/program/libsfx680li.so
ae32c000-ae345000 rw-p 003a9000 03:03 12457      /usr/lib/openoffice/program/libsfx680li.so
ae345000-ae346000 rw-p ae345000 00:00 0 
ae346000-ae34a000 r-xp 00000000 03:03 5476       /lib/tls/i686/cmov/libnss_dns-2.5.so
ae34a000-ae34c000 rw-p 00003000 03:03 5476       /lib/tls/i686/cmov/libnss_dns-2.5.so
ae34c000-ae34e000 r-xp 00000000 03:03 2250       /lib/libnss_mdns4_minimal.so.2
ae34e000-ae34f000 rw-p 00001000 03:03 2250       /lib/libnss_mdns4_minimal.so.2
ae34f000-ae3aa000 r-xp 00000000 03:03 12486      /usr/lib/openoffice/program/libucpfile1.so
ae3aa000-ae3ad000 rw-p 0005a000 03:03 12486      /usr/lib/openoffice/program/libucpfile1.so
ae3ad000-ae3e7000 r-xp 00000000 03:03 12375      /usr/lib/openoffice/program/libfwi680li.so
ae3e7000-ae3e9000 rw-p 0003a000 03:03 12375      /usr/lib/openoffice/program/libfwi680li.so
ae3e9000-ae40c000 r-xp 00000000 03:03 12377      /usr/lib/openoffice/program/libfwl680li.so
ae40c000-ae40d000 rw-p 00023000 03:03 12377      /usr/lib/openoffice/program/libfwl680li.so
ae40d000-ae443000 r-xp 00000000 03:03 2279       /lib/libsepol.so.1
ae443000-ae444000 rw-p 00035000 03:03 2279       /lib/libsepol.so.1
ae444000-ae44e000 rw-p ae444000 00:00 0 
ae44e000-ae451000 r-xp 00000000 03:03 7584       /usr/lib/libgpg-error.so.0.3.0
ae451000-ae452000 rw-p 00002000 03:03 7584       /usr/lib/libgpg-error.so.0.3.0
ae452000-ae4a1000 r-xp 00000000 03:03 7472       /usr/lib/libgcrypt.so.11.2.2
ae4a1000-ae4a3000 rw-p 0004e000 03:03 7472       /usr/lib/libgcrypt.so.11.2.2
ae4a3000-ae4b7000 r-xp 00000000 03:03 7928       /usr/lib/libtasn1.so.3.0.6
ae4b7000-ae4b8000 rw-p 00013000 03:03 7928       /usr/lib/libtasn1.so.3.0.6
ae4b8000-ae4ba000 r-xp 00000000 03:03 5495       /lib/tls/i686/cmov/libutil-2.5.so
ae4ba000-ae4bc000 rw-p 00001000 03:03 5495       /lib/tls/i686/cmov/libutil-2.5.so
ae4bc000-ae4d0000 r-xp 00000000 03:03 2278       /lib/libselinux.so.1
ae4d0000-ae4d2000 rw-p 00013000 03:03 2278       /lib/libselinux.so.1
ae4d2000-ae4e1000 r-xp 00000000 03:03 5489       /lib/tls/i686/cmov/libresolv-2.5.so
ae4e1000-ae4e3000 rw-p 0000f000 03:03 5489       /lib/tls/i686/cmov/libresolv-2.5.so
ae4e3000-ae4e5000 rw-p ae4e3000 00:00 0 
ae4e5000-ae4f3000 r-xp 00000000 03:03 7310       /usr/lib/libavahi-client.so.3.2.2
ae4f3000-ae4f4000 rw-p 0000e000 03:03 7310       /usr/lib/libavahi-client.so.3.2.2
ae4f4000-ae4fe000 r-xp 00000000 03:03 7312       /usr/lib/libavahi-common.so.3.4.3
ae4fe000-ae4ff000 rw-p 00009000 03:03 7312       /usr/lib/libavahi-common.so.3.4.3
ae4ff000-ae501000 r-xp 00000000 03:03 7316       /usr/lib/libavahi-glib.so.1.0.1
ae501000-ae502000 rw-p 00001000 03:03 7316       /usr/lib/libavahi-glib.so.1.0.1
ae502000-ae56c000 r-xp 00000000 03:03 7580       /usr/lib/libgnutls.so.13.0.9
ae56c000-ae572000 rw-p 0006a000 03:03 7580       /usr/lib/libgnutls.so.13.0.9
ae572000-ae5c8000 r-xp 00000000 03:03 7572       /usr/lib/libgnomevfs-2.so.0.1800.1
ae5c8000-ae5cb000 rw-p 00055000 03:03 7572       /usr/lib/libgnomevfs-2.so.0.1800.1
ae5cf000-ae5d1000 r-xp 00000000 03:03 7883       /usr/lib/libscim-x11utils-1.0.so.8.1.0
ae5d1000-ae5d2000 rw-p 00001000 03:03 7883       /usr/lib/libscim-x11utils-1.0.so.8.1.0
ae5d2000-ae5d8000 r-xp 00000000 03:03 12401      /usr/lib/openoffice/program/libj680li_g.so
ae5d8000-ae5d9000 rw-p 00006000 03:03 12401      /usr/lib/openoffice/program/libj680li_g.so
ae5d9000-ae5fd000 r-xp 00000000 03:03 12593      /usr/lib/openoffice/program/ucpgvfs1.uno.so
ae5fd000-ae5ff000 rw-p 00023000 03:03 12593      /usr/lib/openoffice/program/ucpgvfs1.uno.so
ae5ff000-ae63e000 r-xp 00000000 03:03 12482      /usr/lib/openoffice/program/libucb1.so
ae63e000-ae641000 rw-p 0003e000 03:03 12482      /usr/lib/openoffice/program/libucb1.so
ae641000-ae646000 r-xp 00000000 03:03 12465      /usr/lib/openoffice/program/libspl_unx680li.so
ae646000-ae647000 rw-p 00004000 03:03 12465      /usr/lib/openoffice/program/libspl_unx680li.so
ae647000-ae648000 ---p ae647000 00:00 0 
ae648000-aee48000 rwxp ae648000 00:00 0 
aee48000-aee5a000 r-xp 00000000 03:03 12602      /usr/lib/openoffice/program/uriproc.uno.so
aee5a000-aee5c000 rw-p 00011000 03:03 12602      /usr/lib/openoffice/program/uriproc.uno.so
aee5c000-aee5d000 ---p aee5c000 00:00 0 
aee5d000-af65d000 rwxp aee5d000 00:00 0 
af65d000-af665000 r-xp 00000000 03:03 12521      /usr/lib/openoffice/program/localebe1.uno.so
af665000-af666000 rw-p 00008000 03:03 12521      /usr/lib/openoffice/program/localebe1.uno.so
af666000-af68f000 r-xp 00000000 03:03 12580      /usr/lib/openoffice/program/streams.uno.so
af68f000-af692000 rw-p 00028000 03:03 12580      /usr/lib/openoffice/program/streams.uno.so
af692000-af6ae000 r-xp 00000000 03:03 12558      /usr/lib/openoffice/program/sax.uno.so
af6ae000-af6af000 rw-p 0001c000 03:03 12558      /usr/lib/openoffice/program/sax.uno.so
af6af000-af6f8000 r-xp 00000000 03:03 7213       /usr/lib/libORBit-2.so.0.1.0
af6f8000-af702000 rw-p 00048000 03:03 7213       /usr/lib/libORBit-2.so.0.1.0
af702000-af731000 r-xp 00000000 03:03 7470       /usr/lib/libgconf-2.so.4.1.2
af731000-af734000 rw-p 0002e000 03:03 7470       /usr/lib/libgconf-2.so.4.1.2
af735000-af736000 rwxp af735000 00:00 0 
af736000-af737000 rw-p af736000 00:00 0 
af737000-af741000 r-xp 00000000 03:03 12278      /usr/lib/openoffice/program/behelper.uno.so
af741000-af742000 rw-p 00009000 03:03 12278      /usr/lib/openoffice/program/behelper.uno.so
af742000-af751000 r-xp 00000000 03:03 12298      /usr/lib/openoffice/program/gconfbe1.uno.so
af751000-af752000 rw-p 0000f000 03:03 12298      /usr/lib/openoffice/program/gconfbe1.uno.so
af752000-af756000 r-xp 00000000 03:03 12292      /usr/lib/openoffice/program/desktopbe1.uno.so
af756000-af757000 rw-p 00003000 03:03 12292      /usr/lib/openoffice/program/desktopbe1.uno.so
af757000-af763000 r-xp 00000000 03:03 12585      /usr/lib/openoffice/program/sysmgr1.uno.so
af763000-af764000 rw-p 0000c000 03:03 12585      /usr/lib/openoffice/program/sysmgr1.uno.so
af764000-af76c000 r-xp 00000000 03:03 12589      /usr/lib/openoffice/program/typeconverter.uno.so
af76c000-af76d000 rw-p 00008000 03:03 12589      /usr/lib/openoffice/program/typeconverter.uno.so
af76d000-af981000 r-xp 00000000 03:03 12287      /usr/lib/openoffice/program/configmgr2.uno.so
af981000-af995000 rw-p 00213000 03:03 12287      /usr/lib/openoffice/program/configmgr2.uno.so
af995000-af9ce000 r-xp 00000000 03:03 12553      /usr/lib/openoffice/program/regtypeprov.uno.so
af9ce000-af9d2000 rw-p 00038000 03:03 12553      /usr/lib/openoffice/program/regtypeprov.uno.so
af9d2000-afbda000 r--s 00000000 03:03 12566      /usr/lib/openoffice/program/services.rdb
afbda000-aff32000 r--s 00000000 03:03 12591      /usr/lib/openoffice/program/types.rdb
aff32000-aff72000 r--s 00000000 03:03 12530      /usr/lib/openoffice/program/oovbaapi.rdb
aff72000-aff8f000 r-xp 00000000 03:03 12563      /usr/lib/openoffice/program/security.uno.so
aff8f000-aff91000 rw-p 0001c000 03:03 12563      /usr/lib/openoffice/program/security.uno.so
aff91000-affa5000 r-xp 00000000 03:03 12306      /usr/lib/openoffice/program/implreg.uno.so
affa5000-affa6000 rw-p 00013000 03:03 12306      /usr/lib/openoffice/program/implreg.uno.so
affa6000-affce000 r-xp 00000000 03:03 12590      /usr/lib/openoffice/program/typemgr.uno.so
affce000-affd0000 rw-p 00028000 03:03 12590      /usr/lib/openoffice/program/typemgr.uno.so
affd0000-affdf000 r-xp 00000000 03:03 12526      /usr/lib/openoffice/program/nestedreg.uno.so
affdf000-affe0000 rw-p 0000f000 03:03 12526      /usr/lib/openoffice/program/nestedreg.uno.so
affe0000-afff1000 r-xp 00000000 03:03 12571      /usr/lib/openoffice/program/simplereg.uno.so
afff1000-afff2000 rw-p 00010000 03:03 12571      /usr/lib/openoffice/program/simplereg.uno.so
afff2000-b0012000 r-xp 00000000 03:03 12565      /usr/lib/openoffice/program/servicemgr.uno.so
b0012000-b0014000 rw-p 0001f000 03:03 12565      /usr/lib/openoffice/program/servicemgr.uno.so
b0014000-b0030000 r-xp 00000000 03:03 12467      /usr/lib/openoffice/program/libstore.so.3
b0030000-b0031000 rw-p 0001b000 03:03 12467      /usr/lib/openoffice/program/libstore.so.3
b0031000-b0053000 r-xp 00000000 03:03 12438      /usr/lib/openoffice/program/libreg.so.3
b0053000-b0054000 rw-p 00021000 03:03 12438      /usr/lib/openoffice/program/libreg.so.3
b0054000-b0065000 r-xp 00000000 03:03 12366      /usr/lib/openoffice/program/libexlink680li.so
b0065000-b0066000 rw-p 00011000 03:03 12366      /usr/lib/openoffice/program/libexlink680li.so
b0066000-b01a6000 rw-s 00010000 00:0d 15966      /dev/dri/card0
b01a6000-b07e6000 rw-s 00007000 00:0d 15966      /dev/dri/card0
b07e6000-b08e6000 rw-s 00006000 00:0d 15966      /dev/dri/card0
b08e6000-b08f6000 rw-s 00004000 00:0d 15966      /dev/dri/card0
b08f6000-b48f6000 rw-s 00003000 00:0d 15966      /dev/dri/card0
b48f6000-b49a6000 r-xp 00000000 03:03 7920       /usr/lib/libstdc++.so.5.0.7
b49a6000-b49ab000 rw-p 000af000 03:03 7920       /usr/lib/libstdc++.so.5.0.7
b49ab000-b49b0000 rw-p b49ab000 00:00 0 
b49b0000-b520d000 r-xp 00000000 03:03 18031      /usr/lib/dri/fglrx_dri.so
b520d000-b5257000 rw-p 0085d000 03:03 18031      /usr/lib/dri/fglrx_dri.so
b5257000-b52e1000 rw-p b5257000 00:00 0 
b52e1000-b5379000 r-xp 00000000 03:03 18021      /usr/lib/libGL.so.1.2
b5379000-b537e000 rw-p 00098000 03:03 18021      /usr/lib/libGL.so.1.2
b537e000-b5381000 rw-p b537e000 00:00 0 
b5381000-b538a000 r-xp 00000000 03:03 5478       /lib/tls/i686/cmov/libnss_files-2.5.so
b538a000-b538c000 rw-p 00008000 03:03 5478       /lib/tls/i686/cmov/libnss_files-2.5.so
b538c000-b5394000 r-xp 00000000 03:03 5482       /lib/tls/i686/cmov/libnss_nis-2.5.so
b5394000-b5396000 rw-p 00007000 03:03 5482       /lib/tls/i686/cmov/libnss_nis-2.5.so
b5396000-b539d000 r-xp 00000000 03:03 5474       /lib/tls/i686/cmov/libnss_compat-2.5.so
b539d000-b539f000 rw-p 00006000 03:03 5474       /lib/tls/i686/cmov/libnss_compat-2.5.so
b539f000-b53a5000 r-xp 00000000 03:03 12570      /usr/lib/openoffice/program/shlibloader.uno.so
b53a5000-b53a6000 rw-p 00005000 03:03 12570      /usr/lib/openoffice/program/shlibloader.uno.so
b53a6000-b53ad000 rwxp b53a6000 00:00 0 
b53ad000-b5484000 r--p 00000000 03:03 11015      /usr/lib/locale/en_US.utf8/LC_COLLATE
b5484000-b54d1000 r-xp 00000000 03:03 7272       /usr/lib/libXt.so.6.0.0
b54d1000-b54d5000 rw-p 0004c000 03:03 7272       /usr/lib/libXt.so.6.0.0
b54d5000-b5517000 r-xp 00000000 03:03 7190       /usr/lib/libFLAC.so.7.0.0
b5517000-b5518000 rw-p 00041000 03:03 7190       /usr/lib/libFLAC.so.7.0.0
b5518000-b5520000 r-xp 00000000 03:03 7918       /usr/lib/libstartup-notification-1.so.0.0.0
b5520000-b5521000 rw-p 00007000 03:03 7918       /usr/lib/libstartup-notification-1.so.0.0.0
b5521000-b5536000 r-xp 00000000 03:03 7306       /usr/lib/libaudio.so.2.4
b5536000-b5537000 rw-p 00015000 03:03 7306       /usr/lib/libaudio.so.2.4
b5537000-b553d000 r-xp 00000000 03:03 7846       /usr/lib/libportaudio.so.0.0.18
b553d000-b553e000 rw-p 00005000 03:03 7846       /usr/lib/libportaudio.so.0.0.18
b553e000-b5595000 r-xp 00000000 03:03 7902       /usr/lib/libsndfile.so.1.0.16
b5595000-b5597000 rw-p 00056000 03:03 7902       /usr/lib/libsndfile.so.1.0.16
b5597000-b559b000 rw-p b5597000 00:00 0 
b559b000-b55ae000 r-xp 00000000 03:03 5472       /lib/tls/i686/cmov/libnsl-2.5.so
b55ae000-b55b0000 rw-p 00012000 03:03 5472       /lib/tls/i686/cmov/libnsl-2.5.so
b55b0000-b55b2000 rw-p b55b0000 00:00 0 
b55b2000-b5631000 r-xp 00000000 03:03 12501      /usr/lib/openoffice/program/libvclplug_gen680li.so
b5631000-b5639000 rw-p 0007f000 03:03 12501      /usr/lib/openoffice/program/libvclplug_gen680li.so
b5639000-b563a000 rw-p b5639000 00:00 0 
b563a000-b566b000 r-xp 00000000 03:03 7369       /usr/lib/libdbus-1.so.3.2.0
b566b000-b566c000 rw-p 00031000 03:03 7369       /usr/lib/libdbus-1.so.3.2.0
b566c000-b5686000 r-xp 00000000 03:03 7371       /usr/lib/libdbus-glib-1.so.2.1.0
b5686000-b5687000 rw-p 0001a000 03:03 7371       /usr/lib/libdbus-glib-1.so.2.1.0
b5687000-b568e000 r-xp 00000000 03:03 5491       /lib/tls/i686/cmov/librt-2.5.so
b568e000-b5690000 rw-p 00006000 03:03 5491       /lib/tls/i686/cmov/librt-2.5.so
b5690000-b56a9000 r-xp 00000000 03:03 7302       /usr/lib/libatk-1.0.so.0.1809.1
b56a9000-b56ab000 rw-p 00018000 03:03 7302       /usr/lib/libatk-1.0.so.0.1809.1
b56ab000-b59fc000 r-xp 00000000 03:03 7639       /usr/lib/libgtk-x11-2.0.so.0.1000.11
b59fc000-b5a02000 rw-p 00351000 03:03 7639       /usr/lib/libgtk-x11-2.0.so.0.1000.11
b5a02000-b5a03000 rw-p b5a02000 00:00 0 
b5a03000-b5a04000 rw-s 00005000 00:0d 15966      /dev/dri/card0
b5a04000-b5a06000 rw-s 00002000 00:0d 15966      /dev/dri/card0
b5a06000-b5a07000 r-xp 00000000 03:03 9358       /usr/lib/gconv/ISO8859-1.so
b5a07000-b5a09000 rw-p 00000000 03:03 9358       /usr/lib/gconv/ISO8859-1.so
b5a09000-b5a0a000 r--p 00000000 03:03 11021      /usr/lib/locale/en_US.utf8/LC_NUMERIC
b5a0a000-b5a0b000 r--p 00000000 03:03 11024      /usr/lib/locale/en_US.utf8/LC_TIME
b5a0b000-b5a0c000 r--p 00000000 03:03 11019      /usr/lib/locale/en_US.utf8/LC_MONETARY
b5a0c000-b5a0d000 r--p 00000000 03:03 11025      /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b5a0d000-b5a0e000 r--p 00000000 03:03 11022      /usr/lib/locale/en_US.utf8/LC_PAPER
b5a0e000-b5a0f000 r--p 00000000 03:03 11020      /usr/lib/locale/en_US.utf8/LC_NAME
b5a0f000-b5a10000 r--p 00000000 03:03 11014      /usr/lib/locale/en_US.utf8/LC_ADDRESS
b5a10000-b5a11000 r--p 00000000 03:03 11023      /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b5a11000-b5a5c000 r-xp 00000000 03:03 12502      /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5a5c000-b5a62000 rw-p 0004a000 03:03 12502      /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5a62000-b5a9d000 r--p 00000000 03:03 11016      /usr/lib/locale/en_US.utf8/LC_CTYPE
b5a9d000-b5aa1000 rw-p b5a9d000 00:00 0 
b5aa1000-b5ac3000 r-xp 00000000 03:03 7840       /usr/lib/libpng12.so.0.15.0
b5ac3000-b5ac4000 rw-p 00021000 03:03 7840       /usr/lib/libpng12.so.0.15.0
b5ac4000-b5aee000 r-xp 00000000 03:03 7819       /usr/lib/libpangoft2-1.0.so.0.1600.2
b5aee000-b5aef000 rw-p 0002a000 03:03 7819       /usr/lib/libpangoft2-1.0.so.0.1600.2
b5aef000-b5af0000 rw-p b5aef000 00:00 0 
b5af0000-b5c07000 r-xp 00000000 03:03 7980       /usr/lib/libxml2.so.2.6.27
b5c07000-b5c0d000 rw-p 00116000 03:03 7980       /usr/lib/libxml2.so.2.6.27
b5c0d000-b5c2b000 r-xp 00000000 03:03 7427       /usr/lib/libexpat.so.1.0.0
b5c2b000-b5c2d000 rw-p 0001d000 03:03 7427       /usr/lib/libexpat.so.1.0.0
b5c2d000-b5cc1000 r-xp 00000000 03:03 7528       /usr/lib/libglib-2.0.so.0.1200.11
b5cc1000-b5cc2000 rw-p 00093000 03:03 7528       /usr/lib/libglib-2.0.so.0.1200.11
b5cc2000-b5cc4000 r-xp 00000000 03:03 7538       /usr/lib/libgmodule-2.0.so.0.1200.11
b5cc4000-b5cc5000 rw-p 00002000 03:03 7538       /usr/lib/libgmodule-2.0.so.0.1200.11
b5cc5000-b5cc6000 rw-p b5cc5000 00:00 0 
b5cc6000-b5cff000 r-xp 00000000 03:03 7582       /usr/lib/libgobject-2.0.so.0.1200.11
b5cff000-b5d00000 rw-p 00039000 03:03 7582       /usr/lib/libgobject-2.0.so.0.1200.11
b5d00000-b5d6e000 r-xp 00000000 03:03 7335       /usr/lib/libcairo.so.2.11.1
b5d6e000-b5d70000 rw-p 0006d000 03:03 7335       /usr/lib/libcairo.so.2.11.1
b5d70000-b5dac000 r-xp 00000000 03:03 7815       /usr/lib/libpango-1.0.so.0.1600.2
b5dac000-b5dae000 rw-p 0003b000 03:03 7815       /usr/lib/libpango-1.0.so.0.1600.2
b5dae000-b5db2000 r-xp 00000000 03:03 7248       /usr/lib/libXfixes.so.3.1.0
b5db2000-b5db3000 rw-p 00003000 03:03 7248       /usr/lib/libXfixes.so.3.1.0
b5db3000-b5dbb000 r-xp 00000000 03:03 7238       /usr/lib/libXcursor.so.1.0.2
b5dbb000-b5dbc000 rw-p 00007000 03:03 7238       /usr/lib/libXcursor.so.1.0.2
b5dbc000-b5dc1000 r-xp 00000000 03:03 7266       /usr/lib/libXrandr.so.2.1.0
b5dc1000-b5dc2000 rw-p 00005000 03:03 7266       /usr/lib/libXrandr.so.2.1.0
b5dc2000-b5dc3000 rw-p b5dc2000 00:00 0 
b5dc3000-b5dca000 r-xp 00000000 03:03 7254       /usr/lib/libXi.so.6.0.0
b5dca000-b5dcb000 rw-p 00006000 03:03 7254       /usr/lib/libXi.so.6.0.0
b5dcb000-b5dcd000 r-xp 00000000 03:03 7256       /usr/lib/libXinerama.so.1.0.0
b5dcd000-b5dce000 rw-p 00001000 03:03 7256       /usr/lib/libXinerama.so.1.0.0
b5dce000-b5dd5000 r-xp 00000000 03:03 7268       /usr/lib/libXrender.so.1.3.0
b5dd5000-b5dd6000 rw-p 00006000 03:03 7268       /usr/lib/libXrender.so.1.3.0
b5dd6000-b5ddd000 r-xp 00000000 03:03 7817       /usr/lib/libpangocairo-1.0.so.0.1600.2
b5ddd000-b5dde000 rw-p 00007000 03:03 7817       /usr/lib/libpangocairo-1.0.so.0.1600.2
b5dde000-b5df4000 r-xp 00000000 03:03 7492       /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5df4000-b5df5000 rw-p 00015000 03:03 7492       /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5df5000-b5e78000 r-xp 00000000 03:03 7490       /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5e78000-b5e7b000 rw-p 00083000 03:03 7490       /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5e7b000-b5e7c000 rw-p b5e7b000 00:00 0 
b5e7c000-b5e7e000 r-xp 00000000 03:03 7827       /usr/lib/libpaper.so.1.1.2
b5e7e000-b5e7f000 rw-p 00001000 03:03 7827       /usr/lib/libpaper.so.1.1.2
b5e7f000-b682e000 r--p 00000000 03:03 7680       /usr/lib/libicudata.so.36.0
b682e000-b682f000 rw-p 009ae000 03:03 7680       /usr/lib/libicudata.so.36.0
b682f000-b6833000 r-xp 00000000 03:03 7242       /usr/lib/libXdmcp.so.6.0.0
b6833000-b6834000 rw-p 00003000 03:03 7242       /usr/lib/libXdmcp.so.6.0.0
b6834000-b6836000 r-xp 00000000 03:03 7231       /usr/lib/libXau.so.6.0.0
b6836000-b6837000 rw-p 00001000 03:03 7231       /usr/lib/libXau.so.6.0.0
b6837000-b6838000 rw-p b6837000 00:00 0 
b6838000-b683d000 r-xp 00000000 03:03 5465       /lib/tls/i686/cmov/libcrypt-2.5.so
b683d000-b683f000 rw-p 00004000 03:03 5465       /lib/tls/i686/cmov/libcrypt-2.5.so
b683f000-b6866000 rw-p b683f000 00:00 0 
b6866000-b686d000 r-xp 00000000 03:03 2259       /lib/libpam.so.0.79
b686d000-b686e000 rw-p 00007000 03:03 2259       /lib/libpam.so.0.79
b686e000-b6872000 r-xp 00000000 03:03 12493      /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b6872000-b6873000 rw-p 00003000 03:03 12493      /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b6873000-b688a000 r-xp 00000000 03:03 12409      /usr/lib/openoffice/program/libjvmfwk.so.3
b688a000-b688b000 rw-p 00017000 03:03 12409      /usr/lib/openoffice/program/libjvmfwk.so.3
b688b000-b688c000 rw-p b688b000 00:00 0 
b688c000-b68aa000 r-xp 00000000 03:03 7709       /usr/lib/libjpeg.so.62.0.0
b68aa000-b68ab000 rw-p 0001d000 03:03 7709       /usr/lib/libjpeg.so.62.0.0
b68ab000-b68ce000 r-xp 00000000 03:03 7433       /usr/lib/libfontconfig.so.1.2.0
b68ce000-b68d6000 rw-p 00023000 03:03 7433       /usr/lib/libfontconfig.so.1.2.0
b68d6000-b68e9000 r-xp 00000000 03:03 7986       /usr/lib/libz.so.1.2.3
b68e9000-b68ea000 rw-p 00012000 03:03 7986       /usr/lib/libz.so.1.2.3
b68ea000-b6952000 r-xp 00000000 03:03 7443       /usr/lib/libfreetype.so.6.3.10
b6952000-b6955000 rw-p 00068000 03:03 7443       /usr/lib/libfreetype.so.6.3.10
b6955000-b6959000 r-xp 00000000 03:03 12408      /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b6959000-b695a000 rw-p 00003000 03:03 12408      /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b695a000-b695b000 rw-p b695a000 00:00 0 
b695b000-b6a00000 r-xp 00000000 03:03 12434      /usr/lib/openoffice/program/libpsp680li.so
b6a00000-b6a49000 rw-p 000a5000 03:03 12434      /usr/lib/openoffice/program/libpsp680li.so
b6a49000-b6a4b000 rw-p b6a49000 00:00 0 
b6a4b000-b6a8a000 r-xp 00000000 03:03 7686       /usr/lib/libicule.so.36.0
b6a8a000-b6a8c000 rw-p 0003f000 03:03 7686       /usr/lib/libicule.so.36.0
b6a8c000-b6ba2000 r-xp 00000000 03:03 7692       /usr/lib/libicuuc.so.36.0
b6ba2000-b6ba9000 rw-p 00116000 03:03 7692       /usr/lib/libicuuc.so.36.0
b6ba9000-b6bab000 rw-p b6ba9000 00:00 0 
b6bab000-b6c21000 r-xp 00000000 03:03 12325      /usr/lib/openoffice/program/libbasegfx680li.so
b6c21000-b6c22000 rw-p 00076000 03:03 12325      /usr/lib/openoffice/program/libbasegfx680li.so
b6c22000-b6c7b000 r-xp 00000000 03:03 12461      /usr/lib/openoffice/program/libsot680li.so
b6c7b000-b6c7e000 rw-p 00059000 03:03 12461      /usr/lib/openoffice/program/libsot680li.so
b6c7e000-b6c7f000 rw-p b6c7e000 00:00 0 
b6c7f000-b6dba000 r-xp 00000000 03:03 5461       /lib/tls/i686/cmov/libc-2.5.so
b6dba000-b6dbb000 r--p 0013b000 03:03 5461       /lib/tls/i686/cmov/libc-2.5.so
b6dbb000-b6dbd000 rw-p 0013c000 03:03 5461       /lib/tls/i686/cmov/libc-2.5.so
b6dbd000-b6dc0000 rw-p b6dbd000 00:00 0 
b6dc0000-b6dcb000 r-xp 00000000 03:03 2225       /lib/libgcc_s.so.1
b6dcb000-b6dcc000 rw-p 0000a000 03:03 2225       /lib/libgcc_s.so.1
b6dcc000-b6df1000 r-xp 00000000 03:03 5469       /lib/tls/i686/cmov/libm-2.5.so
b6df1000-b6df3000 rw-p 00024000 03:03 5469       /lib/tls/i686/cmov/libm-2.5.so
b6df3000-b6ed2000 r-xp 00000000 03:03 7922       /usr/lib/libstdc++.so.6.0.8
b6ed2000-b6ed5000 r--p 000de000 03:03 7922       /usr/lib/libstdc++.so.6.0.8
b6ed5000-b6ed7000 rw-p 000e1000 03:03 7922       /usr/lib/libstdc++.so.6.0.8
b6ed7000-b6edd000 rw-p b6ed7000 00:00 0 
b6edd000-b6f6f000 r-xp 00000000 03:03 7924       /usr/lib/libstlport.so.5.1.0
b6f6f000-b6f73000 rw-p 00091000 03:03 7924       /usr/lib/libstlport.so.5.1.0
b6f73000-b6f77000 rw-p b6f73000 00:00 0 
b6f77000-b6f8a000 r-xp 00000000 03:03 5487       /lib/tls/i686/cmov/libpthread-2.5.so
b6f8a000-b6f8c000 rw-p 00013000 03:03 5487       /lib/tls/i686/cmov/libpthread-2.5.so
b6f8c000-b6f8f000 rw-p b6f8c000 00:00 0 
b6f8f000-b6f91000 r-xp 00000000 03:03 5467       /lib/tls/i686/cmov/libdl-2.5.so
b6f91000-b6f93000 rw-p 00001000 03:03 5467       /lib/tls/i686/cmov/libdl-2.5.so
b6f93000-b7080000 r-xp 00000000 03:03 7225       /usr/lib/libX11.so.6.2.0
b7080000-b7084000 rw-p 000ed000 03:03 7225       /usr/lib/libX11.so.6.2.0
b7084000-b7099000 r-xp 00000000 03:03 7203       /usr/lib/libICE.so.6.3.0
b7099000-b709b000 rw-p 00014000 03:03 7203       /usr/lib/libICE.so.6.3.0
b709b000-b709c000 rw-p b709b000 00:00 0 
b709c000-b70a4000 r-xp 00000000 03:03 7221       /usr/lib/libSM.so.6.0.0
b70a4000-b70a5000 rw-p 00007000 03:03 7221       /usr/lib/libSM.so.6.0.0
b70a5000-b70b2000 r-xp 00000000 03:03 7246       /usr/lib/libXext.so.6.4.0
b70b2000-b70b3000 rw-p 0000d000 03:03 7246       /usr/lib/libXext.so.6.4.0
b70b3000-b70b4000 r--p 00000000 03:03 11018      /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b70b4000-b70b5000 r--p 00000000 03:03 11017      /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b70b5000-b70b9000 r-xp 00000000 03:03 7636       /usr/lib/libgthread-2.0.so.0.1200.11
b70b9000-b70ba000 rw-p 00003000 03:03 7636       /usr/lib/libgthread-2.0.so.0.1200.11
b70ba000-b70c1000 r--s 00000000 03:03 9411       /usr/lib/gconv/gconv-modules.cache
b70c1000-b72f2000 r-xp 00000000 03:03 12479      /usr/lib/openoffice/program/libtk680li.so
b72f2000-b731a000 rw-p 00231000 03:03 12479      /usr/lib/openoffice/program/libtk680li.so
b731a000-b731d000 rw-p b731a000 00:00 0 
b731d000-b736a000 r-xp 00000000 03:03 12492      /usr/lib/openoffice/program/libuno_sal.so.3
b736a000-b736d000 rw-p 0004c000 03:03 12492      /usr/lib/openoffice/program/libuno_sal.so.3
b736d000-b736f000 rw-p b736d000 00:00 0 
b736f000-b739d000 r-xp 00000000 03:03 12490      /usr/lib/openoffice/program/libuno_cppu.so.3
b739d000-b739e000 rw-p 0002d000 03:03 12490      /usr/lib/openoffice/program/libuno_cppu.so.3
b739e000-b740a000 r-xp 00000000 03:03 12491      /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b740a000-b740d000 rw-p 0006c000 03:03 12491      /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b740d000-b742f000 r-xp 00000000 03:03 12503      /usr/lib/openoffice/program/libvos3gcc3.so
b742f000-b7431000 rw-p 00022000 03:03 12503      /usr/lib/openoffice/program/libvos3gcc3.so
b7431000-b74ac000 r-xp 00000000 03:03 12483      /usr/lib/openoffice/program/libucbhelper3gcc3.so
b74ac000-b74b0000 rw-p 0007b000 03:03 12483      /usr/lib/openoffice/program/libucbhelper3gcc3.so
b74b0000-b74b1000 rw-p b74b0000 00:00 0 
b74b1000-b75ad000 r-xp 00000000 03:03 12331      /usr/lib/openoffice/program/libcomphelp4gcc3.so
b75ad000-b75b5000 rw-p 000fc000 03:03 12331      /usr/lib/openoffice/program/libcomphelp4gcc3.so
b75b5000-b75b6000 rw-p b75b5000 00:00 0 
b75b6000-b75ba000 r-xp 00000000 03:03 12385      /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b75ba000-b75bb000 rw-p 00004000 03:03 12385      /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b75bb000-b765a000 r-xp 00000000 03:03 12480      /usr/lib/openoffice/program/libtl680li.so
b765a000-b765d000 rw-p 0009e000 03:03 12480      /usr/lib/openoffice/program/libtl680li.so
b765d000-b76ea000 r-xp 00000000 03:03 12497      /usr/lib/openoffice/program/libutl680li.so
b76ea000-b76ef000 rw-p 0008c000 03:03 12497      /usr/lib/openoffice/program/libutl680li.so
b76ef000-b7ad1000 r-xp 00000000 03:03 12471      /usr/lib/openoffice/program/libsvt680li.so
b7ad1000-b7af6000 rw-p 003e1000 03:03 12471      /usr/lib/openoffice/program/libsvt680li.so
b7af6000-b7af8000 rw-p b7af6000 00:00 0 
b7af8000-b7c0c000 r-xp 00000000 03:03 12470      /usr/lib/openoffice/program/libsvl680li.so
b7c0c000-b7c12000 rw-p 00114000 03:03 12470      /usr/lib/openoffice/program/libsvl680li.so
b7c12000-b7f80000 r-xp 00000000 03:03 12500      /usr/lib/openoffice/program/libvcl680li.so
b7f80000-b7f94000 rw-p 0036e000 03:03 12500      /usr/lib/openoffice/program/libvcl680li.so
b7f94000-b7f97000 rw-p b7f94000 00:00 0 
b7f97000-b7fb0000 r-xp 00000000 03:03 2182       /lib/ld-2.5.so
b7fb0000-b7fb2000 rw-p 00019000 03:03 2182       /lib/ld-2.5.so
bfebb000-bff00000 rwxp bfebb000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
```

---

### Post by lamborghiniwang on 2007-04-30
I'm having the same problem. I guess the problem is caused by SCIM but I'm not sure.

EDIT: Problem solved. Here is what I did:
1) install scim-bridge, scim-bridge-agent, scim-bridge-client-gtk using Synaptic
2) set GTK_IM_MODULE=scim-bridge in /usr/bin/ooffice, my ooffice script looks like this:
```
  
#!/bin/sh
GTK_IM_MODULE=scim-bridge
export OOO_EXTRA_ARG=''
/usr/lib/openoffice/program/ooqstart  "$@"  

```

---

