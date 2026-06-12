---
title: "x11vnc keeps repainting after Lucid upgrade"
date: 2010-05-06
forum: Desktop Environments
---

### Post by dargaud on 2010-05-06
Hello all,
I've had a [whole bunch of problems]("http://ubuntuforums.org/showpost.php?p=9247285&postcount=580") since I upgraded to Lucid yesterday. All of them solved, except this one: when I connect to my kubuntu PC from a Windows PC and launch x11vnc on the remote and TightVNC on the local, it keeps repainting the window making it unusable. Nothing gets printed to the log when the repaintings occur.
Using -noxdamage or -nowf doesn't change a thing. -ncache doesn't work (I get an "ERROR: No active KDE sessions!"). Is this a compositing/compiz/beryl problem ?

Here's the log (it goes through an ssh tunnel):

```
user@remote $ x11vnc -auth guess -find -localhost -once -nopw &
06/05/2010 11:09:54 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 4027
06/05/2010 11:09:54
06/05/2010 11:09:54 wait_for_client: WAIT:cmd=FINDDISPLAY
06/05/2010 11:09:54
06/05/2010 11:09:54 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
06/05/2010 11:09:54
06/05/2010 11:09:54 Autoprobing TCP port
06/05/2010 11:09:54 Autoprobing selected port 5900
06/05/2010 11:09:54

The VNC desktop is:      remote:0
PORT=5900
06/05/2010 11:10:07 Got connection from client 127.0.0.1
06/05/2010 11:10:07   other clients:
06/05/2010 11:10:07 check_access: client 127.0.0.1 matches host 127.0.0.1
06/05/2010 11:10:07 incr accepted_client=1 for 127.0.0.1:38719  sock=4
06/05/2010 11:10:07 wait_for_client: got client
06/05/2010 11:10:07 client progressed=0 in 15/10 0.009935 s
06/05/2010 11:10:07 client_set_net: 127.0.0.1  0.0006
06/05/2010 11:10:07 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/s
h /tmp/x11vnc-find_display.ZV1OS9
06/05/2010 11:10:08 running: chvt 7 >/dev/null 2>/dev/null &
06/05/2010 11:10:10 -auth guess: using default XAUTHORITY for display=':0'
06/05/2010 11:10:10 Using X display :0
06/05/2010 11:10:10 rootwin: 0x15a reswin: 0x6c00001 dpy: 0x16669b0
06/05/2010 11:10:10
06/05/2010 11:10:10 ------------------ USEFUL INFORMATION ------------------
06/05/2010 11:10:10 X DAMAGE available on display, using it for polling hints.
06/05/2010 11:10:10   To disable this behavior use: '-noxdamage'
06/05/2010 11:10:10
06/05/2010 11:10:10   Most compositing window managers like 'compiz' or 'beryl'
06/05/2010 11:10:10   cause X DAMAGE to fail, and so you may not see any screen
06/05/2010 11:10:10   updates via VNC.  Either disable 'compiz' (recommended) or

06/05/2010 11:10:10   supply the x11vnc '-noxdamage' command line option.
06/05/2010 11:10:10
06/05/2010 11:10:10 Wireframing: -wireframe mode is in effect for window moves.
06/05/2010 11:10:10   If this yields undesired behavior (poor response, painting

06/05/2010 11:10:10   errors, etc) it may be disabled:
06/05/2010 11:10:10    - use '-nowf' to disable wireframing completely.
06/05/2010 11:10:10    - use '-nowcr' to disable the Copy Rectangle after the
06/05/2010 11:10:10      moved window is released in the new position.
06/05/2010 11:10:10   Also see the -help entry for tuning parameters.
06/05/2010 11:10:10   You can press 3 Alt_L's (Left "Alt" key) in a row to
06/05/2010 11:10:10   repaint the screen, also see the -fixscreen option for
06/05/2010 11:10:10   periodic repaints.
06/05/2010 11:10:10
06/05/2010 11:10:10 XFIXES available on display, resetting cursor mode
06/05/2010 11:10:10   to: '-cursor most'.
06/05/2010 11:10:10   to disable this behavior use: '-cursor arrow'
06/05/2010 11:10:10   or '-noxfixes'.
06/05/2010 11:10:10 using XFIXES for cursor drawing.
06/05/2010 11:10:10 GrabServer control via XTEST.
06/05/2010 11:10:10
06/05/2010 11:10:10 Scroll Detection: -scrollcopyrect mode is in effect to
06/05/2010 11:10:10   use RECORD extension to try to detect scrolling windows
06/05/2010 11:10:10   (induced by either user keystroke or mouse input).
06/05/2010 11:10:10   If this yields undesired behavior (poor response, painting

06/05/2010 11:10:10   errors, etc) it may be disabled via: '-noscr'
06/05/2010 11:10:10   Also see the -help entry for tuning parameters.
06/05/2010 11:10:10   You can press 3 Alt_L's (Left "Alt" key) in a row to
06/05/2010 11:10:10   repaint the screen, also see the -fixscreen option for
06/05/2010 11:10:10   periodic repaints.
06/05/2010 11:10:10
06/05/2010 11:10:10 XKEYBOARD: number of keysyms per keycode 16 is greater
06/05/2010 11:10:10   than 4 and 865 keysyms are mapped above 4.
06/05/2010 11:10:10   Automatically switching to -xkb mode.
06/05/2010 11:10:10   If this makes the key mapping worse you can
06/05/2010 11:10:10   disable it with the "-noxkb" option.
06/05/2010 11:10:10   Also, remember "-remap DEAD" for accenting characters.
06/05/2010 11:10:10 X FBPM extension not supported.
06/05/2010 11:10:10 X display is capable of DPMS.
06/05/2010 11:10:10 --------------------------------------------------------
06/05/2010 11:10:10
06/05/2010 11:10:10 Default visual ID: 0x21
06/05/2010 11:10:10 Read initial data from X display into framebuffer.
06/05/2010 11:10:10 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/7680
06/05/2010 11:10:10 rfbNewFramebuffer(0x1656b50, 0x0, 1920, 1200, 8, 1, 4)
06/05/2010 11:10:10 Pixel format for client 127.0.0.1:
06/05/2010 11:10:10   32 bpp, depth 24, little endian
06/05/2010 11:10:10   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/05/2010 11:10:10
06/05/2010 11:10:10 X display :0.0 is 32bpp depth=24 true color
06/05/2010 11:10:10
06/05/2010 11:10:10 calling setTranslateFunction()...
06/05/2010 11:10:10 Pixel format for client 127.0.0.1:
06/05/2010 11:10:10   32 bpp, depth 24, little endian
06/05/2010 11:10:10   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/05/2010 11:10:10 no translation needed
06/05/2010 11:10:10   done.
06/05/2010 11:10:10 TS_REDIR is empty, restarting...
06/05/2010 11:10:10
06/05/2010 11:10:10 Xinerama is present and active (e.g. multi-head).
06/05/2010 11:10:10 fb read rate: 555 MB/sec
06/05/2010 11:10:10 fast read: reset wait  ms to: 10
06/05/2010 11:10:10 fast read: reset defer ms to: 10
06/05/2010 11:10:10 The X server says there are 24 mouse buttons.
06/05/2010 11:10:10 screen setup finished.
06/05/2010 11:10:10

The VNC desktop is:      localhost:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching

06/05/2010 11:10:10 Client Protocol Version 3.8
06/05/2010 11:10:10 Protocol version sent 3.8, using 3.8
06/05/2010 11:10:11 Battling with something for -norepeat!! (1 resets left)
06/05/2010 11:10:11 Disabled X server key autorepeat.
06/05/2010 11:10:11   to force back on run: 'xset r on' (2 times)
06/05/2010 11:10:11 created   xdamage object: 0x6c00040
06/05/2010 11:10:11 rfbProcessClientSecurityType: executing handler for type 1
06/05/2010 11:10:11 rfbProcessClientSecurityType: returning securityResult for c
lient rfb version >= 3.8
06/05/2010 11:10:11 Pixel format for client 127.0.0.1:
06/05/2010 11:10:11   32 bpp, depth 24, little endian
06/05/2010 11:10:11   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/05/2010 11:10:11 no translation needed
06/05/2010 11:10:11 rfbProcessClientNormalMessage: ignoring unsupported encoding
 type zlibhex
06/05/2010 11:10:11 Enabling X-style cursor updates for client 127.0.0.1
06/05/2010 11:10:11 Enabling full-color cursor updates for client 127.0.0.1
06/05/2010 11:10:11 Enabling cursor position updates for client 127.0.0.1
06/05/2010 11:10:11 Using image quality level 6 for client 127.0.0.1
06/05/2010 11:10:11 Enabling LastRect protocol extension for client 127.0.0.1
06/05/2010 11:10:11 Enabling NewFBSize protocol extension for client 127.0.0.1
06/05/2010 11:10:11 Using tight encoding for client 127.0.0.1
06/05/2010 11:10:17 created selwin: 0x6c00041
06/05/2010 11:10:17 called initialize_xfixes()
06/05/2010 11:10:18 copy_tiles: allocating first_line at size 61
06/05/2010 11:10:19 client 1 network rate 38.0 KB/sec (1095.5 eff KB/sec)
06/05/2010 11:10:19 client 1 latency:  49.8 ms
06/05/2010 11:10:19 dt1: 0.0114, dt2: 0.2819 dt3: 0.0498 bytes: 10203
06/05/2010 11:10:19 link_rate: LR_BROADBAND - 49 ms, 38 KB/s
06/05/2010 11:10:51 client_count: 0
06/05/2010 11:10:51 Restored X server key autorepeat to: 1
06/05/2010 11:10:51 viewer exited.
06/05/2010 11:10:51 deleted 60 tile_row polling images.
```

