---
title: "aiglx on i915 _today_ (end of August 2006)"
date: 2006-08-24
forum: Desktop Environments
---

### Post by mdwuznik on 2006-08-24
Hi folks, 
I've recently got back to my i915 laptop and would like to get as much as possible from my i915. Judging from March/April posts there were many people very happy with aiglx performance on their i915, and Xgl was running OK on mine till recently, but fairly slow,so I decided to give a go to aiglx. I have a working Xorg-air server (ps aux |grep air shows it), glxgears shows 800 FPS, so the direct rendering is really there (same according to glxinfo), 
so I should in general be prepared. The Xorg logs shows nicely the DRI stuff and the AIGLX stuff, with only worrying messages of :
[HTML]
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0[/HTML]

Trying to get compiz/cgwd work compiz, compiz-gnome,compiz-core
ver. 0.0.13.37 (I assume that means quinn, not vanilla ?) I unfortunately get errors:

compiz --replace:
[HTML] 
libGL warning: 3D driver claims to not support visual 0x4b
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0
[/HTML]

and the probably better way of running
 compiz --strict-binding --indirect-rendering --replace gconf
says:

[HTML]
libGL warning: 3D driver claims to not support visual 0x4b
compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0
[/HTML]

0x4b again, for 24 bit depth (haven't tried for 16).

Guessing a bit I tried:
compiz --strict-binding --direct-rendering --replace gconf

which results in the same as simple compiz --replace gconf &
(no  GLX_EXT_texture_from_pixmap ).

My glxinfo output follows:
[HTML]
 glxinfo 
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

[/HTML]


Is there anyone who can give some more hints (or anyone with working compiz on i915, so I could possibly steal his configs :).

Cheers
Michal

PS:Just realized, that glxgears often crashes with 
[HTML]
michal@jabberwocky:~$ glxgears 
libGL warning: 3D driver claims to not support visual 0x4b
4332 frames in 5.0 seconds = 866.383 FPS
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
[1]+  Done                    sudo synaptic
Przerwane
michal@jabberwocky:~$ glxgears 
libGL warning: 3D driver claims to not support visual 0x4b
4245 frames in 5.0 seconds = 848.815 FPS
3756 frames in 5.0 seconds = 750.672 FPS
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Przerwane
michal@jabberwocky:~$ 

[/HTML]

---

### Post by logus on 2006-08-25
Just got the same error:
```
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int*)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted
```
It appeared just after yesterday's 'apt-get dist-upgrade' (2006-08-24). mesa-packages and some other things were upgraded.

Also my screensaver ('flurry') began to freeze.

Really think it's because mesa upgrades.

P.S.: i915 graphics, compiz-quinn packages (used for 2 months w/o any problems).

---

### Post by mdwuznik on 2006-08-25
Sorry for asking - AIGLX or Xgl ?
Xgl worked with no problems for some time:)

Michal

---

### Post by logus on 2006-08-25
> Sorry for asking - AIGLX or Xgl ?
Xgl worked with no problems for some time

compiz 0.0.13.37-0ubuntu4
compiz-quinn-aiglx 0.0.13-0ubuntu2

But this problem appears after upgrading mesa packages, so I suppose they are causing it.

libgl1-mesa 6.5.1+cvs20060824
libgl1-mesa-dri 6.5.1+cvs20060824
libglu1-mesa 6.5.1+cvs20060824
mesa-utils 6.5.1+cvs20060824

What versions of mesa do you have installed? (dpkg -l | grep mesa)

---

### Post by logus on 2006-08-25
> **mdwuznik said:**
> Sorry for asking - AIGLX or Xgl ?
Xgl worked with no problems for some time:)

Right now I tried to disable compiz and switched to standard Xorg server (from Xorg-air). Error message running glxgears (error output see in messages above) remains the same. However, it seems that random screensaver freezes and x-server restarts stopped.

