---
title: "ATI 8.42.3 with Xpress 200m and Compiz-Fusion on Gutsy Gibbon"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by goodguy20k on 2007-10-23
Ok, so here's the deal: I couldn't wait for the latest and greatest. ;)

So my setup is a Compaq R4000, which has an AMD Athlon 64-bit, but I'm running 32-bit Gutsy Gibbon, released edition. When I used the fglrx (ATI proprietary) 8.40.X, desktop effects wouldn't work. "No composite".

Nothing new, so I waited for 8.42.3. It has the composite built in, right? Great, right?

I installed it, enabled the composite in "/etc/X11/xorg.conf", and white listed the fglrx driver in Compiz. Click the radio button and... Nothing. Could not start the effects, it says. I proceeded to grumble. :P

Then I opened a terminal and ran "compiz". "Blacklisted PCIID '1002:5955' found" was the result of the command. Yes, I know I have a pathetic version of an ATI card. (Somewhere I read it's the r480 family GPU, I think?) A little googlin' and... I found how to get around the black list: "SKIP_CHECKS=yes compiz". And...

White screen! It all looked like it was working well, and then it shows completely white, plus the mouse cursor. O_O Yes, I could move the cursor around the screen, and it changed per window below it, that I could not see. I could even click back into the terminal and CTRL+C Compiz out. It's a step in the right direction, I think, but... I'm not sure which way to head now. Any thoughts?

---

### Post by goodguy20k on 2007-10-23
Just a little more... Tried some stuff mentioned here: [http://ubuntuforums.org/showthread.php?t=589075](http://ubuntuforums.org/showthread.php?t=589075)

Well, interesting thing... I'm still stuck with MESA. :?

> ~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


> $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

Any thoughts with this? (And if you look at the thread I linked, which links to another thread, I have tried their methods to ditch MESA. No luck. :( )

---

### Post by marsmissionaries on 2007-10-23
you need to install it properly. 

If you just ran the driver install file then it will not work.


You have to use the build package filter.


I'm sure if you go over to the phoronix forums and request a script to install the driver for you they will provide you with one.


Installing without a script is very dificult.



Also: Performance on the x 200m isn't the best, there is some graphical errors here and there, and it used large amounts of CPU.

---

### Post by Jay_Davis on 2007-10-23
I wouldn't bother with it. I have the same graphics, Xpress 200m, in my Acer Aspire 5100. I got 8.42.3 drivers installed and working fine with Compiz but 2d performance was TERRIBLE. Scrolling web pages had 1-2 seconds of lag with massive tearing. You're better off sticking with XGL, it's faster and more stable, at least for now.

---

### Post by goodguy20k on 2007-10-24
Ok, so I did the packaged based install... Now...

No OpenGL, period. :lol: MUCH better, eh? ;)

> $ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

> $ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

I followed the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually)

I may just roll back. ::sigh:: What did I do wrong?

---

### Post by goodguy20k on 2007-10-24
So I searched the system and there is NO libGL.so.1 file. Now look close, and that'll make sense. :P They DID install a "libGL.so.1.2", the default name, BUT... It doesn't look for that name, for some reason! It looks for "libGL.so.1", so I copied a backup, renamed and... VIOLA! EVERYTHING'S WORKING! :D Compiz runnin' pretty darn smoothly, and all that good stuff!

Now if I could figure out if it was an ATI or my side goof. :P

EDIT: Well, mostly. :-P Some of my OpenGL apps aren't doin' so well. Mostly flashing.. New bug to sniff out. :P ;)

---

### Post by trishacupra on 2007-10-24
Are you getting ati or mesa still in fglrxinfo? I can't get ati - I'm stuck on mesa. I have Xress 200m too.

---

### Post by goodguy20k on 2007-10-25
I'm now fully have ATI, not MESA. :) Did you follow the packaged based manual install? Not just running the .run file, but with the flags for ubuntu? If all goes well, it'll work from there. On the other hand, if it works like it did for me, after you run the packaged based install, fglrxinfo will report that it can't find "libGL.so.1". If you get that, come back and let me know. :)

---