---

### Post by krunge on 2010-05-06
Could you explain more what you mean by 'repainting'?  What does it look like between repaints? Is it just for a single window or the whole screen?  Are you providing any mouse or keyboard input during this period?

Maybe add these to your command line:
```
x11vnc -auth guess -find -localhost -once -nopw -nowf -noscr -noxdamage
```
(I realize you mentioned you already tried some of those, but the above should be a good starting baseline for troubleshooting.)

Another possibility is the screensaver, KDE had that problem before:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-kde-screensaver](http://www.karlrunge.com/x11vnc/faq.html#faq-kde-screensaver)[/INDENT]
I thought that was fixed some time ago, but these desktop problems often have a tendency of reappearing...

---

### Post by dargaud on 2010-05-06
It goes entirely black and then starts repainting from the top. You were right about the screensaver thing, using -nodpms fixed the issue, thanks.

---

### Post by krunge on 2010-05-06
> **dargaud said:**
> It goes entirely black and then starts repainting from the top. You were right about the screensaver thing, using -nodpms fixed the issue, thanks.
Ugh. Did you not have this problem recently in KDE?  The KDE screensaver problem first appeared in 2006. I'm wondering if it has been there all along or if it has reappeared.

Could you indicate the KDE version(s) the problem did not occur for you and the KDE version for which it did appear?

---

### Post by dargaud on 2010-05-06
I did not have this problem in the previous kubuntu version, and I use x11vnc daily. It appeared with the upgrade to Lurid Lynx yesterday. KDE is now 4.4.2 but I don't know what the previous version was.

---

### Post by Zorael on 2010-05-06
This happens to me when I connect to my laptop when it has its lid closed.

To work around it I had to go into the Power Management settings for my power profile, and set it to *When laptop lid closed: Do nothing*.

---

### Post by krunge on 2010-05-06
> I did not have this problem in the previous kubuntu version, and I use x11vnc daily. It appeared with the upgrade to Lurid Lynx yesterday. KDE is now 4.4.2 but I don't know what the previous version was.
What was the most recent ubuntu version where you did not see the problem?

---

