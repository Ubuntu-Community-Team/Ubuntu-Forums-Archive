---
title: "pure-ftpd &amp; pureadmin  problems with virtual users"
date: 2009-02-02
forum: General Help
---

### Post by access-denied on 2009-02-02
I try to create the joe user as virtual user but all my attempts are ending with login failed :(
I tried misc things but still no progress...
e.g. [http://ubuntuforums.org/archive/index.php/t-213266.html](http://ubuntuforums.org/archive/index.php/t-213266.html) ...nothing!

Has anyone successfully tried to install pure-ftp common & pure-ftp & pureadmin with success and then to create a virtual user that can login?
in ubuntu 8.10 ????

If so pls post a reply pls!!!!

---

### Post by access-denied on 2009-02-03
The good new...
finally i managed to create the joe virtual user... but!!!!
... without the pureadmin tool which seems that in my 8.10 ubuntu doesn't fit well...
So,
[I]1. pureadmin doesn't stop the pure-ftp service. Or at least after all the tries seems that something is changed and can not stop pure-ftp service.
[/I]*2. pureadmin tool crashes when i try to open online help from menu*
```
/etc$ sudo pureadmin
*** glibc detected *** pureadmin: double free or corruption (out): 0x00007f310bbb0780 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f310b8bd938]
/lib/libc.so.6(cfree+0x76)[0x7f310b8bff86]
pureadmin(misc_find_webbrowser+0x1bc)[0x41777c]
pureadmin[0x410cdb]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x16d)[0x7f310c8ec25d]
/usr/lib/libgobject-2.0.so.0[0x7f310c901f5d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b8)[0x7f310c903608]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f310c903b33]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x6b)[0x7f310ec6203b]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0xfd)[0x7f310eb669ed]
/usr/lib/libgtk-x11-2.0.so.0[0x7f310eb68435]
/usr/lib/libgtk-x11-2.0.so.0[0x7f310eb59908]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x16d)[0x7f310c8ec25d]
/usr/lib/libgobject-2.0.so.0[0x7f310c901c3b]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x63a)[0x7f310c90348a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f310c903b33]
/usr/lib/libgtk-x11-2.0.so.0[0x7f310ec5c74e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xe3)[0x7f310eb52273]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2e3)[0x7f310eb53393]
/usr/lib/libgdk-x11-2.0.so.0[0x7f310e47906c]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x23b)[0x7f310c44fd3b]
/usr/lib/libglib-2.0.so.0[0x7f310c45350d]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1cd)[0x7f310c453a3d]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f310eb537a7]
pureadmin(main+0x4cb)[0x40f09b]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f310b862466]
pureadmin[0x40e969]
======= Memory map: ========
00400000-0042e000 r-xp 00000000 08:06 12910835                           /usr/bin/pureadmin
0062d000-0062e000 r--p 0002d000 08:06 12910835                           /usr/bin/pureadmin
0062e000-0062f000 rw-p 0002e000 08:06 12910835                           /usr/bin/pureadmin
0062f000-00631000 rw-p 0062f000 00:00 0 
0151a000-01b3e000 rw-p 0151a000 00:00 0                                  [heap]
41a55000-41a56000 ---p 41a55000 00:00 0 
41a56000-42256000 rw-p 41a56000 00:00 0 
7f3100000000-7f3100021000 rw-p 7f3100000000 00:00 0 
7f3100021000-7f3104000000 ---p 7f3100021000 00:00 0 
7f310769e000-7f31076b4000 r-xp 00000000 08:06 13066251                   /lib/libgcc_s.so.1
7f31076b4000-7f31078b4000 ---p 00016000 08:06 13066251                   /lib/libgcc_s.so.1
7f31078b4000-7f31078b5000 r--p 00016000 08:06 13066251                   /lib/libgcc_s.so.1
7f31078b5000-7f31078b6000 rw-p 00017000 08:06 13066251                   /lib/libgcc_s.so.1
7f31078cb000-7f310792b000 rw-s 00000000 00:09 21626911                   /SYSV00000000 (deleted)
7f310792b000-7f310798b000 rw-s 00000000 00:09 21594141                   /SYSV00000000 (deleted)
7f310798b000-7f3107a0d000 rw-p 7f310798b000 00:00 0 
7f3107a0d000-7f3107a59000 r--p 00000000 08:06 1836797                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
7f3107a59000-7f3107b5d000 rw-p 7f3107a59000 00:00 0 
7f3107b5d000-7f3107be6000 r--p 00000000 08:06 1836794                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f3107be6000-7f3107cea000 rw-p 7f3107be6000 00:00 0 
7f3107cea000-7f3107cec000 r-xp 00000000 08:06 1713092                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3107cec000-7f3107eeb000 ---p 00002000 08:06 1713092                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3107eeb000-7f3107eec000 r--p 00001000 08:06 1713092                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3107eec000-7f3107eed000 rw-p 00002000 08:06 1713092                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3107eed000-7f3107f82000 r--p 00000000 08:06 1836795                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f3107f82000-7f3107f86000 r-xp 00000000 08:06 1720882                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f3107f86000-7f3108186000 ---p 00004000 08:06 1720882                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.soAborted

```
something bothers pureadmin in my system and i don't have the courage to find what right now :(
3. If i don't install pureadmin and setup my pure-ftp service to work with joe as virtual user (manually) and then try to install pureadmin (from synaptic-manager always) pureadmin tries allways to create the ftpuser & ftpgroup and because are already created manually it stacks there and doesn't ignore the error, so all my progress should be deleted and i have to find a way to make pureadmin to work.
4. Removing everything (even the ftpuser & ftpgroup &* /home/ftpusers directory that are left) and reinstalling pureadmin (+pure-ftp, +pure-ftp-common) with synaptic still no progress....

So my next step, is to hit my head up to the wall (again) for hours till i find a solution **or** somebody that has already been in a similar situation (Unbuntu 8.10, pureadmin, pureftpd, pureftpd-common) and found a solution posts it here :)

Unfortunally i don't know exactly why pure-ftpd + pure-ftpd-common (without pureadmin) didn't work at start, mayby the 65pam link needed to be deleted.

---