### Post by alina.bolero on 2007-10-25
I was able to execute the run script directly without too much trouble, but I have to shut down Compiz-Fusion whenever I am going to view movies or start Secondlife or GoogleEarth.  Otherwise I get that nasty flicker.

I would LOVE to be able to run my 3D apps without having to shut down Compiz.

I don't even know where to start looking to debug this one.

---

### Post by goodguy20k on 2007-10-25
There are work arounds for most Video players. Search this forum. This is the thread that worked for me: [http://ubuntuforums.org/archive/index.php/t-507332.html](http://ubuntuforums.org/archive/index.php/t-507332.html)

As to OpenGL apps (Google Earth), I was tipped off on the Compiz forum about the Extra WM Actions plugin. Look in the CompizConfig Settings window for it. Setup a key shortcut for the redirect toggle. When you run an OpenGL app and it's flickering or whatever, hit the redirect action, and it MIGHT fix it. :)

---

### Post by alina.bolero on 2007-10-25
> **goodguy20k said:**
> There are work arounds for most Video players. Search this forum. This is the thread that worked for me: [http://ubuntuforums.org/archive/index.php/t-507332.html](http://ubuntuforums.org/archive/index.php/t-507332.html)

As to OpenGL apps (Google Earth), I was tipped off on the Compiz forum about the Extra WM Actions plugin. Look in the CompizConfig Settings window for it. Setup a key shortcut for the redirect toggle. When you run an OpenGL app and it's flickering or whatever, hit the redirect action, and it MIGHT fix it. :)

OK.  Maybe I'm a moron, but the field for the shortcut key won't accept anything but basic letters of the alphabet.  How do I assign, say "CTL+F1" to the field?

---

### Post by reiki on 2007-10-25
> **alina.bolero said:**
> OK.  Maybe I'm a moron, but the field for the shortcut key won't accept anything but basic letters of the alphabet.  How do I assign, say "CTL+F1" to the field?

You're not a moron... either that or I'm a moron right there with ya :)

I just figured it out too.... don't double-click so that the "Add a Key" dialogue pops up. Just click on the empty space to the right of the action you want to modify. Like you are clicking (once) in the "Key" column next to the action you want to modify. You'll then see "New Accelerator" in that column. Now hit your key combo and it will take it correctly.

---

### Post by alina.bolero on 2007-10-25
Thank you for the instructions.

Well, the WM redirect thing works for both Google Earth and Second Life, but it's VERY temporary.  As soon as I pan in Google Earth, it goes back to flickering again, and as soon as I try to IM in SL, it starts flickering again.

What DOES seem to work a bit better, is the fullscreen toggle in the WM options:  [http://wiki.compiz-fusion.org/Plugins/Extrawm]("http://wiki.compiz-fusion.org/Plugins/Extrawm")

I can live with that, since I usually run Google Earth and Second Life in full screen anyway.

I'm happy!  :)

---

### Post by Qrikko on 2007-10-30
Hi, yeah had some problems as well..

first I was running beryl with compiz but "upgraded to" compiz fusion and first of all it's much sleeker and feel like a better design of options and everything so thanks for that ^^

BUT this did help.. I just want to confirm my experiance :)

I have been able to run all opengl apps with both these solutions.. it feels like a hack.. but hey I have my 3D desctop, and I can run my apps.. I can do so with aiglx now! (pat ati.. now now that wasn't so bad now was it? now BACK TO WORK LAZY SOBS! ;))

so tested and working:
WoW in opengl under wine-0.9.48, though I would love to see some work done to the mouse hardware support or something simular for opengl / wine.. would rawk, since my framerate is actually better when I run in wine then it was in vista .. about 7fps actually I won the day I said: "WTF bill? is this all you can come up with *sigh* this is it no more... never again ->ubuntu* I can't run in D3d, or maybe it's possible but the glitches are too huge for me probably it's fixable.. but it's almost worth it to have mouse fully supported.

Google earth, work nice in fullscreen.. thought when I get tooltips I have to redo it.. like give it focus again.. because it start flickering (still it's usable)

Tough I have to run X11 for mplayer it hardlocked when I used gl and tried to use this WM utility from compiz.. 

but it's all working, I'm on the very nasty 200m chip but all working I say go for 8.42.3 because I have better performance with it and composite / aiglrx then I had when I had to use xgl :)

very nice thread!

---

### Post by jetdog440 on 2007-10-30
Hello all!  I went nuts this weekend with the x200m and 8.42.3 + ubuntu on x64 AND x32.

To all those attempting the new ATI drivers with 8.42.3 on the ATI Xpress 200M chip, i can confirm that if you follow the instructions and your intuitive common sense, you WILL be able to run on the new drivers with good performance - increased FPS and smoother video.

******A NOTE of caution with the x200m and compiz-fusion:
In compiz-fusion, the X200m IS blacklisted... you'll have to search how to UN-blacklist it
in compiz's initialization.  I've tested its performance with the 8.42.3 driver and it does work with compiz-fusion, however, it currently has some SERIOUS issues with videos playing in the X-video extension, AND in OpenGL.  For some reason, there's some serious flickering issues on X-video and Open-Gl accelerated videos in window-mode, sometimes the videos show for 1/2 a second then disappear until the window is moved again.  Fullscreen video playback works FINE, until you initiate a 3D cube rotation with compiz or something else that moves the 3D surface your video is on.  - You CAN switch you video playback to X11, to get around these issues if you have something of a decent processor or a non-laptop, but this is usually ugly and pixelated.  Also, Open-GL games work VERY SLOW once you start playing them via compiz-fusion which runs the game through ATI's AIGLX, because the X200m seems to require the support of the CPU for running hardware-acceperated environments on hardware-accelerated surfaces. (i.e. games, videos, etc, on compiz-fusion, which runs them through aiglx)  TO ME, this seems SUFFICIENT enough reason to keep the compiz-fusion disabled on the x200m.  Your alternative would be to use a non-aiglx system to run these, such as xserver-xgl.  I tried compiz-fusion with this too, and tried specifically disabling aiglx in xorg.conf with xgl - the x-videos RAN, but i couldn't run open-gl, because xgl doesn't support it.  Also important, running the videos in fullscreen with xgl and compiz-fusion used LOTS of cpu, and any 3d-manipulations in compiz-fusion really cranked the cpu while a video was playing - but it did play.  So if you don't care much for your cpu or you have a desktop, and you still want compiz-fusion, this MIGHT be good for you.  The way i see it, compiz-fusion is asking a LOT from the cpu because of the way the x200m is designed... and although aiglx is a nice addon, for THIS CARD IN PARTICULAR, it's a bad idea because of how much cpu we're wasting at the expense of having our stuff on a hardware-accelerated surface.

I will continue to investigate a more cpu-friendly way of doing this, and i'll be watching the ati drivers as well.

If anyone feels so compelled to have the x200m and 8.42.3 working with the "pretty  cube", go ahead and follow my guide below, then un-blocklist your card from compiz-fusion, and and give it a go (the nice thing is that you can always disable/enable compiz-fusion on the go without logging off, so if you just wanna see it the way it is right now etc, because it DOES work, just not that great yet cuz of x-video and opengl). 

If you want the "pretty cube" efficiently, try to find a working version of beryl for gutsy without destroying your new os too much.  You'll have to run it in xgl, which means that while you're logged IN the xgl session, you'll be forced  to stay away from open-gl.

What i recommend is go ahead with the new drivers, because they have smoother fps and better open-gl support (I'm doing that right now), but stay away from compiz-fusion i.e. ubuntu's "desktop Effects".

Here's how to UN-blacklist ALL cards from compiz-fusion, so you can try the x200m with compiz-fusion:

echo SKIP_CHECKS=yes > ~/.config/compiz/compiz-manager

#Save, then go ahead and enable desktop effects in ubuntu.  You can always disable them later, so i encourage you to try/  Best of luck with compiz and Ati X200 + 8.42.3!


******</End rant on x200m and compiz-fusion> ******

Here's basically what i did.  I went ahead with the NON-gui install... you can be more sure that it worked well...

# These are needed to compile your driver into the kernel
sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

-Download the 8.42.3 drivers from ati's site
[URL="http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run"]
http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run[/URL]

./ati-driver-installer-8.42.3-x86.x86_64.run --extract atidump

*********
-If you are a 64-bit user, you WILL have to patch your drivers with a special debian patch.  ATI basically screwed up a few symlinks to some libraries on the 64-bit ubuntu

[http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2]("http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2")

In the patch for the 64-bit version, there is a folder (maybe 2 - can't remember!)
Just click/drag/copy any folders from the patch OVER ati's ones of the same name.  Ubuntu WILL merge them and replace any files with the same names (so it'll be updated properly).
I did this easily with the drag and drop way from nautilus (your little gui :) )

*********

cd atidump
./ati-installer.sh 8.42.3 --buildpkg Ubuntu/gusty

You will see FOUR new .deb files appear beside the "atidump" directory.
You ONLY have to install two of them for the card to work...

sudo dpkg -i fglrx-kernel-source<something>.deb
sudo dpkg -i xorg-driver-fglrx_<something>.deb   <-- this one has an underscore before the rest, and its not the developper .deb

Now your ati is ready to be compiled into the kernel...
sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb

# Back up your xorg.conf... I had attempted it with a default gutsy xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

You have to blacklist ubuntu's open source driver by changing /etc/default/linux-restricted-modules-common to include DISABLED_MODULES="somemodule2 fglrx" where somemodule2 is the old contents of that line. When you have finished this last change, REBOOT.

As for composite support in xorg.conf, I can't remember if i had to manually add the composite "ON" to the xorg.conf.  If it isn't there, by all means, feel free to add it.  (After all, it IS supported, why not make it official :) ! )

#in /etc/X11/xorg.conf
#At the end, if you don't already HAVE an extensions section
Section "Extensions"
        Option "Composite" "Enable"
EndSection


The other thing I discovered is that the AIGLX support is ON by default in the driver and REMAINS ON unless PURPOSELY switched off in Xorg.conf.  So you don't have to do anything crazy to enable it.  I've tested this over and over in the gnome default xserver AND in xgl.  I repeat, it's already turned on, no additional configuration is necessary.   The only thing i've seen so far that uses it is compiz fusion, so no need to worry about turning aiglx on or off :)

