---
title: "VNC and High CPU After Use"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Sweezel on 2006-06-16
I use VNC on Ubuntu at home and my husband logs in from a Windows XP machine using a VNC client.

The only problem is, that my Ubuntu machine is really slow after he has logged off. I end up restarting X to keep Xorg from hogging resources.

Does anyone else experience this??? Is there a fix???

---

### Post by scxtt on 2006-06-16
is there a defunct process left over after he logs out? -- check your 'system monitor' (or top) and see if VNC server is still using the CPU or a client is still running [ you should just be able to kill them, no restart/logout ] ... i've never had that happen to me, but i'm the only one who uses my computer - so no one is sitting in front of it when i VNC to it ...

---

### Post by Sweezel on 2006-06-20
Xorg seems to be the only thing taking major CPU and nothing seems errant.

I would look at top next time.


Thanks

---

### Post by Sweezel on 2006-06-20
Well, it looks like vino-server was still running but did not appear to be sucking down the CPU.

After killing vino-server, everything went back to normal.

I will see if this works every time my husband logs off.


Thanks for the lead!

Staci

---

### Post by Sweezel on 2006-06-21
It worked again today!

Even though the CPU use is high in Xorg, killing vino-server corrects the slowness.

I don't trust the resource monitors due to things like this. My computer is slow so I kill a sleeping process and things get better????

---

### Post by scxtt on 2006-06-21
have him try using x11vnc instead of vino, and see if that helps ...

vino is "ok" in a pinch, but i don't like it overall ...

---

### Post by Sweezel on 2006-06-21
Do I just install a new package?

---

### Post by scxtt on 2006-06-21
yup, x11vnc ... then it can be started via:
```
x11vnc -display :0 &
```my only problem w/ it is that it prints to the window it was started from (i even tried redirecting it to a file, no luck) - but it's a minor complaint ...

---

### Post by Sweezel on 2006-06-21
What a pain in the rear!


Jeez, this is user friendly:


$ ###############################################################
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  **  WARNING  **  WARNING  **  WARNING  **  WARNING  **   @#
#@                                                           @#
#@        YOU ARE RUNNING X11VNC WITHOUT A PASSWORD!!        @#
#@                                                           @#
#@  This means anyone with network access to this computer   @#
#@  will be able to easily view and control your desktop.    @#
#@                                                           @#
#@ >>> If you did not mean to do this Press CTRL-C now!! <<< @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  You can create an x11vnc password file by running:       @#
#@                                                           @#
#@      x11vnc -storepasswd password /path/to/passfile       @#
#@                                                           @#
#@  and then starting x11vnc via:                            @#
#@                                                           @#
#@      x11vnc -rfbauth /path/to/passfile                    @#
#@                                                           @#
#@  an existing ~/.vnc/passwd file will work too.            @#
#@                                                           @#
#@  You can also use the -passwdfile or -passwd options.     @#
#@  (note -passwd is unsafe if local users are not trusted)  @#
#@                                                           @#
#@  Make sure any -rfbauth and -passwdfile password files    @#
#@  cannot be read by untrusted users.                       @#
#@                                                           @#
#@  Even with a password, the subsequent VNC traffic is      @#
#@  sent in the clear.  Consider tunnelling via ssh(1):      @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)            @#
#@                                                           @#
#@  Please Read the documention for more info about          @#
#@  passwords, security, and encryption.                     @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/#faq-passwd](http://www.karlrunge.com/x11vnc/#faq-passwd)            @#
#@                                                           @#
#@  To disable this warning use the -nopw option, or put     @#
#@  the setting in your ~/.x11vncrc file.                    @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
###############################################################