Will wait to next mesa build. I mind if it is ubuntu-specific bug, or it appears in other linux distributions too?..

---

### Post by ayoli on 2006-08-25
hi,
hmm, i've got the same error with glxgears, and i renember one or two freeze with a screensaver (dont renember which one), i also use aiglx/compiz-quinn but i thought it was more a problem of i810/915 driver from Xorg.
however, my aiglx/compiz works fine.
regards.

---

### Post by logus on 2006-08-25
> **ayoli said:**
> hi,
hmm, i've got the same error with glxgears, and i renember one or two freeze with a screensaver (dont renember which one), i also use aiglx/compiz-quinn but i thought it was more a problem of i810/915 driver from Xorg.
however, my aiglx/compiz works fine.
regards.

Many (if not any) of installed screensavers freezes after some seconds, when running under Xorg-air. After switching to standard Xorg, all freezes and hangs stopped, but glxgears error remains the same. I tried to run some screensavers (gl and non-gl) for some half an hour, and some apps with extensive graphic usage -- works fine (standard Xorg).

---

### Post by mdwuznik on 2006-08-25
Hmm, where did you exactly get compiz-quinn-aiglx ?
It's missing on mine Ubuntu :)

---

### Post by logus on 2006-08-25
> **mdwuznik said:**
> Hmm, where did you exactly get compiz-quinn-aiglx ?
It's missing on mine Ubuntu :)

Here: [http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068) and here: [http://xgl.compiz.info](http://xgl.compiz.info)

---

### Post by mdwuznik on 2006-08-25
I got the quinn repos enabled, I lack only compiz-quinn-aiglx (compiz-vanilla-aiglx is there). compiz-quinn-aiglx dissapeared some 4 days ago.

---

### Post by Freedreamer on 2006-08-26
hi guys ,
i'm italian.
 today i've updated xserver-xorg-air-core and after reboot aiglx doesn't work correctly: i can't see the edges of the windows.
i post an image
any idea?

---

### Post by defeca on 2006-08-26
> **Freedreamer said:**
> hi guys ,
i'm italian.
 today i've updated xserver-xorg-air-core and after reboot aiglx doesn't work correctly: i can't see the edges of the windows.
i post an image
any idea?

Hi, I had the same problem here!! Does anyone know what happened?

---

### Post by Freedreamer on 2006-08-26
so i'm not the only one...](*,) ](*,) 

temporally i make a downgrade to the previous version of Xorg-air

---

### Post by mdwuznik on 2006-08-26
Hi guys, 
After some fight which in fact started this thread I decided  to install a fresh system to check if I can get it running at all. To my surprise I have everything working now, with minor hiccups of installing compiz-quinn-aiglx from the old /var/cache/apt/archives, cause I can't find it in the repos.
Concerning the lacking decoration - have you tried "cgwd --replace" and/or "compiz --replace gconf" ? You may also want to check if the decoration plugin is enabled (in gset-compiz).
With aiglx I can really see performance, not poorformance of  i915 (but do not try to use blur :))
Good luck...

---

### Post by Freedreamer on 2006-08-26
i have no tried "cgwd --replace" and/or "compiz --replace gconf"  because now i have the previous version of Xorg-air but if anyone want to try pls write the result here.

thanks again

---

### Post by Freedreamer on 2006-08-26
[http://www.compiz.net/topic-3579-aiglx-xorg-air-cannot-start](http://www.compiz.net/topic-3579-aiglx-xorg-air-cannot-start)


maybe?

---

### Post by mdwuznik on 2006-08-26
No, that causes it to fail loading, not to lose the decoration (BTDT).
I had the disappearing borders problems before, but I finally screwed up compiz so bad, that I reinstalled the system (having the same home it took sufficently short time :) )

---

### Post by Freedreamer on 2006-08-26
i don't want to reinstall the system ... :(

---