Best of Luck All!  Hope this helped, cuz i pieced this together from ALL over!!!

---

### Post by shriek on 2007-11-05
Do you guys find any use for the new driver? I installed it a couple of days ago and all I can say is: I want to move back to ubuntu driver+XGL+Compiz. Yes, I couldn't get Direct rendering to work (at least game like warsow can't detect direct rendering) but compiz run smoothly, video WITH compiz worked flawlessly, and I'm pretty sure that I could (once) run G Earth (though for some reason it stop working....)

I'm thinking about "downgrading" back to ubuntu driver and XGL. What do you guys think? how easy can I do this now that I have evrything set for AIGLX?

---

### Post by lachild on 2007-11-05
> I'm thinking about "downgrading" back to ubuntu driver and XGL. What do you guys think? how easy can I do this now that I have evrything set for AIGLX?

Oh no, not me.  Since upgrading to the new driver for my x200  I have noticed an overall performance boost through out the system.  The system is just running everything better.  I had no idea that the video driver was causing such a noticeable slowdown in the system.

The only thing I have noticed is that I get random graphic glitches and strange garbage blocks once in a while.  Compitz works ok but FireFox crawls and is unuable with compitz turned on, so I have turned them off.

I just can't wait for the next version so they can get rid of these random boxes of garbage on my screen.

