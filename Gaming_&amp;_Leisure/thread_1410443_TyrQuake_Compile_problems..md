---
title: "TyrQuake Compile problems."
date: 2010-02-18
forum: Gaming &amp; Leisure
---

### Post by dancingtofu on 2010-02-18
Hello! I have been trying to compile TyrQuake, but have been running into some problems. The README says to just type "make", it doesn't tell me any required libraries or anything. So I type make and this is what happens.
```

~/Downloads/tyrquake-0.61$ make
  MKDIR   build/nqsw
  MKDIR   build/nqgl
  MKDIR   build/qwsw
  MKDIR   build/qwgl
  MKDIR   build/qwsv
  CC      build/nqsw/cd_common.o
  CC      build/nqsw/chase.o
  CC      build/nqsw/cl_demo.o
NQ/cl_demo.c: In function ‘CL_GetMessage’:
NQ/cl_demo.c:125: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
  CC      build/nqsw/cl_input.o
  CC      build/nqsw/cl_main.o
  CC      build/nqsw/cl_parse.o
  CC      build/nqsw/cl_tent.o
  CC      build/nqsw/cmd.o
  CC      build/nqsw/common.o
NQ/common.c: In function ‘COM_Init’:
NQ/common.c:1018: warning: dereferencing type-punned pointer will break strict-aliasing rules
  CC      build/nqsw/console.o
common/console.c: In function ‘Con_NotifyBox’:
common/console.c:629: warning: format not a string literal and no format arguments
  CC      build/nqsw/crc.o
  CC      build/nqsw/cvar.o
  CC      build/nqsw/host.o
  CC      build/nqsw/host_cmd.o
NQ/host_cmd.c: In function ‘Host_Loadgame_f’:
NQ/host_cmd.c:580: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
NQ/host_cmd.c:587: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
NQ/host_cmd.c:589: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
NQ/host_cmd.c:595: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
NQ/host_cmd.c:599: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
NQ/host_cmd.c:600: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
NQ/host_cmd.c:616: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
  CC      build/nqsw/keys.o
  CC      build/nqsw/mathlib.o
  CC      build/nqsw/menu.o
NQ/menu.c: In function ‘M_ScanSaves’:
NQ/menu.c:464: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
NQ/menu.c:465: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
  CC      build/nqsw/net_dgrm.o
NQ/net_dgrm.c: In function ‘_Datagram_Connect’:
NQ/net_dgrm.c:1324: warning: format not a string literal and no format arguments
  CC      build/nqsw/net_loop.o
  CC      build/nqsw/net_main.o
  CC      build/nqsw/pr_cmds.o
  CC      build/nqsw/pr_edict.o
  CC      build/nqsw/pr_exec.o
  CC      build/nqsw/r_part.o
  CC      build/nqsw/rb_tree.o
  CC      build/nqsw/sbar.o
  CC      build/nqsw/shell.o
  CC      build/nqsw/snd_dma.o
  CC      build/nqsw/snd_mem.o
  CC      build/nqsw/snd_mix.o
  CC      build/nqsw/sv_main.o
NQ/sv_main.c: In function ‘SV_SendServerinfo’:
NQ/sv_main.c:220: warning: format not a string literal and no format arguments
  CC      build/nqsw/sv_move.o
  CC      build/nqsw/sv_phys.o
  CC      build/nqsw/sv_user.o
  CC      build/nqsw/view.o
  CC      build/nqsw/wad.o
  CC      build/nqsw/world.o
  CC      build/nqsw/zone.o
  CC      build/nqsw/d_edge.o
  CC      build/nqsw/d_fill.o
  CC      build/nqsw/d_init.o
  CC      build/nqsw/d_modech.o
  CC      build/nqsw/d_part.o
  CC      build/nqsw/d_polyse.o
  CC      build/nqsw/d_scan.o
  CC      build/nqsw/d_sky.o
  CC      build/nqsw/d_sprite.o
  CC      build/nqsw/d_surf.o
  CC      build/nqsw/d_vars.o
  CC      build/nqsw/d_zpoint.o
  CC      build/nqsw/draw.o
  CC      build/nqsw/model.o
  CC      build/nqsw/r_aclip.o
  CC      build/nqsw/r_alias.o
  CC      build/nqsw/r_bsp.o
  CC      build/nqsw/r_draw.o
  CC      build/nqsw/r_edge.o
  CC      build/nqsw/r_efrag.o
  CC      build/nqsw/r_light.o
  CC      build/nqsw/r_main.o
  CC      build/nqsw/r_misc.o
  CC      build/nqsw/r_sky.o
  CC      build/nqsw/r_sprite.o
  CC      build/nqsw/r_surf.o
  CC      build/nqsw/r_vars.o
  CC      build/nqsw/screen.o
  CC      build/nqsw/cd_linux.o
  CC      build/nqsw/net_udp.o
  CC      build/nqsw/net_bsd.o
  CC      build/nqsw/snd_linux.o
  CC      build/nqsw/sys_linux.o
NQ/sys_linux.c: In function ‘Sys_DebugLog’:
NQ/sys_linux.c:226: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
NQ/sys_linux.c: At top level:
NQ/sys_linux.c:258: warning: ‘floating_point_exception_handler’ defined but not used
  CC      build/nqsw/x11_core.o
  CC      build/nqsw/in_x11.o
common/in_x11.c:28:36: error: X11/extensions/xf86dga.h: No such file or directory
common/in_x11.c: In function ‘IN_ActivateDGAMouse’:
common/in_x11.c:65: warning: implicit declaration of function ‘XF86DGADirectVideo’
common/in_x11.c:65: error: ‘XF86DGADirectMouse’ undeclared (first use in this function)
common/in_x11.c:65: error: (Each undeclared identifier is reported only once
common/in_x11.c:65: error: for each function it appears in.)
common/in_x11.c: In function ‘IN_Init’:
common/in_x11.c:232: warning: implicit declaration of function ‘XF86DGAQueryVersion’
make: *** [build/nqsw/in_x11.o] Error 1
```