Settings:
 display:    :0
 authfile:   null
 subwin:     0x0
 -sid mode:  0
 clip:       null
 flashcmap:  0
 shiftcmap:  0
 force_idx:  0
 visual:     null
 overlay:    0
 ovl_cursor: 1
 scaling:    0 1.0000
 viewonly:   0
 shared:     0
 conn_once:  1
 timeout:    0
 inetd:      0
 http:       0
 connect:    null
 connectfile null
 vnc_conn:   1
 allow:      null
 input:      null
 passfile:   null
 accept:     null
 gone:       null
 users:      null
 using_shm:  1
 flipbytes:  0
 onetile:    0
 solid:      null
 blackout:   null
 xinerama:   0
 xtrap:      0
 xrandr:     0
 xrandrmode: null
 padgeom:    null
 logfile:    null
 logappend:  0
 flag:       null
 rc_file:    ""
 norc:       0
 dbg:        0
 bg:         0
 mod_tweak:  1
 isolevel3:  0
 xkb:        0
 skipkeys:   null
 sloppykeys: 0
 skip_dups:  0
 addkeysyms: 1
 xkbcompat:  0
 clearmods:  0
 remap:      null
 norepeat:   1
 norepeatcnt:2
 nofb:       0
 watchbell:  1
 watchsel:   1
 watchprim:  1
 seldir:     null
 cursor:     1
 multicurs:  0
 curs_mode:  null
 arrow:      1
 xfixes:     1
 alphacut:   240
 alphafrac:  0.33
 alpharemove:0
 alphablend: 1
 cursorshape:1
 cursorpos:  1
 xwarpptr:   0
 buttonmap:  null
 dragging:   1
 wireframe:  0xff,3,0,32+8+8+8,all,0.15+0.30+5.0+0.125
 wirecopy:   always
 scrollcopy: always
  scr_area:  60000
  scr_skip:  ##Soffice.bin,##StarOffice
  scr_inc:   ##Nomatch
  scr_keys:  null
  scr_term:  null
  scr_keyrep: null
  scr_parms: 0+64+32+32,0.02+0.10+0.9,0.03+0.06+0.5+0.1+5.0
 fixscreen:  null
 noxrecord:  0
 grabbuster: 0
 ptr_mode:   2
 inputskip:  10
 speeds:     null
 wmdt:       null
 debug_ptr:  0
 debug_key:  0
 defer:      30
 waitms:     30
 wait_ui:    2.00
 nowait_bog: 0
 slow_fb:    0.00
 readtimeout: 20
 take_naps:  1
 sb:         60
 xdamage:    1
  xd_area:   20000
  xd_mem:    1.000
 sigpipe:    null
 threads:    0
 fs_frac:    0.75
 gaps_fill:  4
 grow_fill:  3
 tile_fuzz:  2
 snapfb:     0
 rawfb:      null
 pipeinput:  null
 gui:        0
 gui_mode:   null
 noremote:   0
 unsafe:     0
 privremote: 0
 safer:      0
 nocmds:     0
 deny_all:   0

21/06/2006 21:46:02 x11vnc version: 0.7.3 lastmod: 2005-08-07
21/06/2006 21:46:02 Using X display :0
21/06/2006 21:46:02
21/06/2006 21:46:02 ------------------ USEFUL INFORMATION ------------------
21/06/2006 21:46:02 X DAMAGE available on display, using it for polling hints.
21/06/2006 21:46:02   To disable this behavior use: '-noxdamage'
21/06/2006 21:46:02 Wireframing: -wireframe mode is in effect for window moves.
21/06/2006 21:46:02   If this yields undesired behavior (poor response, painting21/06/2006 21:46:02   errors, etc) it may be disabled:
21/06/2006 21:46:02    - use '-nowf' to disable wireframing completely.
21/06/2006 21:46:02    - use '-nowcr' to disable the Copy Rectangle after the
21/06/2006 21:46:02      moved window is released in the new position.
21/06/2006 21:46:02   Also see the -help entry for tuning parameters.
21/06/2006 21:46:02   You can press 3 Alt_L's (Left "Alt" key) in a row to
21/06/2006 21:46:02   repaint the screen, also see the -fixscreen option for
21/06/2006 21:46:02   periodic repaints.
21/06/2006 21:46:02 XFIXES available on display, resetting cursor mode
21/06/2006 21:46:02   to: '-cursor most'.
21/06/2006 21:46:02   to disable this behavior use: '-cursor arrow'
21/06/2006 21:46:02   or '-noxfixes'.
21/06/2006 21:46:02 using XFIXES for cursor drawing.
21/06/2006 21:46:02 GrabServer control via XTEST.
Xlib:  extension "RECORD" missing on display ":0.0".
21/06/2006 21:46:02 XKEYBOARD: all 28 "must have" keysyms accounted for.
21/06/2006 21:46:02   Not automatically switching to -xkb mode.
21/06/2006 21:46:02   If some keys still cannot be typed, try using -xkb.
21/06/2006 21:46:02   Also, remember "-remap DEAD" for accenting characters.
21/06/2006 21:46:02 --------------------------------------------------------
21/06/2006 21:46:02
21/06/2006 21:46:02 Default visual ID: 0x23
21/06/2006 21:46:03 Read initial data from X display into framebuffer.
21/06/2006 21:46:03 X display :0.0 is 32bpp depth=24 true color