---

### Post by monkeytech on 2007-11-06
I am having issues after following the above post. getting missing libGL.so.1 

anyone have any ideas?

---

### Post by jetdog440 on 2007-11-06
monkey: if you're using the 64-bit version of gutsy, make SURE you patched your driver with the 64-bit debian patch to fix the symlinks... otherwise i'd check some of your libraries, and a few crazy google searches.  If you're lazy like me, go ahead an try a system wipe.  I can't tell you how many times i've had issues upgrading from pre-gutsy to gutsy.  It seems as though even an unmodified and completely upgraded version of feisty even has issues upgrading to gutsy.  I screwed up two normal feisty kernels, on compltetly different systems because they completely froze up during upgrade to gutsy... makes me wonder about a lot of things with regards to a system that was once pre-gutsy.  But yeah, i'd just wipe then you can be sure.

lachild: I can confirm the garbage... it seems to occur sometimes during normal window-switches, and either the mouse will get somewhat garbaged, or the bottom right corner gets two interesting colored lines about 100 pixels apart.  I feel the same way... been tempted to try suse, because the drivers' makers (novell) were contracted to make these new drivers (god forbid!) :-?

---

### Post by monkeytech on 2007-11-07
> **jetdog440 said:**
> monkey: if you're using the 64-bit version of gutsy, make SURE you patched your driver with the 64-bit debian patch to fix the symlinks... otherwise i'd check some of your libraries, and a few crazy google searches.  If you're lazy like me, go ahead an try a system wipe.  I can't tell you how many times i've had issues upgrading from pre-gutsy to gutsy.  It seems as though even an unmodified and completely upgraded version of feisty even has issues upgrading to gutsy.  I screwed up two normal feisty kernels, on compltetly different systems because they completely froze up during upgrade to gutsy... makes me wonder about a lot of things with regards to a system that was once pre-gutsy.  But yeah, i'd just wipe then you can be sure.


