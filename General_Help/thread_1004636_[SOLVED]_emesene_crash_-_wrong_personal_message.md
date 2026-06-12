---
title: "[SOLVED] emesene crash - wrong personal message?"
date: 2008-12-07
forum: General Help
---

### Post by balta on 2008-12-07
> Edit:
I'm now sure that the problem is my weird personal message: I've tried to remove from the folder "/usr/share/emesene/plugins_base" the files "PersonalMessage.py" and "PersonalMessage.pyc" and without them I can normally log in, however I cannot save the personal message between the sessions and I have not found a way to reinstall the plugin or modify its status, even if change my personal message after returning the files the next time I try to log in it's a failure.

So the real question is: **how can I change or remove my personal message without being logged in?**

I've been trying to solve this alone but didn't manage to, so I'm asking you:
I've been using emesene for a long time, more or less two days ago it started to crash as soon as I try to log in my MSN account: I've already tried to completely remove emesene from synaptic and then reinstalling but first, it still remembers of me (even though I clearly chose 'complete' removal...), second it still crashes...
I tried loggin in from the emesene of a friend of mine and with other clients (pidgin, aMSN) there were no problems.

I'll post the debug notes I get when I start emesene from the terminal (show binary codes in debug >> off) :  

> 
:~$ emesene
>>> VER 1 MSNP13 CVR0
<<< VER 1 MSNP13
>>> CVR 2 0x0c0a winnt 5.1 i386 MSNMSGR 8.0.0792 msmsgs [email]ilbalta@hotmail.com[/email]
<<< CVR 2 8.1.0178 8.1.0178 8.1.0178 [http://msgruser.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe](http://msgruser.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe) [http://get.live.com/es](http://get.live.com/es)
>>> USR 3 TWN I [email]ilbalta@hotmail.com[/email]
<<< XFR 3 NS 207.46.107.69:1863 U D
>>> VER 1 MSNP13 CVR0
<<< VER 1 MSNP13
>>> CVR 2 0x0c0a winnt 5.1 i386 MSNMSGR 8.0.0792 msmsgs [email]ilbalta@hotmail.com[/email]
<<< CVR 2 8.1.0178 8.1.0178 8.1.0178 [http://msgruser.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe](http://msgruser.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe) [http://get.live.com/es](http://get.live.com/es)
>>> USR 3 TWN I [email]ilbalta@hotmail.com[/email]
<<< GCF 0 6328
<<< USR 3 TWN S ct=1228674013,rver=5.5.4177.0,wp=FS_40SEC_0_COMPACT,lc=1033,id=507,ru=http:%2F%2Fmessenger.msn.com,tw=0,kpp=1,kv=4,ver=2.1.6000.1,rn=1lgjBfIL,tpf=b0735e3a873dfb5e75054465196398e0
PASSPORT begin
200 OK
>>> USR 4 TWN S t=9K5bmoGkVG5l24t0cuh!YU8EdTN2eovTILXV0guRDmywNyN3lbz0Q4q7cb4Q5230IYgZtYF3gYcvV0AE4KW7NgwMUvO0eVAYaVB*R4Ro6MVecxi3P8cTpWt0TvlxlEkgDQ&p=9NILW40QqB246PBvIYw6m7y8BoRFc65pnUTnw6wxJzY24XkDFDWO3fc7i2Pv6oSZv8bkXmCJmlYfntg2IBahof2JWfvW!HEKFBVJrbgs0zdVkhgCZvLBvYCdazIZyE2EyRVpLd*b2TDDEaXWZff6VCh07YfvZ4h7wC8ZXbUKji89o$
<<< USR 4 OK [email]ilbalta@hotmail.com[/email] 1 0
We are in
<<< SBS 0 null
<<< MSG Hotmail Hotmail 551
>>> CHG 5 AWY 1342472198 0
duplicate pm
user [email]ilbalta@hotmail.com[/email] not found, returning dummy user
>>> CHG 6 AWY 1342472198 %3Cmsnobj%20Creator%3D%22ilbalta%40hotmail.com%22%20Size%3D%2215282%22%20Type%3D%223%22%20Location%3D%220%22%20Friendly%3D%22%22%20SHA1D%3D%22IhuPD/faMNlUDcuowrfnI0aM16g%3D%22%20SHA1C%3D%22MkbNWyPhw/nrezb/v2ff21xE0YA%3D%22/%3E
sqlite3 imported
info: reset player: org.gnome.Rhythmbox
info: not running, listening NameOwnerChanged
info: getStatus: Ok
>>> UUX 7 182
<Data><PSM>~ ~ ~  ~ (L)spam</PSM><CurrentMedia></CurrentMedia><MachineGuid></MachineGuid></Data>
*** glibc detected *** python: double free or corruption (!prev): 0x08db6398 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e5ea85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e624f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7aebb51]
/usr/lib/libpango-1.0.so.0[0xb7457ba4]
/usr/lib/libpango-1.0.so.0(pango_layout_set_attributes+0x3d)[0xb745910d]
/var/lib/python-support/python2.5/gtk-2.0/pango.so[0xb7043bb3]
python(PyEval_EvalFrameEx+0x5d13)[0x80c9ab3]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalCodeEx+0x6e7)[0x80cb1f7]
python(PyEval_EvalFrameEx+0x565e)[0x80c93fe]
python(PyEval_EvalCodeEx+0x6e7)[0x80cb1f7]
python(PyEval_EvalFrameEx+0x565e)[0x80c93fe]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalCodeEx+0x6e7)[0x80cb1f7]
python(PyEval_EvalFrameEx+0x565e)[0x80c93fe]
python(PyEval_EvalCodeEx+0x6e7)[0x80cb1f7]
python(PyEval_EvalFrameEx+0x565e)[0x80c93fe]
python(PyEval_EvalCodeEx+0x6e7)[0x80cb1f7]
python[0x811372e]
python(PyObject_Call+0x27)[0x805cb97]
python[0x8062bfb]
python(PyObject_Call+0x27)[0x805cb97]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c2e9c]
python(PyObject_CallObject+0x20)[0x805d040]
/var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so[0xb7c17afb]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb7bc7749]
/usr/lib/libgobject-2.0.so.0[0xb7bdbf7b]
/usr/lib/libgobject-2.0.so.0(g_signal_emitv+0x150)[0xb7bde0b0]
/var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so[0xb7c0cc78]
python(PyEval_EvalFrameEx+0x5d13)[0x80c9ab3]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalCodeEx+0x6e7)[0x80cb1f7]
python[0x811372e]
python(PyObject_Call+0x27)[0x805cb97]
python[0x8062bfb]
python(PyObject_Call+0x27)[0x805cb97]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c2e9c]
python(PyObject_CallObject+0x20)[0x805d040]
/var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so[0xb7c17afb]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb7bc7749]
/usr/lib/libgobject-2.0.so.0[0xb7bdbf7b]
/usr/lib/libgobject-2.0.so.0(g_signal_emitv+0x150)[0xb7bde0b0]
/var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so[0xb7c0cc78]
python(PyEval_EvalFrameEx+0x5d13)[0x80c9ab3]
python(PyEval_EvalFrameEx+0x5945)[0x80c96e5]
python(PyEval_EvalCodeEx+0x6e7)[0x80cb1f7]
python[0x811372e]
python(PyObject_Call+0x27)[0x805cb97]
python[0x8062bfb]
python(PyObject_Call+0x27)[0x805cb97]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c2e9c]
python(PyObject_CallObject+0x20)[0x805d040]
/var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so[0xb7c17afb]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb7bc7749]
/usr/lib/libgobject-2.0.so.0[0xb7bdbf7b]
/usr/lib/libgobject-2.0.so.0(g_signal_emitv+0x150)[0xb7bde0b0]
/var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so[0xb7c0cc78]
python(PyEval_EvalFrameEx+0x5d13)[0x80c9ab3]
======= Memory map: ========
08048000-08140000 r-xp 00000000 08:03 1622778    /usr/bin/python2.5
08140000-08165000 rw-p 000f7000 08:03 1622778    /usr/bin/python2.5
08165000-09034000 rw-p 08165000 00:00 0          [heap]
b3c00000-b3c21000 rw-p b3c00000 00:00 0 
b3c21000-b3d00000 ---p b3c21000 00:00 0 
b3de8000-b3e34000 r--p 00000000 08:03 1770912    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b3e34000-b5249000 r--p 00000000 08:03 1770807    /usr/share/fonts/truetype/arphic/uming.ttc
b5249000-b52c4000 r--p 00000000 08:03 1769507    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b52c4000-b52c5000 ---p b52c4000 00:00 0 
b52c5000-b5ac5000 rw-p b52c5000 00:00 0 
b5ac5000-b5ac6000 ---p b5ac5000 00:00 0 
b5ac6000-b6447000 rw-p b5ac6000 00:00 0 
b6447000-b645a000 r-xp 00000000 08:03 1704801    /usr/lib/python-support/python-dbus/python2.5/_dbus_bindings.so
b645a000-b6465000 rw-p 00012000 08:03 1704801    /usr/lib/python-support/python-dbus/python2.5/_dbus_bindings.so
b6465000-b64c8000 r-xp 00000000 08:03 1624397    /usr/lib/libsqlite3.so.0.8.6
b64c8000-b64ca000 rw-p 00062000 08:03 1624397    /usr/lib/libsqlite3.so.0.8.6
b64df000-b6513000 r-xp 00000000 08:03 1623076    /usr/lib/libdbus-1.so.3.4.0
b6513000-b6515000 rw-p 00033000 08:03 1623076    /usr/lib/libdbus-1.so.3.4.0
b6515000-b652f000 r-xp 00000000 08:03 1623800    /usr/lib/libdbus-glib-1.so.2.1.0
b652f000-b6530000 rw-p 0001a000 08:03 1623800    /usr/lib/libdbus-glib-1.so.2.1.0
b6530000-b6536000 r-xp 00000000 08:03 1624235    /usr/lib/libnotify.so.1.1.2
b6536000-b6537000 rw-p 00006000 08:03 1624235    /usr/lib/libnotify.so.1.1.2
b6537000-b6577000 r-xp 00000000 08:03 1704960    /usr/lib/python-support/python-libxml2/python2.5/libxml2mod.so
b6577000-b657c000 rw-p 00040000 08:03 1704960    /usr/lib/python-support/python-libxml2/python2.5/libxml2mod.so
b657c000-b6586000 r-xp 00000000 08:03 1624048    /usr/lib/libgstinterfaces-0.10.so.0.13.0
b6586000-b6587000 rw-p 00009000 08:03 1624048    /usr/lib/libgstinterfaces-0.10.so.0.13.0
b658d000-b659a000 r-xp 00000000 08:03 1706545    /usr/lib/python2.5/lib-dynload/_sqlite3.so
b659a000-b659c000 rw-p 0000c000 08:03 1706545    /usr/lib/python2.5/lib-dynload/_sqlite3.so
b659c000-b663c000 r-xp 00000000 08:03 1089560    /usr/lib/libgstreamer-0.10.so.0.16.0
b663c000-b6640000 rw-p 0009f000 08:03 1089560    /usr/lib/libgstreamer-0.10.so.0.16.0
b6640000-b6669000 r-xp 00000000 08:03 1089555    /usr/lib/libgstbase-0.10.so.0.16.0
b6669000-b666a000 rw-p 00029000 08:03 1089555    /usr/lib/libgstbase-0.10.so.0.16.0
b666a000-b666e000 r-xp 00000000 08:03 1089558    /usr/lib/libgstdataprotocol-0.10.so.0.16.0
b666e000-b666f000 rw-p 00003000 08:03 1089558    /usr/lib/libgstdataprotocol-0.10.so.0.16.0
b666f000-b6675000 r-xp 00000000 08:03 1089559    /usr/lib/libgstnet-0.10.so.0.16.0
b6675000-b6676000 rw-p 00005000 08:03 1089559    /usr/lib/libgstnet-0.10.so.0.16.0
b6676000-b6699000 r-xp 00000000 08:03 1089557    /usr/lib/libgstcontroller-0.10.so.0.16.0
b6699000-b669a000 rw-p 00023000 08:03 1089557    /usr/lib/libgstcontroller-0.10.so.0.16.0
b669a000-b66f9000 r-xp 00000000 08:03 1712306    /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so
b66f9000-b6701000 rw-p 0005f000 08:03 1712306    /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so
b6701000-b67ab000 r-xp 00000000 08:03 1623699    /usr/lib/libaspell.so.15.1.4
b67ab000-b67b0000 rw-p 000a9000 08:03 1623699    /usr/lib/libaspell.so.15.1.4
b67b0000-b67b3000 rw-p b67b0000 00:00 0 
b67b3000-b67b8000 r-xp 00000000 08:03 1624086    /usr/lib/libgtkspell.so.0.0.0
b67b8000-b67b9000 rw-p 00004000 08:03 1624086    /usr/lib/libgtkspell.so.0.0.0
b67b9000-b67ba000 r-xp 00000000 08:03 1704802    /usr/lib/python-support/python-dbus/python2.5/_dbus_glib_bindings.so
b67ba000-b67bb000 rw-p 00001000 08:03 1704802    /usr/lib/python-support/python-dbus/python2.5/_dbus_glib_bindings.so
b67bb000-b67bf000 r-xp 00000000 08:03 1704934    /usr/lib/python-support/python-notify/python2.5/gtk-2.0/pynotify/_pynotify.so
b67bf000-b67c0000 rw-p 00004000 08:03 1704934    /usr/lib/python-support/python-notify/python2.5/gtk-2.0/pynotify/_pynotify.so
b67c0000-b67cc000 r-xp 00000000 08:03 1712307    /usr/lib/python2.5/site-packages/gst-0.10/gst/interfaces.so
b67cc000-b67ce000 rw-p 0000b000 08:03 1712307    /usr/lib/python2.5/site-packages/gst-0.10/gst/interfaces.so
b67ce000-b67e5000 r-xp 00000000 08:03 598141     /lib/libselinux.so.1
b67e5000-b67e7000 rw-p 00016000 08:03 598141     /lib/libselinux.so.1
b67e7000-b6846000 r-xp 00000000 08:03 1089619    /usr/lib/libgio-2.0.so.0.0.0
b6846000-b6848000 rw-p 0005f000 08:03 1089619    /usr/lib/libgio-2.0.so.0.0.0
b6848000-b687a000 r-xp 00000000 08:03 1623772    /usr/lib/libcroco-0.6.so.3.0.1
b687a000-b687d000 rw-p 00031000 08:03 1623772    /usr/lib/libcroco-0.6.so.3.0.1
b687d000-b68ad000 r-xp 00000000 08:03 1624026    /usr/lib/libgsf-1.so.114.0.7
b68ad000-b68b0000 rw-p 0002f000 08:03 1624026    /usr/lib/libgsf-1.so.114.0.7
b68b0000-b68b1000 rw-p b68b0000 00:00 0 
b68b1000-b68e1000 r-xp 00000000 08:03 1624349    /usr/lib/librsvg-2.so.2.22.2
b68e1000-b68e2000 rw-p 00030000 08:03 1624349    /usr/lib/librsvg-2.so.2.22.2
b68e2000-b68e4000 r-xp 00000000 08:03 1712922    /usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gtkspell.so
b68e4000-b68e5000 rw-p 00001000 08:03 1712922    /usr/lib/python-support/python-gnome2-extras/python2.5/gtk-2.0/gtkspell.so
b68e5000-b68f4000 r-xp 00000000 08:03 1706454    /usr/lib/python2.5/lib-dynload/datetime.so
b68f4000-b68f7000 rw-p 0000e000 08:03 1706454    /usr/lib/python2.5/lib-dynload/datetime.so
b68f7000-b6906000 r-xp 00000000 08:03 614419     /lib/tls/i686/cmov/libresolv-2.7.so
b6906000-b6908000 rw-p 0000f000 08:03 614419     /lib/tls/i686/cmov/libresolv-2.7.so
b6908000-b690a000 rw-p b6908000 00:00 0 
b690a000-b690e000 r-xp 00000000 08:03 614412     /lib/tls/i686/cmov/libnss_dns-2.7.so
b690e000-b6910000 rw-p 00003000 08:03 614412     /lib/tls/i686/cmov/libnss_dns-2.7.so
b6910000-b6912000 r-xp 00000000 08:03 598111     /lib/libnss_mdns4_minimal.so.2
b6912000-b6913000 rw-p 00001000 08:03 598111     /lib/libnss_mdns4_minimal.so.2
b6914000-b6915000 r-xp 00000000 08:03 1706458    /usr/lib/python2.5/lib-dynload/_bisect.so
b6915000-b6916000 rw-p 00001000 08:03 1706458    /usr/lib/python2.5/lib-dynload/_bisect.so
b6916000-b6925000 r-xp 00000000 08:03 598054     /lib/libbz2.so.1.0.4
b6925000-b6926000 rw-p 0000f000 08:03 598054     /lib/libbz2.so.1.0.4
b6926000-b6927000 r-xp 00000000 08:03 1648163    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6927000-b6928000 rw-p 00000000 08:03 1648163    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6928000-b692d000 r-xp 00000000 08:03 1647485    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b692d000-b692e000 rw-p 00005000 08:03 1647485    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b692f000-b698f000 rw-s 00000000 00:09 8323113    /SYSV00000000 (deleted)
b698f000-b6a3a000 r--p 00000000 08:03 1861980    /usr/share/icons/Tangerine/icon-theme.cache
b6a3a000-b6a3c000 r-xp 00000000 08:03 1696765    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6a3c000-b6a3d000 rw-p 00001000 08:03 1696765    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6a3d000-b6ace000 r--p 00000000 08:03 1770910    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6ace000-b6ad4000 r--s 00000000 08:03 674037     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6ad4000-b6ad7000 r--s 00000000 08:03 673988     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6ad7000-b6ad8000 r--s 00000000 08:03 673986     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6ad8000-b6ad9000 r--s 00000000 08:03 673818     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6ad9000-b6adc000 r--s 00000000 08:03 673815     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6adc000-b6ae3000 r--s 00000000 08:03 673810     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6ae3000-b6aeb000 r--s 00000000 08:03 673802     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6aeb000-b6af3000 r--s 00000000 08:03 673801  Aborted



however I really believe the error is this:
> <Data><PSM>~ ~ ~  ~ (L)spam</PSM><CurrentMedia></CurrentMedia><MachineGuid></MachineGuid></Data>
*** glibc detected *** python: double free or corruption (!prev): 0x08db6398 ***

my personal message was the only thing I changed, it was all written with Chinese and Arabian characters between the ~ ~ ~ 
:P

however I can't find any way of deleting it. 
:P

please help me!

---

### Post by balta on 2008-12-10
the folder ~/.config/emesene1.0 holds your personal data, you can freely edit it offline

~/.config/emesene1.0/your_mail/PersonalMessage.conf holds personal message as text file this way: pm=this is your personal message

---