Any thoughts?

---

### Post by Perfect Storm on 2010-02-19
> common/in_x11.c:28:36: error: X11/extensions/xf86dga.h: No such file or directory

Did you install the dev package of xf86dga?

---

### Post by dancingtofu on 2010-02-21
The xf86dga (dev package) was not installed, so I installed it and now it displays a bit different error.

```
~/Downloads/tyrquake-0.61$ make
  CC      build/nqsw/vid_x.o
common/vid_x.c:39:38: error: X11/extensions/xf86vmode.h: No such file or directory
common/vid_x.c:107: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;saved_vidmode&#8217;
common/vid_x.c: In function &#8216;VID_set_vidmode&#8217;:
common/vid_x.c:445: error: &#8216;XF86VidModeModeInfo&#8217; undeclared (first use in this function)
common/vid_x.c:445: error: (Each undeclared identifier is reported only once
common/vid_x.c:445: error: for each function it appears in.)
common/vid_x.c:445: error: &#8216;modes&#8217; undeclared (first use in this function)
common/vid_x.c:446: error: &#8216;mode&#8217; undeclared (first use in this function)
common/vid_x.c:452: warning: implicit declaration of function &#8216;XF86VidModeGetAllModeLines&#8217;
common/vid_x.c:466: warning: implicit declaration of function &#8216;XF86VidModeSwitchToMode&#8217;
common/vid_x.c:470: error: &#8216;saved_vidmode&#8217; undeclared (first use in this function)
common/vid_x.c: In function &#8216;VID_restore_vidmode&#8217;:
common/vid_x.c:481: error: &#8216;saved_vidmode&#8217; undeclared (first use in this function)
common/vid_x.c: In function &#8216;VID_Init&#8217;:
common/vid_x.c:531: warning: implicit declaration of function &#8216;XF86VidModeQueryVersion&#8217;
common/vid_x.c:687: warning: implicit declaration of function &#8216;XF86VidModeSetViewPort&#8217;
make: *** [build/nqsw/vid_x.o] Error 1
```

Thanks so much!

---

### Post by Perfect Storm on 2010-02-21
> common/vid_x.c:39:38: error: X11/extensions/xf86vmode.h: No such file or directory

dev package of libxxf86vm1

---

### Post by dancingtofu on 2010-02-22
Ok, I installed both xf86dga and libxxf86vml dev packages and it compiled, albiet with several non-critical errors. So now I have executables, but now it displays this error message when I try to launch it.

```

~/Downloads/tyrquake-0.61$ ./tyr-quake
FindFile: can't find gfx/pop.lmp
Playing shareware version.
FindFile: can't find gfx.wad
Error: W_LoadWadFile: couldn't load gfx.wad
VID_Shutdown
Segmentation fault

```

I really hate asking for support here instead of an official forum, but I have not been able to locate an official forum or wiki or FAQ, and the only documentation just says "Type Make", it doesn't say where to put your game data or anything (I put the Id1 folder in the same directory as the tyrquake executable and even tried renaming it to id1. Oh wait! I tried changing the uppercase file names inside the folder to lowercase and at least I get something on the screen, but it freezes my machine (luckily Firefox saved this reply for me). I am not sure if it is related to the errors I received while compiling or simply a hardware issue.

On a different note, I really should have been able to figure out I needed xf86dga from the error message output, but how did you equate xf86vmode.h with the libxxf86vml dev package? I am asking so next time I can just grab packages and solve problems myself instead of relying on others to do the hard work for me. I've been using Linux exclusively almost a year now and I think it is time I really get comfortable doing these kinds of things myself without giving up at the first sign of trouble. 

Thanks, Artificial Intelligence, for your help and I appreciate any kind of tips you can give me or documentation you can point me towards to help me in my advanced usage of Linux!

**UPDATE**
I tried running tyrquake again, this time I tried the OpenGL Quake executable and that works fine, but no sound. If that is the only problem, I'm happy. Im sure I can figure out a sound issue, but I'd still appreciate some advice on how to solve compilation issues in the future. Thanks!

---