I am using 32bit version, and it was a fresh install of Gutsy, only thing i can think of was i had the gutsy restricted drivers installed when i went thought the process. i have been look around everywhere for a fix. i honsty thought they would have these driver issues sorted by now.. this laptop is over 2 years old.  my intel 945GM works soo much better then the ATI x2000m in my old mans pc. but that being said.. i even have issues with the drivers in windows also.. in fact i have ALWAYS had issues with ATI cards. and will not be going near an ATI card ever again.

cheers

---

### Post by lachild on 2007-11-09
monkeytech:  according to the [unoffical wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#libGL_error") they state the following

>  libGL error

    * fglrxinfo gives: libGL.so.1: cannot open shared object file.
    * Fixed with command: 

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1


However,  if that doesn't work I would do is this:

1) Install the Mesa Driver
2) Blacklist the restricted driver
3) REBOOT
4) Re-install the driver

BTW: Don't forget to reset the values in Xorg.conf back to allow AIGLX and add composite back in to allow for AIGLX/Compitz (we had to turn these off in older driver versions).


jetdog440:  I had no idea that Novell wrote these new drivers.  I still wouldn't switch back to SuSe just yet.  All distro's use the same X (more or less) and the same Windows Managers.  My bet is they are having the same issues in SuSe as well.

As this driver was completely redone fro this version, it's like using a 1.0 of a new program.  Bugs and more Bugs.  The next release should relieve our corrupted graphics, and of course introduce us to new bugs for awhile longer.

---

### Post by monkeytech on 2007-11-09
thanks, adding the sym link worked, i also had to add a symlink  for the fglxdri modules to get dri to work. but now all is welll.. get 1200fps glxgears. and mythtv seems to be working great now..

cheers.

---

### Post by jack handy on 2007-11-09
> **jetdog440 said:**
> 
lachild: I can confirm the garbage... it seems to occur sometimes during normal window-switches, and either the mouse will get somewhat garbaged, or the bottom right corner gets two interesting colored lines about 100 pixels apart.  I feel the same way... been tempted to try suse, because the drivers' makers (novell) were contracted to make these new drivers (god forbid!) :-?

when this happens, is there any way of getting rid of this without logging out?  its a pain in the *******.

---

### Post by lachild on 2007-11-09
Not that I know of... However it seems that the screen just needs to be redrawn.  Maybe tring to switch terminals and then back would do the trick?

Next time it happens try to hit Ctrl-Alt F1 then Ctrl-Alt F7 to retrun.  That should fix it in theory, but I havn't tried it.

---

### Post by jack handy on 2007-11-09
i'll give it a shot. should happen again soon.  i notice that whenever it happens, i get some sort of error message in the logout pertaining to fglrx, but its gone before i have time to read it properly.  where in the logs would i be able to review that error message?

---

### Post by Melcar on 2007-11-10
Those little square things that pop up every now and then around either the mouse pointer or on corners of the screen seem to go away when I open and close the CCC (odd).  OpenSuse seems to have this problem too with screen corruption, but because the CCC seems to be broken on this particular distro, that same fix doesn't work for me.

---

### Post by lachild on 2007-11-11
Looks like there's already a couple of bug reports.

