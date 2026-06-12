---
title: "Open Office Crash direct at launch"
date: 2007-07-05
forum: Desktop Environments
---

### Post by jmaryinchina on 2007-07-05
Hardware : DELL optiplex 320
Ubuntu Alternate install : 64 Bit with RAID1
Open Office Launch :
ju@optiplex320:~$ oowriter 
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x00000000006a7790 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b4c77c56b23]
/lib/libc.so.6(cfree+0x8c)[0x2b4c77c5a26c]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x17)[0x44b737]
/usr/lib/libscim-1.0.so.8[0x2aaaaf869789]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x45)[0x2aaaaf86a435]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x30)[0x2aaaaf865910]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0x2aaaaf5d4e0c]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x39c)[0x2b4c7c76206c]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x85a)[0x2b4c7c748aba]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21c)[0x2b4c7c748eac]
/usr/lib/libgobject-2.0.so.0(g_object_new+0xa1)[0x2b4c7c7490e1]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x46)[0x2aaaaf5cab16]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb6)[0x2b4c7dbaf446]
/usr/lib/libgtk-x11-2.0.so.0[0x2b4c7dbafdd6]
/usr/lib/libgtk-x11-2.0.so.0[0x2b4c7dbb0009]
/usr/lib/libgtk-x11-2.0.so.0[0x2b4c7db604c9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10a)[0x2b4c7c7437da]
/usr/lib/libgobject-2.0.so.0[0x2b4c7c75384d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x833)[0x2b4c7c754843]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x2b4c7c754a13]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x8f)[0x2b4c7dcd152f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1ee)[0x2b4c7dcd1a8e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xda)[0x2b4c7db887aa]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10a)[0x2b4c7c7437da]
/usr/lib/libgobject-2.0.so.0[0x2b4c7c75384d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x833)[0x2b4c7c754843]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x2b4c7c754a13]
/usr/lib/openoffice/program/libvclplug_gtk680lx.so[0x2b4c7d84b3ef]
/usr/lib/openoffice/program/libvclplug_gtk680lx.so[0x2b4c7d84d4c2]
/usr/lib/openoffice/program/libvcl680lx.so[0x2b4c73be43e4]
/usr/lib/openoffice/program/libvcl680lx.so[0x2b4c73b77574]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x57)[0x2b4c73b77eb7]
/usr/lib/openoffice/program/libsvt680lx.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x21)[0x2b4c744a8781]
/usr/lib/openoffice/program/libsvt680lx.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdjhhs+0x2a)[0x2b4c7447ee6a]
/usr/lib/openoffice/program/libsvt680lx.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdjS5_h+0x29)[0x2b4c7447c4e9]
/usr/lib/openoffice/program/libspl680lx.so[0x2aaaaeca3c59]
/usr/lib/openoffice/program/libspl680lx.so[0x2aaaaec9b10d]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xc96)[0x427396]
/usr/lib/openoffice/program/libvcl680lx.so[0x2b4c73a11344]
/usr/lib/openoffice/program/libvcl680lx.so(_Z6SVMainv+0x25)[0x2b4c73a11435]
/usr/lib/openoffice/program/soffice.bin(main+0x3f)[0x41c10f]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b4c77c048e4]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x41bfa9]
======= Memory map: ========
00400000-00459000 r-xp 00000000 09:00 13927019                           /usr/lib/openoffice/program/soffice.bin
00659000-0065b000 rw-p 00059000 09:00 13927019                           /usr/lib/openoffice/program/soffice.bin
0065b000-00a17000 rw-p 0065b000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rwxp 40001000 00:00 0 
40801000-40802000 ---p 40801000 00:00 0 
40802000-41002000 rwxp 40802000 00:00 0 
2aaaaaabc000-2aaaaaad1000 r-xp 00000000 09:00 13927205                   /usr/lib/openoffice/program/uriproc.uno.so
2aaaaaad1000-2aaaaacd0000 ---p 00015000 09:00 13927205                   /usr/lib/openoffice/program/uriproc.uno.so
2aaaaacd0000-2aaaaacd3000 rw-p 00014000 09:00 13927205                   /usr/lib/openoffice/program/uriproc.uno.so
2aaaaacd3000-2aaaaacd9000 r-xp 00000000 09:00 13927009                   /usr/lib/openoffice/program/libspl_unx680lx.so
2aaaaacd9000-2aaaaaed8000 ---p 00006000 09:00 13927009                   /usr/lib/openoffice/program/libspl_unx680lx.so
2aaaaaed8000-2aaaaaed9000 rw-p 00005000 09:00 13927009                   /usr/lib/openoffice/program/libspl_unx680lx.so
2aaaaaed9000-2aaaaaeda000 rw-p 2aaaaaed9000 00:00 0 
2aaaaaeda000-2aaaaaf1c000 r-xp 00000000 09:00 13927195                   /usr/lib/openoffice/program/libucb1.so
2aaaaaf1c000-2aaaab11b000 ---p 00042000 09:00 13927195                   /usr/lib/openoffice/program/libucb1.so
2aaaab11b000-2aaaab120000 rw-p 00041000 09:00 13927195                   /usr/lib/openoffice/program/libucb1.so
2aaaab120000-2aaaab147000 r-xp 00000000 09:00 13927696                   /usr/lib/openoffice/program/ucpgvfs1.uno.so
2aaaab147000-2aaaab346000 ---p 00027000 09:00 13927696                   /usr/lib/openoffice/program/ucpgvfs1.uno.so
2aaaab346000-2aaaab349000 rw-p 00026000 09:00 13927696                   /usr/lib/openoffice/program/ucpgvfs1.uno.so
2aaaab35a000-2aaaab3bc000 r-xp 00000000 09:00 13783439                   /usr/lib/libgnomevfs-2.so.0.1800.1
2aaaab3bc000-2aaaab5bc000 ---p 00062000 09:00 13783439                   /usr/lib/libgnomevfs-2.so.0.1800.1
2aaaab5bc000-2aaaab5c1000 rw-p 00062000 09:00 13783439                   /usr/lib/libgnomevfs-2.so.0.1800.1
2aaaab5c1000-2aaaab636000 r-xp 00000000 09:00 13781488                   /usr/lib/libgnutls.so.13.0.9
2aaaab636000-2aaaab835000 ---p 00075000 09:00 13781488                   /usr/lib/libgnutls.so.13.0.9
2aaaab835000-2aaaab840000 rw-p 00074000 09:00 13781488                   /usr/lib/libgnutls.so.13.0.9
2aaaab840000-2aaaab843000 r-xp 00000000 09:00 13783397                   /usr/lib/libavahi-glib.so.1.0.1
2aaaab843000-2aaaaba42000 ---p 00003000 09:00 13783397                   /usr/lib/libavahi-glib.so.1.0.1
2aaaaba42000-2aaaaba43000 rw-p 00002000 09:00 13783397                   /usr/lib/libavahi-glib.so.1.0.1
2aaaaba43000-2aaaaba4e000 r-xp 00000000 09:00 13783393                   /usr/lib/libavahi-common.so.3.4.3
2aaaaba4e000-2aaaabc4e000 ---p 0000b000 09:00 13783393                   /usr/lib/libavahi-common.so.3.4.3
2aaaabc4e000-2aaaabc4f000 rw-p 0000b000 09:00 13783393                   /usr/lib/libavahi-common.so.3.4.3
2aaaabc4f000-2aaaabc5e000 r-xp 00000000 09:00 13783395                   /usr/lib/libavahi-client.so.3.2.2
2aaaabc5e000-2aaaabe5e000 ---p 0000f000 09:00 13783395                   /usr/lib/libavahi-client.so.3.2.2
2aaaabe5e000-2aaaabe5f000 rw-p 0000f000 09:00 13783395                   /usr/lib/libavahi-client.so.3.2.2
2aaaabe5f000-2aaaabe70000 r-xp 00000000 09:00 23150628                   /lib/libresolv-2.5.so
2aaaabe70000-2aaaac070000 ---p 00011000 09:00 23150628                   /lib/libresolv-2.5.so
2aaaac070000-2aaaac072000 rw-p 00011000 09:00 23150628                   /lib/libresolv-2.5.so
2aaaac072000-2aaaac074000 rw-p 2aaaac072000 00:00 0 
2aaaac074000-2aaaac08a000 r-xp 00000000 09:00 23150655                   /lib/libselinux.so.1
2aaaac08a
** (process:2863): WARNING **: Unknown error forking main binary / abnormal early exit ...

---

### Post by limbourg31 on 2007-07-05
a binary error, it seems... reinstall openoffice i say or see if there are broken dependencies

---

### Post by dcstar on 2007-07-07
> **limbourg31 said:**
> a binary error, it seems... reinstall openoffice i say or see if there are broken dependencies

Or try stopping the CUPS process, and then see if OO suddenly starts working......    ;)

---

### Post by jmaryinchina on 2007-07-10
Stopping the cups process doesn't help anything.

full reinstall did the job.

---

