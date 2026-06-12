---
title: "Is Compiz Fusion broken for anyone else? Broke two updates ago..."
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-09-18
I updated CF two days ago, after which it wouldn't start. I use the following script to switch between Metacity and CF:
> #!/bin/sh

# click to start, click to stop

if pidof compiz.real
then
 exec metacity --replace
else
 exec compiz --replace -c emerald

fi
I ran "compiz --replace" in a terminal to see if there were errors, and it gave me a REALLY long...thing? It's a bunch of stuff that I don't understand, but a lot is repeated:
> riley@Riley:~$ compiz --replace
A handler is already registered for the path starting with path[0] = "org"

**That line is repeated at least 80 or 85 times**

inotify_add_watch: No such file or directory
GConf backend: There is an unsupported value at path /apps/compiz/plugins/water/allscreens/options/toggle_wiper_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/unfold_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/next_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/prev_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 9011

**Lots of loading and reading of things here**

[Thread debugging using libthread_db enabled]
[New Thread -1213770048 (LWP 9011)]

**Lots more reading/loading of things here, and the only thing that didn't fit was this next part**

Reading symbols froUndefined command: "-e".  Try "help".
m /usr/lib/compiz/libtext.so...done.
Loaded symbols for /usr/lib/compiz/libtext.so

**A bit more reading/loading**

0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1213770048 (LWP 9011)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c546a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7bfba3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb544bcfc in crash_handler (sig=11) at crashhandler.c:59
        count = 1
#4  <signal handler called>
#5  0x08052c49 in allocatePrivateIndex (len=0x80799a0, indices=0x807999c, 
    reallocProc=0x805ae00 <reallocScreenPrivate>, closure=0x8079980)
    at privates.c:41
        i = 0
#6  0x0805da07 in allocScreenObjectPrivateIndex (parent=0x8079980)
    at screen.c:76
No locals.
#7  0x0805d949 in allocateScreenPrivateIndex (display=0x8079980)
    at screen.c:148
No locals.
#8  0xb5220b69 in screenSaverInitDisplay (p=0x86b5bb8, d=0x8079980)
    at screensaver.cpp:351
        sd = (ScreenSaverDisplay *) 0x86f1d60
#9  0xb521fe49 in screenSaverInitObject (p=0x86b5bb8, o=0x8079980)
    at screensaver.cpp:397
        dispTab = {0xb5220b0c <screenSaverInitDisplay>, 
  0xb52204de <screenSaverInitScreen>, 0xb522036e <screenSaverInitWindow>}
#10 0xb5228a8b in screensaverOptionsInitObjectWrapper (p=0x86b5bb8, 
    o=0x8079980) at build/screensaver_options.c:641
        rv = 1
#11 0x0806f54d in initObjectTree (object=0x8079980, closure=0xbf872acc)
    at plugin.c:369
        p = (CompPlugin *) 0x86b5bb8
        ctx = {plugin = 0x0, type = 4294967295}
#12 0x0806f7b4 in pushPlugin (p=0x86b5bb8) at plugin.c:444
        ctx = {plugin = 0x86b5bb8, object = 0x8079980}