[http://ati.cchtml.com/show_bug.cgi?id=859]("http://ati.cchtml.com/show_bug.cgi?id=859")
[http://ati.cchtml.com/show_bug.cgi?id=881]("http://ati.cchtml.com/show_bug.cgi?id=881")

One states that a work-around is to turn off SWCursor in xorg.conf.  Except that this option has never been turned on, on my computer (I also double checked to make sure it wasn't hiding somewhere on me).

The other possible work around is to Turn on OpenGLOverlay and Composite.  This obviously didn't fix the problem on my machine, as the settings where already turned on to run Compiz. 

While the work arounds didn't work for me, maybe they'll work for some of you.

---

### Post by jack handy on 2007-11-12
i also notice that when these errors do occur,  video playback is messed up.  i have to reboot everytime.

---

### Post by lachild on 2007-11-16
Ok tested theory and it worked for me.

When you get the random garbage on your screen switch to another termanal and then back to X.

1) Press Ctr-Alt-F1 to get to a new termanal
2) Press Ctr-Alt-F7 to get back to X.

No more garbage.


PS...  For those rebooting when you see errors or having problems with the video, a simple Crtl-Alt-Backspace will restart X without having to reboot.  (Unless of course it's hard locked)

---

### Post by jack handy on 2007-11-17
> **lachild said:**
> Ok tested theory and it worked for me.

When you get the random garbage on your screen switch to another termanal and then back to X.

1) Press Ctr-Alt-F1 to get to a new termanal
2) Press Ctr-Alt-F7 to get back to X.

No more garbage.


PS...  For those rebooting when you see errors or having problems with the video, a simple Crtl-Alt-Backspace will restart X without having to reboot.  (Unless of course it's hard locked)


works as a temporary workaround.  hopefully the folks over at ATI get this fixed sooner than later.

---

### Post by lachild on 2007-11-20
Edit:  Deleted.  Incorrect information.  Sorry - Lachild

---

### Post by stunner on 2007-11-20
Well I'll throw in my 2 cents.  I'm eager to try AIGLX  on my 200m but random garbage doesn't sound fun.  I will say that the performance in XGL/compiz is significantly better now than it was a year ago.  My main gripe is that I have to use nonXgl (search the forum) for acceptable performance in fullscreen Xv.  I figure AIGLX would take care of this but judging by this thread it looks like it's not quite there yet...

---

### Post by guris on 2007-11-23
> **stunner said:**
> Well I'll throw in my 2 cents.  I'm eager to try AIGLX  on my 200m but random garbage doesn't sound fun.  I will say that the performance in XGL/compiz is significantly better now than it was a year ago.  My main gripe is that I have to use nonXgl (search the forum) for acceptable performance in fullscreen Xv.  I figure AIGLX would take care of this but judging by this thread it looks like it's not quite there yet...

Hi guys. Almost all have been said about 200m and compiz fusion here. And   
I wanto  add my little two cents too.  Hope this will help someone :)
Abount that garbage in the down left corner of the screen, randomly appearing. It's VERY annoying, yes I had that too both in OpenSuSe 10.3 and Ubuntu Gutsy Gibbon. I've found a workaround for this while playing with Ati Catalys Control Center I pushed "Identify displays" button and "Garbage" disappeared suddenly and It never appeared since then  (Well, just couple more times only, that's all) It made me really happy, with this crappy bricks it was impossible to do anything and I had to restart X everytime. Now you no longer have to :D 

One more thing. About slow srcolling speed in FF and video in Google earth flickering, Isn't that very annoying???Yes it is.  I agree with you whoever said that this drivers are faster and "smoother" but it really better for now to stick with old fglrx driver with xgl. however, If you don't kare much about compiz this drivers are acually best drivers ati has made, because it has AIXGL support :). But those annoying "bugs" with compiz or with ati drivers really are dissappointing. However all this problems can be fixed easily by recompiling kernel to use SLAB instead of SLUB memory allocator.
Then Hibernate will work and I belive this flickering and high CPU usage will be fixed too. 
If you have Dell 1501 like m,e and you use wifi you will have to copy /lib/firmware/2.6.22-14-generic(or whatever kernel u r using/bcm433xxx_microcode11.fw
 file to /lib/firmware. 
Otherwise after recompile your wifi will not load it's firmware and it will now work. If you have different hardware than find out what firmware it uses and copy the apropriate file in the  folder mentioned above. And don't  forget to recompile/reinstall video drivers after every kernel update or recompile.  Well that's all I got to say. Right now I'm using generic ubuntu kernel with 8.42.3 drivers, with compiz disabled. I'm gonna wait for new drivers from ati, hope they will fix everything and I don't have to waist time on kernel recompaile :P Please excuse my english I'm learnin now.  GL to you all hope this will help someone. :)

---

### Post by jetdog440 on 2008-02-23
I don't know how many have been following the updated drivers (i actually had some work to do in the past three months :P).

Anyhow ati has some new drivers out for linux as of February 18th, 2008 v8.2 --> dunno what this version number means, but its recent (Yeaya!)

I'm going to manually install them again this time to make sure everything goes smoothly.

---

### Post by fracturedmorals on 2008-02-23
> **goodguy20k said:**
> Ok, so here's the deal: I couldn't wait for the latest and greatest. ;)