### Post by mdwuznik on 2006-08-26
I know, I'm really far from advertising reinstall as the cure of all problems. I admit this is the way of saying "I'm not knowledgeable enough to repair it" to yourself and the world, but is faster than repairing sometimes...
Economy of movement, that is (when you want to spend time working, rather than fiddling with your system). 

I just said the thing about reinstall to make you know, that the "disappearing border" problem happened before with different package versions, than you have, and vice-versa - that the same versions may work, nothing more.

Sorry if you counted it is Windows ultimate support answer "reinstall will cure it" :)

---

### Post by kairu0 on 2006-08-27
> **logus said:**
> Just got the same error:
```
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int*)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted
```
It appeared just after yesterday's 'apt-get dist-upgrade' (2006-08-24). mesa-packages and some other things were upgraded.

Also my screensaver ('flurry') began to freeze.

Really think it's because mesa upgrades.

P.S.: i915 graphics, compiz-quinn packages (used for 2 months w/o any problems).

Exactly the same error on the same hardware here. Has anyone resolved this?

---

### Post by T8y8 on 2006-08-27
I've got the same error as well.

---

### Post by dentaku65 on 2006-08-27
Maybe you did not change the compiz-start script, see here:

[http://yep.it/?chzjnh](http://yep.it/?chzjnh)

---

### Post by kairu0 on 2006-08-29
Has anyone solved this yet?

DRI returns that it is Enabled in /var/log/X.org.log. All packages are current. DRI is still not working.

---

### Post by dentaku65 on 2006-08-29
> **kairu0 said:**
> Has anyone solved this yet?

DRI returns that it is Enabled in /var/log/X.org.log. All packages are current. DRI is still not working.

Try to do this, fix for me.

> sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`

---

### Post by kairu0 on 2006-08-29
> **dentaku65 said:**
> Try to do this, fix for me.

I already had the dri modules installed, however I re-installed them as you suggested and no result. Anyone else have an idea?

---

### Post by PathSpace on 2006-08-29
I also get the same error with glxgears (I have the same hardware as well), but have not been worrying about it since Compiz works fine...

---

### Post by kairu0 on 2006-08-29
> **PathSpace said:**
> I also get the same error with glxgears (I have the same hardware as well), but have not been worrying about it since Compiz works fine...

So, you are saying the Compiz works, but hardware acceleration is broken?

---

### Post by ayoli on 2006-08-30
The error or/and glxgears crash doesn t mean that diret rendering doesn t work:
```
[23:50:38@ayoli.zone]:~ >$ glxinfo |grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```
this problem is also discussed [here]("http://www.compiz.net/topic-3517-1.html")
regards.

---

### Post by kairu0 on 2006-08-30
> **ayoli said:**
> The error or/and glxgears crash doesn t mean that diret rendering doesn t work:
```
[23:50:38@ayoli.zone]:~ >$ glxinfo |grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```
this problem is also discussed [here]("http://www.compiz.net/topic-3517-1.html")
regards.

This thread seems to be about X crashing, not 3d acceleration not functioning. Now, I'm only speaking for myself when I say X hasn't crashing, but 3d accleration is still broken.

---

### Post by nikopol on 2006-09-02
I've tried all the various fixes that seem to offered but to no avail. looks like aiglx is well and truly broken on my laptop.

EDIT: Mmm... looks like it's mysteriously started to work again now I've stopped trying to solve the problem. As a result, I'm sorry I can't offer any of the steps I followed to recover it but it is indeed working now despite not responding to any of the other efforts to solve it...

---

### Post by kairu0 on 2006-09-02
I downgraded Mesa and Mesa-DRI packages to the Ubuntu Official version and switched back to Metacity. Finally, glxgears works.

I think I'll wait until AIGLX becomes more stable before I try it again.

---

### Post by Freedreamer on 2006-09-03
[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

if you want stable this is the guide i guess

good luck!

---

### Post by ayoli on 2006-09-03
> **Freedreamer said:**
> [http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

if you want stable this is the guide i guess

good luck!

this is almost the same guide as [gandalfn's]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/") one, based on the same xorg-air and compiz packages, but for kde.
this is almost stable for me, however i have same the glxgears errors as ppl here.

---

### Post by snape on 2006-09-03
Be considerate. Your work will be used by other people, and you in turn will depend on the work of others. Any decision you take will affect users and colleagues, and we expect you to take those consequences into account when making decisions. For example, when we are in a feature freeze, please don't upload dramatically new versions of critical system software, as other people will be testing the frozen system and not be expecting big changes. 

Be respectful. The Ubuntu community and its members treat one another with respect. Everyone can make a valuable contribution to Ubuntu. We may not always agree, but disagreement is no excuse for poor behaviour and poor manners. We might all experience some frustration now and then, but we cannot allow that frustration to turn into a personal attack. It's important to remember that a community where people feel uncomfortable or threatened is not a productive one. We expect members of the Ubuntu community to be respectful when dealing with other contributors as well as with people outside the Ubuntu project, and with users of Ubuntu. 

Be collaborative. Ubuntu and Free Software are about collaboration and working together. Collaboration reduces redundancy of work done in the Free Software world, and improves the quality of the software produced. You should aim to collaborate with other Ubuntu maintainers, as well as with the upstream community that is interested in the work you do. Your work should be done transparently and patches from Ubuntu should be given back to the community when they are made, not just when the distribution releases. If you wish to work on new code for existing upstream projects, at least keep those projects informed of your ideas and progress. It may not be possible to get consensus from upstream or even from your colleagues about the correct implementation of an idea, so don't feel obliged to have that agreement before you begin, but at least keep the outside world informed of your work, and publish your work in a way that allows outsiders to test, discuss and contribute to your efforts. 

When you disagree, consult others. Disagreements, both political and technical, happen all the time and the Ubuntu community is no exception. The important goal is not to avoid disagreements or differing views but to resolve them constructively. You should turn to the community and to the community process to seek advice and to resolve disagreements. We have the Technical Board and the Community Council, both of which will help to decide the right course for Ubuntu. There are also several Project Teams and Team Leaders, who may be able to help you figure out which direction will be most acceptable. If you really want to go a different way, then we encourage you to make a derivative distribution or alternative set of packages available using the Ubuntu Package Management framework, so that the community can try out your changes and ideas for itself and contribute to the discussion. 

When you are unsure, ask for help. Nobody knows everything, and nobody is expected to be perfect in the Ubuntu community (except of course the SABDFL). Asking questions avoids many problems down the road, and so questions are encouraged. Those who are asked should be responsive and helpful. However, when asking a question, care must be taken to do so in an appropriate forum. Off-topic questions, such as requests for help on a development mailing list, detract from productive discussion. 

Step down considerately. Developers on every project come and go and Ubuntu is no different. When you leave or disengage from the project, in whole or in part, we ask that you do so in a way that minimises disruption to the project. This means you should tell people you are leaving and take the proper steps to ensure that others can pick up where you leave off. 

Mailing Lists and Web Forums
Mailing lists and web forums are an important part of the Ubuntu community platform. This code of conduct applies very much to your behaviour in those forums too. Please follow these guidelines in addition to the general code of conduct:

all the best//snape//registered.user    s///robertson8) =D>

---

### Post by kairu0 on 2006-09-03
Be relevant. Please remember that this thread is a serious discussion about a real problem, and many users are in discussion. Please post relevant guidelines that will lead to that goal, not distract from the main issue.

---

### Post by jshayden on 2006-09-18
> **kairu0 said:**
> I downgraded Mesa and Mesa-DRI packages to the Ubuntu Official version and switched back to Metacity. Finally, glxgears works.

I think I'll wait until AIGLX becomes more stable before I try it again.

How did you go about doing this?  I've given up on AIGLX/XGL for now as well, and I'd just like 3d accel back.  Which version(s) did you downgrade to?

Thanks,
Josh

---