FrameBuffer Info:
 width:            1024
 height:           768
 scaled_width:     1024
 scaled_height:    768
 indexed_color:    0
 bits_per_pixel:   32
 depth:            24
 red_mask:   0x00ff0000  00000000111111110000000000000000
 green_mask: 0x0000ff00  00000000000000001111111100000000
 blue_mask:  0x000000ff  00000000000000000000000011111111
 red:   max: 255  shift: 16
 green: max: 255  shift:  8
 blue:  max: 255  shift:  0
 mainfb_bytes_per_line: 4096
 rfb_fb_bytes_per_line: 4096
 format:     ZPixmap
 byte_order: LSBFirst
 bitmap_pad:  32
 bitmap_unit: 32
 bitmap_bit_order: LSBFirst
 main_fb:     0xb799e008
 rfb_fb:      0xb799e008

21/06/2006 21:46:03 setting up 32 cursors...
21/06/2006 21:46:03   done.
21/06/2006 21:46:03 Autoprobing TCP port
21/06/2006 21:46:03 Autoprobing selected port 5901
21/06/2006 21:46:03 created 32 tile_row shm polling images.
21/06/2006 21:46:04 fb read rate: 5 MB/sec
21/06/2006 21:46:04 screen setup finished.
21/06/2006 21:46:04
21/06/2006 21:46:04 WARNING: You are running x11vnc WITHOUT a password.  See
21/06/2006 21:46:04 WARNING: the warning message printed above for more info.
21/06/2006 21:46:04
21/06/2006 21:46:04 The VNC desktop is Dapper:1
PORT=5901

---

### Post by scxtt on 2006-06-21
yeah, it's not pretty, but it performs MUCH better than vino ... and there probably is a way to stop it from printing that crap - either w. a flag or something better than simple stdout redirection to a file ... i've been using it for a week and it hasn't bothered me that much ...

and all that output can be ignored ...

---

### Post by Sweezel on 2006-06-21
There should be a better GUI solution in Ubuntu.

I will live with vino-server until some other solution works easier.


Sorry, I am a believer in utilities that support the average smb user w/o resorting to custom scripts etc.

---

### Post by scxtt on 2006-06-21
eh, i think vino hogging resources and required to be killed is more of a hassle than the one time output from x11vnc ... besides, your husband should be the one seeing it, not you - unless you start the server for him (i.e. no SSH access on XP) ... you could make a launcher on the desktop and just not see the output, i think that'd work ...

i hate vino, actually :p

and i'm not understanding what your last line is referring to ... this has nothing to do w/ samba and isn't a custom script ...

---

### Post by Sweezel on 2006-07-19
I did a check of "open files" in use by vino-server by right clicking it in the "System Monitor". It shows a file type of "network connection" still open to my IP address at work!

My PC at work is turned off so I don't understand why this connection is still open. The only way I know to speed my PC back up is to "kill" or "stop" vino-server.

Is there a way to just stop this network connection w/o killing vino-server?


Thanks

---

### Post by econmit on 2007-12-11
I am having the same issue, after a while (sometimes days) my vino-server and Xorg skyrocket in 'top' up to around 30% and my computer's performance goes down a lot. 

I'm using Ubuntu 7.0.

Is there any solution to this other than getting rid of vino-server and using a different VNC server?

---