So my setup is a Compaq R4000, which has an AMD Athlon 64-bit, but I'm running 32-bit Gutsy Gibbon, released edition. When I used the fglrx (ATI proprietary) 8.40.X, desktop effects wouldn't work. "No composite".

Nothing new, so I waited for 8.42.3. It has the composite built in, right? Great, right?

I installed it, enabled the composite in "/etc/X11/xorg.conf", and white listed the fglrx driver in Compiz. Click the radio button and... Nothing. Could not start the effects, it says. I proceeded to grumble. :P

Then I opened a terminal and ran "compiz". "Blacklisted PCIID '1002:5955' found" was the result of the command. Yes, I know I have a pathetic version of an ATI card. (Somewhere I read it's the r480 family GPU, I think?) A little googlin' and... I found how to get around the black list: "SKIP_CHECKS=yes compiz". And...

White screen! It all looked like it was working well, and then it shows completely white, plus the mouse cursor. O_O Yes, I could move the cursor around the screen, and it changed per window below it, that I could not see. I could even click back into the terminal and CTRL+C Compiz out. It's a step in the right direction, I think, but... I'm not sure which way to head now. Any thoughts?

Really quick solution;

1. FIRST THING: Revert your /etc/X11/xorg.conf back to default:
```
sudo dpkg-reconfigure xserver-xorg
```

2. Install XGL (The 200m has ALWAYS been buggy....I used to run it on an Acer laptop and it gace me headaches.....bad ones.....)
```
sudo apt-get install xserver-xgl
```

3. Log out.

4. Log back in

5. Turn on desktop effects to desired level.

6. Shake your fists at the sky and curse ATI for not better supporting DRI

---

### Post by jetdog440 on 2008-02-25
fracturedmorals: I'd check to see if the driver you have installed actually supports direct rendering.  That would easily explain why your getting all white.

glxinfo | grep render

If it says direct rendering : no , then your probably using the wrong driver, or the restricted driver manager is interfering with your driver (perhaps you have the ubuntu-recommended driver installed?  In my system i have it displaying "Enabled = No, In Use? = Yes... this is in the restricted drivers manager).  I had the same problem earlier for a while now... it seems ubuntu's restricted driver manager offers a little bit more confusion to our already messy situation with the x200m.

Best of Luck.

---

### Post by jetdog440 on 2008-02-25
Great news to all!  Try the ati-driver-installer 8-01 !  It has a number of issues resolved.  I'm already had it working like charm and i didn't even have to do anything crazy to compile it into the kernel!  (just make sure you delete the sources of the old ones in your kernel source folder before you install any new ones).

HOWEVER, do NOT use the drivers from February 2008.  Their 3d acceleration is BROKEN ( i tried it and it gives me funky pieces of 3d dispersed evenly into sections across my screen ).

Anyhow, im currently going nuts installing kde 4.0 from the official repositories there, then compiz with the full control panel, with ati-driver-installer 8-01 from January 2008. (I will report any interesting findings if its not worth it yet here).  If i get the proper cube effects and video rendering on the cube with this setup, i will report my findings here.

---