#13 0x080585ee in eventLoop () at display.c:1017
        event = {type = 117, xany = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, window = 14680106}, xkey = {
    type = 117, serial = 3298, send_event = 0, display = 0x8085a10, 
    window = 14680106, root = 56623214, subwindow = 0, time = 0, x = 2800261, 
    y = 10, x_root = 1573258, y_root = 77070336, state = 1574784, keycode = 0, 
    same_screen = 0}, xbutton = {type = 117, serial = 3298, send_event = 0, 
    display = 0x8085a10, window = 14680106, root = 56623214, subwindow = 0, 
    time = 0, x = 2800261, y = 10, x_root = 1573258, y_root = 77070336, 
    state = 1574784, button = 0, same_screen = 0}, xmotion = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    root = 56623214, subwindow = 0, time = 0, x = 2800261, y = 10, 
    x_root = 1573258, y_root = 77070336, state = 1574784, is_hint = 0 '\0', 
    same_screen = 0}, xcrossing = {type = 117, serial = 3298, send_event = 0, 
    display = 0x8085a10, window = 14680106, root = 56623214, subwindow = 0, 
    time = 0, x = 2800261, y = 10, x_root = 1573258, y_root = 77070336, 
    mode = 1574784, detail = 0, same_screen = 0, focus = 0, state = 0}, 
  xfocus = {type = 117, serial = 3298, send_event = 0, display = 0x8085a10, 
    window = 14680106, mode = 56623214, detail = 0}, xexpose = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    x = 56623214, y = 0, width = 0, height = 2800261, count = 10}, 
  xgraphicsexpose = {type = 117, serial = 3298, send_event = 0, 
    display = 0x8085a10, drawable = 14680106, x = 56623214, y = 0, width = 0, 
    height = 2800261, count = 10, major_code = 1573258, 
    minor_code = 77070336}, xnoexpose = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, drawable = 14680106, 
    major_code = 56623214, minor_code = 0}, xvisibility = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    state = 56623214}, xcreatewindow = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, parent = 14680106, window = 56623214, 
    x = 0, y = 0, width = 2800261, height = 10, border_width = 1573258, 
    override_redirect = 77070336}, xdestroywindow = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, event = 14680106, 
    window = 56623214}, xunmap = {type = 117, serial = 3298, send_event = 0, 
    display = 0x8085a10, event = 14680106, window = 56623214, 
    from_configure = 0}, xmap = {type = 117, serial = 3298, send_event = 0, 
    display = 0x8085a10, event = 14680106, window = 56623214, 
    override_redirect = 0}, xmaprequest = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, parent = 14680106, 
    window = 56623214}, xreparent = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, event = 14680106, window = 56623214, 
    parent = 0, x = 0, y = 2800261, override_redirect = 10}, xconfigure = {
    type = 117, serial = 3298, send_event = 0, display = 0x8085a10, 
    event = 14680106, window = 56623214, x = 0, y = 0, width = 2800261, 
    height = 10, border_width = 1573258, above = 77070336, 
    override_redirect = 1574784}, xgravity = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, event = 14680106, window = 56623214, 
    x = 0, y = 0}, xresizerequest = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, window = 14680106, width = 56623214, 
    height = 0}, xconfigurerequest = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, parent = 14680106, window = 56623214, 
    x = 0, y = 0, width = 2800261, height = 10, border_width = 1573258, 
    above = 77070336, detail = 1574784, value_mask = 0}, xcirculate = {
    type = 117, serial = 3298, send_event = 0, display = 0x8085a10, 
    event = 14680106, window = 56623214, place = 0}, xcirculaterequest = {
    type = 117, serial = 3298, send_event = 0, display = 0x8085a10, 
    parent = 14680106, window = 56623214, place = 0}, xproperty = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    atom = 56623214, time = 0, state = 0}, xselectionclear = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    selection = 56623214, time = 0}, xselectionrequest = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, owner = 14680106, 
    requestor = 56623214, selection = 0, target = 0, property = 2800261, 
    time = 10}, xselection = {type = 117, serial = 3298, send_event = 0, 
    display = 0x8085a10, requestor = 14680106, selection = 56623214, 
    target = 0, property = 0, time = 2800261}, xcolormap = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    colormap = 56623214, new = 0, state = 0}, xclient = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    message_type = 56623214, format = 0, data = {
      b = "\000\000\000\000\205&#65533;*\000\n\000\000\000\212\001\030\000\000\000\230\004", s = {0, 0, -17787, 42, 10, 0, 394, 24, 0, 1176}, l = {0, 2800261, 10, 
        1573258, 77070336}}}, xmapping = {type = 117, serial = 3298, 
    send_event = 0, display = 0x8085a10, window = 14680106, 
    request = 56623214, first_keycode = 0, count = 0}, xerror = {type = 117, 
    display = 0xce2, resourceid = 0, serial = 134765072, error_code = 42 '*', 
    request_code = 0 '\0', minor_code = 224 '&#65533;'}, xkeymap = {type = 117, 
    serial = 3298, send_event = 0, display = 0x8085a10, window = 14680106, 
    key_vector = "n\000`\003\000\000\000\000\000\000\000\000\205&#65533;*\000\n\000\000\000\212\001\030\000\000\000\230\004\200\a\030"}, pad = {117, 3298, 0, 
    134765072, 14680106, 56623214, 0, 0, 2800261, 10, 1573258, 77070336, 
    1574784, 0 <repeats 11 times>}}
        timeDiff = <value optimized out>
        tv = {tv_sec = 1190155093, tv_usec = 29374}
        d = (CompDisplay *) 0x86eb5e0
        s = (CompScreen *) 0x86eb5e0
        w = <value optimized out>
        time = <value optimized out>
        timeToNextRedraw = 0
        damageMask = 4
        mask = <value optimized out>
