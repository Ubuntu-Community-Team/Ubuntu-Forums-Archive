---
title: "cannot open &quot;open office&quot;"
date: 2007-10-03
forum: Desktop Environments
---

### Post by fyplinux on 2007-10-03
Hi

When "open office" is started, the progress bar goes to its 50%, then it is terminated.

If i run oobase, i got the following message:
> *** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d0ab0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6d0a7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6d0de30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb73620bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xad7c7156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xad7c7f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xad7c2f05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xad868f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5d08b41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5cef1cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5cef5ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5cef7a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xad85db57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xad86d27c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb57e5d29]
/usr/lib/libgtk-x11-2.0.so.0[0xb57e693b]
/usr/lib/libgtk-x11-2.0.so.0[0xb57e6b39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb57e3f0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb578d71f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5cf69d9]
/usr/lib/libgobject-2.0.so.0[0xb5ce7e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5ce962b]
/usr/lib/libgobject-2.0.so.0[0xb5cfa59a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cfb627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cfb7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb5921bea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb59221ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb57baec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb57baf08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5cf5ee9]
/usr/lib/libgobject-2.0.so.0[0xb5ce7e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5ce962b]
/usr/lib/libgobject-2.0.so.0[0xb5cfa59a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cfb627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cfb7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb57711bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a542bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a56043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a60abd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7ebe285]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e4b32b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7e4bd57]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb791899e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb78ea1da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb78e755f]
/usr/lib/openoffice/program/libspl680li.so[0xad971926]
/usr/lib/openoffice/program/libspl680li.so[0xad968024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7ccbecc]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7ccbfd5]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6cb8ebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 08:05 1929942    /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 08:05 1929942    /usr/lib/openoffice/program/soffice.bin
0809e000-08381000 rw-p 0809e000 00:00 0          [heap]
ad600000-ad621000 rw-p ad600000 00:00 0 
ad621000-ad700000 ---p ad621000 00:00 0 
ad75f000-ad833000 r-xp 00000000 08:05 1243164    /usr/lib/libscim-1.0.so.8.1.0
ad833000-ad841000 rw-p 000d4000 08:05 1243164    /usr/lib/libscim-1.0.so.8.1.0
ad851000-ad872000 r-xp 00000000 08:05 1896924    /usr/lib/gtk
** (process:7631): WARNING **: Unknown error forking main binary / abnormal early exit ...


That is the problem, How can i solve it ?

Thank you

---

### Post by swisscow on 2007-10-03
I would try reinstalling first - in Synaptic search for openoffice, I think (and I'm not sure) open office core contains everything important - try right clicking and selecting reinstall. Alternatively, everything openoffice based - reinstall the lot!

Good luck

---

### Post by adrighem on 2007-10-08
I had the same problem. In my case it was caused by the theme I had chosen. Changing the theme to something else (like Clearlooks) made OOo work okay.

---

### Post by matigol on 2007-10-08
Maybe oOo is broken.
And maybe the thema.

It apperas with all oOo applications ?

---

### Post by willcritchlow on 2007-10-09
I am still having this problem (and I have tried changing theme).

Has anyone got any other ideas?

I don't know how to debug.

I also find that Firefox crashes when I try to print.

I'm sure these are related.

Please help!

Thanks
Will

---

### Post by Rui Pais on 2007-10-11
Hi,
have you tried to close any OOo quick launcher running (on taskbar at panels) and then:
```
 mv .openoffice.org2 .openoffice.org2_BACKUP
```
and try to run it again?

---

### Post by rfurman24 on 2007-10-18
It seems to be a problem with openoffice.org-gtk. Try uninstalling it and see if it helps. I hope they fix it soon.

---

