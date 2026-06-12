---
title: "Google Earth - Help!"
date: 2008-12-04
forum: Desktop Environments
---

### Post by smirnoff76 on 2008-12-04
Hey Guys, 

When I open Google earth it appears on screen for a few seconds then closes unexpectedly? 

When I have launched GE from CLI the text below appears, can anyone help?

Thanks!!

Warning, xpress200 detected.
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 471
Software fallback:ctx->Line.SmoothFlag
***************************************************************************
googleearth-bin: r300_emit.c:403: r300EmitArrays: Assertion `((inputs_bitset)[((_TNL_ATTRIB_COLOR0) / (sizeof (GLuint) * 8))] & (1 << ((_TNL_ATTRIB_COLOR0) % (sizeof (GLuint) * 8))))' failed.
Google Earth has caught signal 6.

Stacktrace from glibc:
  ./googleearth-bin [0x804f403]
  ./googleearth-bin [0x804f916]
  [0xb7f26420]
  /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb70d0a01]
  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb70c810e]
  /usr/lib/dri/r300_dri.so(r300EmitArrays+0x126d) [0xae5ea51d]
  /usr/lib/dri/r300_dri.so [0xae5dc901]
  /usr/lib/dri/r300_dri.so [0xae5dd6bb]
  /usr/lib/dri/r300_dri.so(_tnl_run_pipeline+0x153) [0xae670f33]
  /usr/lib/dri/r300_dri.so(_tnl_draw_prims+0x431) [0xae6714b1]
  /usr/lib/dri/r300_dri.so [0xae669d9c]
  /home/karl/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext11genericDrawEiiiii+0x575) [0xb3e2cc25]
  /home/karl/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext12drawMultipleENS0_20IG_GFX_DRAW_MULTIPLEEiii+0xeb) [0xb3e4678b]
  ./libIGAttrs.so(_ZN3Gap5Attrs17igGeometryAttr1_55applyEPNS_3Gfx15igVisualContextE+0xc5) [0xb3884b25]
  ./libIGAttrs.so(_ZN3Gap5Attrs17igDisplayListAttr5applyEPNS_3Gfx15igVisualContextE+0x48) [0xb3881448]
  ./libIGAttrs.so(_ZN3Gap5Attrs17igDisplayListAttr5applyEPNS_3Gfx15igVisualContextE+0x2f) [0xb388142f]
  /home/karl/google-earth/libevll.so(_ZN5earth4evll17SceneGraphManager14drawSceneGraphEPN3Gap5Attrs17igDisplayListAttrES5_+0x39) [0xb3ba0c59]
  /home/karl/google-earth/libevll.so(_ZN5earth4evll17SceneGraphManager4drawEv+0xce) [0xb3ba2e7e]
  /home/karl/google-earth/libevll.so(_ZN5earth4evll13VisualContext6renderEb+0xae4) [0xb3a1ae54]
  /home/karl/google-earth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0x1c4) [0xb3a1d734]
  /home/karl/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0x166) [0xb3bba2f6]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x2a) [0xb67aeb6a]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x1a) [0xb67bbfba]
  ./libbase.so(_ZN5earth5Timer8dispatchEv+0x2d) [0xb707003d]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application18CommandCustomEvent8dispatchEv+0x23) [0xb728f483]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application11customEventEP6QEvent+0x3a) [0xb7280e4a]
  ./libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0xed) [0xb7d629a1]
  ./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0x1d3) [0xb775b4ab]
  ./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xb4) [0xb7762020]
  ./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x62) [0xb7d54eda]
  ./libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x247) [0xb7d569db]
  ./libQtCore.so.4(_ZN16QCoreApplication16sendPostedEventsEP7QObjecti+0x23) [0xb7d56c4f]
  ./libQtCore.so.4 [0xb7d74a9a]
  /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x176) [0xb6bf7cc6]
  /usr/lib/libglib-2.0.so.0 [0xb6bfb083]
  /usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x6e) [0xb6bfb63e]
  ./libQtCore.so.4(_ZN20QEventDispatcherGlib13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x53) [0xb7d7461b]
  ./libQtGui.so.4 [0xb77c9cf2]
  ./libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x2d) [0xb7d54861]
  ./libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xc7) [0xb7d54a07]
  ./libQtCore.so.4(_ZN16QCoreApplication4execEv+0x98) [0xb7d56cf0]
  ./libQtGui.so.4(_ZN12QApplication4execEv+0x25) [0xb775af75]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x380) [0xb728d570]
  ./googleearth-bin(main+0x2ba) [0x8050bea]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70ba450]
  ./googleearth-bin [0x804f231]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/karl/.googleearth/crashlogs/crashlog-FF95045F.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

---

### Post by itix on 2008-12-05
Well, the output clearly says it's a bug within Google Earth and that the output should be reported to them. 

There should be a lot of debug info in that file specified by the program. File that info to google and I bet they'd be happy..

---

### Post by sofasurfer on 2009-01-28
I am having the same problem along with the same message. The message says that the info will be sent to google the next time I try to run it. In the meantime, is there a way for me to fix it?

---

### Post by arvevans on 2009-01-28
This has been posted earlier under thread "Google Earth Crashes".  Apparently no fix yet available.  If you have not done so, it might help to post a bug report with Google.  Several of us have already posted bug reports there, but a few more cannot hurt.

_._

---

### Post by sofasurfer on 2009-01-29
I uninstalled it and removed any left over directories. Then I reinstalled with apt-get. It works fine UNTIL I set a bunch of place markers. Then it starts shutting down immediately after starting.

---

### Post by sofasurfer on 2009-01-30
Problem fixed!! For now anyway.

Without uninstalling my current version of google earth, which I installed with "sudo apt-get install googleearth" and which was version 4.2, I installed "sudo apt-get install googleearth-4.3".

So far it is running perfectly on my system.

---

### Post by arvevans on 2009-02-15
[I]arv@arv-desktop:~$ sudo apt-get install googleearth-4.3
[sudo] password for arv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth-4.3
arv@arv-desktop:~$ [/I]

So, that obviously does not work.

---

### Post by sofasurfer on 2009-02-17
It worked for me. But I do seem to remember that at one point it did not work. I think I needed to do sudo apt-get update and sudo apt-get upgrade. Are you sure you have the correct sources in your list?

---

### Post by dreamdigital on 2009-02-17
Yeah I am having this same problem.  Google Earth 5.0.  It starts to open, I see the "Tips" pop up then it just shuts down in flames (do to my burn graphics).  Been looking for a fix for a while.  I'm going to try and uninstall and reinstall it see what happens, so far it won't work for me.

---