#14 0x08052803 in main (argc=5, argv=0xbf8730b4) at main.c:461
        size = 1
        ctx = {offset = 3960, pluginData = 0x807a008 "\003", 
  textureFilterData = 0x0, refreshRateData = 0x0}
        displayName = 0x0
        plugin = {0xbf8749c6 "ccp", 0xb7a8a25c "trstr", 0xb7a8a25f "tr", 0x0, 
  0x0, 0x1 <Address 0x1 out of bounds>, 0x364 <Address 0x364 out of bounds>, 
  0xb7a76ae0 "&#563;&#65533;&#65533;\020ii\r", 0xb7ebcd58 "", 0xb7a8a25b "strstr", 
  0xb7bd17a8 "", 0xb7a89078 "&#65533;", 0x1 <Address 0x1 out of bounds>, 
  0xb7f55ff4 "(\237\001", 0xb7aa4468 "<h&#65533;&#65533;", 0xbf872ce8 "h¼&#65533;X&#65533;&#65533;&#65533;", 
  0xbf872d04 "@-\207&#65533;R\216&#65533;&#65533;hD&#65533;&#65533;&#65533;j&#65533;&#65533;\001", 0xb7f45103 "\203&#65533;", 0xb7a89078 "&#65533;", 
  0xbf872ce8 "h¼&#65533;X&#65533;&#65533;&#65533;", 0xb7f5683c "h:\031\b#", 0x0, 
  0xb7a76ae0 "&#563;&#65533;&#65533;\020ii\r", 0x1 <Address 0x1 out of bounds>, 0x0, 
  0x1 <Address 0x1 out of bounds>, 0xbf872c7c "\001", 
  0xb7f4bfa8 "\205&#65533;t\027\2118\203&#65533;\b\211F\004\211&#65533;\213]&#65533;\213u&#65533;\213}&#65533;\211&#65533;]&#65533;1&#65533;&#65533;&#65533;\211&#65533;\215&#65533;'", 0x11 <Address 0x11 out of bounds>, 
  0x8 <Address 0x8 out of bounds>, 0xb7f3c468 "", 
  0xbf872cf4 "&#65533;\232&#65533;\a&#65533;_&#65533;&#65533;&#65533;B&#65533;&#65533;x\220&#65533;&#65533;@-\207&#65533;R\216&#65533;&#65533;hD&#65533;&#65533;&#65533;j&#65533;&#65533;\001", 
  0xb7a75000 "", 0x1 <Address 0x1 out of bounds>, 0xbf872cb0 "\210", 
  0xbf872d30 "h¼&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;&#65533;t-\207&#65533;\0300\207&#65533;", 0xb7aa42b0 "", 
  0xb7a8a25b "strstr", 0x1000000 <Address 0x1000000 out of bounds>, 
  0x1c93db57 <Address 0x1c93db57 out of bounds>, 0x0, 0x0, 
  0xb7f54434 "_dl_allocate_tls_init", 0x0, 0xb7f54434 "_dl_allocate_tls_init", 
  0xb7f3c700 "l\236\001", 0x88 <Address 0x88 out of bounds>, 0x0, 0x0, 0x0, 
  0xb7a8c300 "U\211&#65533;\203&#65533;\024\211]&#65533;\213M\f\211u&#65533;\211}&#65533;&#65533;C&#65533;&#65533;&#65533;\201&#65533;&#65533;
  0x10000004 <Address 0x10000004 out of bounds>, 
  0xb7f27000 "\177ELF\001\001\001", 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0xb7bcc268 "\030G", 0xb7ebcd58 "", 0x0, 
  0x7ab9ab2 <Address 0x7ab9ab2 out of bounds>, 0xb7f55ff4 "(\237\001", 
  0xb7aa42b0 "", 0xb7a89078 "&#65533;", 0xbf872d40 "\0300\207&#65533;", 
  0xb7f48e52 "\213U&#65533;\203&#65533;\024\211&#65533;1&#65533;\205&#65533;t\t\205&#65533;t\002\213\001\003B\004\213\213\030&#65533;&#65533;&#65533;\205&#65533;u\t\213M&#65533;\213U&#65533;\211\004\021\215e&#65533;[^_]&#65533;1&#65533;&#65533;\223\215\203&#65533;&#65533;&#65533;&#65533;\211D$\f\215\203&#65533;&#65533;&#65533;&#65533;\211D$\004\215\203&#65533;&#65533;&#65533;&#65533;&#65533;D$\bM", 0xb7aa4468 "<h&#65533;&#65533;", 
  0xb7a76ae0 "&#563;&#65533;&#65533;\020ii\r", 0x1 <Address 0x1 out of bounds>, 
  0x1 <Address 0x1 out of bounds>, 0x0, 0xb7a8a25b "strstr", 
  0x34 <Address 0x34 out of bounds>, 0xb7a88000 "\177ELF\001\001\001", 
  0x140b8 <Address 0x140b8 out of bounds>, 0xb7bcc268 "\030G", 
  0xb7a9bff4 "&#65533;>\001", 0xb7a756bc "", 0xbf872d74 "Linux", 
  0xbf873018 "\2100\207&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;\\&#65533;&#65533;&#65533;V\a\b\2100\207&#65533;&#65533;&#65533;&#65533;&#65533;\005", 
  0xb7f4e300 "ZY\207\004$&#65533;\b", 0xbf872e37 "#2 Fri Aug 31 00:51:58 UTC 2007", 
  0x0, 0xb7a756bc "", 0xbf872d74 "Linux", 
  0xbf873018 "\2100\207&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;\\&#65533;&#65533;&#65533;V\a\b\2100\207&#65533;&#65533;&#65533;&#65533;&#65533;\005", 
  0xb7a8c77a "\205&#65533;\017\225&#65533;\017&#65533;&#65533;\211\203&#65533;!", 
  0xbf872e37 "#2 Fri Aug 31 00:51:58 UTC 2007", 0xb7a972b9 "SMP", 0x0, 0x0, 
  0xbf872f78 "<h&#65533;&#65533;", 0x756e694c <Address 0x756e694c out of bounds>, 
  0x78 <Address 0x78 out of bounds>, 0x0 <repeats 14 times>, 
  0x6c695200 <Address 0x6c695200 out of bounds>, 
  0x7965 <Address 0x7965 out of bounds>, 0x0 <repeats 14 times>, 
  0x2e320000 <Address 0x2e320000 out of bounds>, 
  0x30322e36 <Address 0x30322e36 out of bounds>, 
  0x2d36312d <Address 0x2d36312d out of bounds>, 
  0x363833 <Address 0x363833 out of bounds>, 0x0 <repeats 12 times>, 
  0x23000000 <Address 0x23000000 out of bounds>, 
  0x72462032 <Address 0x72462032 out of bounds>, 
  0x75412069 <Address 0x75412069 out of bounds>, 
  0x31332067 <Address 0x31332067 out of bounds>, 
  0x3a303020 <Address 0x3a303020 out of bounds>, 
  0x353a3135 <Address 0x353a3135 out of bounds>, 
  0x54552038 <Address 0x54552038 out of bounds>, 
  0x30322043 <Address 0x30322043 out of bounds>, 
  0x3730 <Address 0x3730 out of bounds>, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0x0, 0x36383669 <Address 0x36383669 out of bounds>, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0x0, 0x0, 0x0, 0x0, 0x804fd1c "GLIBC_2.1", 
  0xd696910 <Address 0xd696910 out of bounds>, 0xb7bd0fa8 "&#65533;*", 
  0xbf872ee4 "h/\207&#65533;BO&#65533;&#65533;", 
  0xb7f44b79 "\205&#65533;\017\204r&#65533;&#65533;&#65533;\213E&#65533;\213@\b\205&#65533;\017\205b&#65533;&#65533;&#65533;\205&#65533;\017\205Z&#65533;&#65533;&#65533;f\203}&#65533;", 0xb7bd6cd4 "GLIBC_2.0", 0x804fd12 "GLIBC_2.0", 
  0xb7ebcd0c "cursor.so.1", 0xb7ebccfc "\b&#65533;&#65533;&#65533;", 
  0xb7a76020 "\022&#65533;\004\b\020ii\r", 0xbf870002 "", 
  0xb7f49c69 "\205&#65533;u&#65533;\203&#65533;\b&#65533;\001", 0x804d89d "libc.so.6", 
  0xb7ebcd08 "libXcursor.so.1", 0xb7f55ff4 "(\237\001", 0xb7aa4fa4 "X&#65533;&#65533;&#65533;", 
  0xe <Address 0xe out of bounds>, 
  0xbf872f68 "40\207&#65533;\003Q&#65533;&#65533;L&#65533;\004\b\0300\207&#65533;<h&#65533;&#65533;", 
  0xb7f44f42 "\205&#65533;t&#65533;&#65533;\235&#65533;&#65533;&#65533;\220\215t&", 0x0, 0x0, 0x0, 0x0, 
  0x123 <Address 0x123 out of bounds>, 
  0x3d8f5 <Address 0x3d8f5 out of bounds>, 0xbf872f34 "", 0xbf872f34 "", 
  0xbf873024 "&#65533;V\a\b\2100\207&#65533;&#65533;&#65533;&#65533;&#65533;\005", 
  0xf63d4e2e <Address 0xf63d4e2e out of bounds>, 0xb7ebcd58 "", 
  0x1a <Address 0x1a out of bounds>, 0xb7bc8c28 "", 
  0xb7bc8a28 "/N=&#65533;&#65533;\030L\017&#65533;&#65533;-&#65533;\204\"\233|&#65533;&#65533;\217&#65533;\205\"\233|&#65533;&#65533;&#65533;=&#65533;\"\225&#65533;8&#65533;\031u&#65533;\001&#65533;\022&#65533;BY\020&#65533;&#65533;&#52598;w\035\rG&#65533;&#65533;%&#65533;V1&#65533;&#65533;r1\035\a;&#65533;L\214\t)\020\t~\222\0348&#65533;&#65533;0j&#65533;&#65533;{\004\\H&#65533;&#1313;\034&#65533;\002&#65533;&#65533;\0179&#65533;&#65533;0X?\227|\030\034s&#65533;T\200&#65533;s&#65533;\202c\002;H\205\0336\rf&#65533;2v&#65533;&#1384;&#65533;K&#65533;&#65533;\234#\217&#65533;\036h\233&#65533;\230&#65533;&#65533;\234\002Y1\n&#65533;\006&#2045;&#65533;e\235J\032\223&#65533;P&#65533;&#65533;\020\205)%~\016|\030&#65533;&#65533;8\a\221\222&#65533;\206&#65533;&#65533;:V&#65533;&#65533;I&#65533;$\202&#65533;7&#65533;Qho&#65533;&#65533;&#65533;\017l"..., 
  0x804da6d "__libc_start_main", 
  0xf63d4e2e <Address 0xf63d4e2e out of bounds>, 0x804da79 "_main", 
  0x804da71 "bc_start_main", 0x0, 0x0, 0x1 <Address 0x1 out of bounds>...}
        i = <value optimized out>
        nPlugin = 1
        disableSm = 1
        clientId = 0x0
        refreshRateArg = 0x0
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c546a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7bfba3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb544bcfc in crash_handler (sig=11) at crashhandler.c:59
#4  <signal handler called>
#5  0x08052c49 in allocatePrivateIndex (len=0x80799a0, indices=0x807999c, 
    reallocProc=0x805ae00 <reallocScreenPrivate>, closure=0x8079980)
    at privates.c:41
#6  0x0805da07 in allocScreenObjectPrivateIndex (parent=0x8079980)
    at screen.c:76
#7  0x0805d949 in allocateScreenPrivateIndex (display=0x8079980)
    at screen.c:148
#8  0xb5220b69 in screenSaverInitDisplay (p=0x86b5bb8, d=0x8079980)
    at screensaver.cpp:351
#9  0xb521fe49 in screenSaverInitObject (p=0x86b5bb8, o=0x8079980)
    at screensaver.cpp:397
#10 0xb5228a8b in screensaverOptionsInitObjectWrapper (p=0x86b5bb8, 
    o=0x8079980) at build/screensaver_options.c:641
#11 0x0806f54d in initObjectTree (object=0x8079980, closure=0xbf872acc)
    at plugin.c:369
#12 0x0806f7b4 in pushPlugin (p=0x86b5bb8) at plugin.c:444
#13 0x080585ee in eventLoop () at display.c:1017
#14 0x08052803 in main (argc=5, argv=0xbf8730b4) at main.c:461
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 9011

[CRASH_HANDLER]: "/tmp/compiz_crash-9011.out" created!

Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"

I noticed that last line (well, second to last) that talked about the crash, and it looks like that file that was created is the same thing it said in the terminal but I'm not sure if it's identical. Let me know if I should post it.

---

### Post by hyperair on 2007-09-19
Oh it definitely crashed alright. What are you using to update?

---

### Post by orange2k on 2007-09-19
Well, I installed the 0.5.2 version a few weeks ago, and **removed** the repository I installed it from - exactly for this reason - I dont want to update until a new (relativly) stable release comes out...

Maybe you should try that. This is the guide I used to completely remove my old C-F and install the new one: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

