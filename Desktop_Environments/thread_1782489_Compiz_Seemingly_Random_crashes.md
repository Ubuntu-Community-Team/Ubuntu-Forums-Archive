---
title: "Compiz Seemingly Random crashes"
date: 2011-06-14
forum: Desktop Environments
---

### Post by cm0n3y34 on 2011-06-14
Compiz crashes and restarts very frequently. It is annoying, but I can't give up the animations and such. 
I have tried purging compiz, all plugins, fusion icon, and emerald and reinstalling, but that didn't fix it. I also tried indirect rendering, to no avail.  If anyone can help me it would be REALLY appreciated! 

I ran compiz --replace from a terminal, and got this when it eventually crashes:
glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: vector::_M_fill_insert

Here is the terminal output:
cm0n3y34 Tue Jun 14 16:13:36 EDT 2011
[~] compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
 ---- Many "Window created on XQueryTree, map state isViewable? 1" or "0" s
Initializing crashhandler options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing place options...done
Initializing grid options...done
Initializing titleinfo options...done
Initializing imgjpeg options...done
Initializing move options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing debugspew options...done
Initializing mousepoll options...done
compiz (core) - Error: Plugin 'text' not loaded.

compiz (shift) - Warn: No compatible text plugin loaded
Initializing shift options...done
Initializing vpswitch options...done
Initializing resize options...done
compiz (core) - Error: Plugin 'text' not loaded.

Initializing thumbnail options...done
Initializing animation options...done
Initializing wall options...done
Initializing workarounds options...done
Initializing wobbly options...done
Initializing animationaddon options...[ERROR]: Option "time_step_intense" already defined
[ERROR]: Option "airplane_path_length" already defined
[ERROR]: Option "airplane_fly_to_taskbar" already defined
[ERROR]: Option "beam_size" already defined
[ERROR]: Option "beam_spacing" already defined
[ERROR]: Option "beam_color" already defined
[ERROR]: Option "beam_slowdown" already defined
[ERROR]: Option "beam_life" already defined
[ERROR]: Option "fire_particles" already defined
[ERROR]: Option "fire_size" already defined
[ERROR]: Option "fire_slowdown" already defined
[ERROR]: Option "fire_life" already defined
[ERROR]: Option "fire_color" already defined
[ERROR]: Option "fire_direction" already defined
[ERROR]: Option "fire_constant_speed" already defined
[ERROR]: Option "fire_smoke" already defined
[ERROR]: Option "fire_mystical" already defined
[ERROR]: Option "domino_direction" already defined
[ERROR]: Option "explode_gridx" already defined
[ERROR]: Option "explode_gridy" already defined
[ERROR]: Option "explode_spokes" already defined
[ERROR]: Option "explode_tiers" already defined
[ERROR]: Option "explode_thickness" already defined
[ERROR]: Option "explode_tessellation" already defined
[ERROR]: Option "fold_gridx" already defined
[ERROR]: Option "fold_gridy" already defined
[ERROR]: Option "fold_dir" already defined
[ERROR]: Option "glide3_away_position" already defined
[ERROR]: Option "glide3_away_angle" already defined
[ERROR]: Option "glide3_thickness" already defined
[ERROR]: Option "razr_direction" already defined
[ERROR]: Option "skewer_direction" already defined
[ERROR]: Option "skewer_tessellation" already defined
[ERROR]: Option "skewer_gridx" already defined
[ERROR]: Option "skewer_gridy" already defined
[ERROR]: Option "skewer_thickness" already defined
[ERROR]: Option "skewer_rotation" already defined
done
Initializing animationplus options...done
Initializing mag options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done
Setting Update "directory"
Setting Update "shadow_x_offset"
Setting Update "shadow_y_offset"
Setting Update "command"
Setting Update "top_left_corner_action"
Setting Update "top_right_corner_action"
Setting Update "bottom_edge_action"
Setting Update "outline_color"
Setting Update "fill_color"
Setting Update "behind_window"
Setting Update "run_command_terminal_key"
Setting Update "initiate_key"
Setting Update "shift_speed"
Setting Update "size"
Setting Update "background_intensity"
Setting Update "ground_color1"
Setting Update "ground_size"
Setting Update "intensity"
Setting Update "flip_rotation"
Setting Update "cover_offset"
Setting Update "cover_angle"
Setting Update "cover_max_visible_windows"
Setting Update "multioutput_mode"
Setting Update "title_font_bold"
Setting Update "title_text_placement"
Setting Update "border_color"
Setting Update "fill_color"
Setting Update "open_effects"
Setting Update "open_durations"
Setting Update "close_effects"
Setting Update "close_durations"
Setting Update "minimize_effects"
Setting Update "minimize_durations"
Setting Update "focus_effects"
Setting Update "focus_durations"
Setting Update "time_step"
Setting Update "friction"
Setting Update "spring_k"
Setting Update "beam_life"
Setting Update "fire_particles"
Setting Update "fire_slowdown"
Setting Update "fire_life"
Setting Update "fire_color"
Setting Update "explode_gridx"
Setting Update "explode_spokes"
Setting Update "explode_thickness"
Setting Update "explode_tessellation"
Setting Update "skewer_direction"
Setting Update "skewer_gridx"
Setting Update "skewer_gridy"
Setting Update "skewer_thickness"
Setting Update "skewer_rotation"
Setting Update "zoom_factor"
Setting Update "speed"
Setting Update "keep_screen"
Setting Update "box_width"
Setting Update "box_height"
Setting Update "border"
Setting Update "x_offset"
Setting Update "y_offset"
Setting Update "radius"
Setting Update "next_key"
Setting Update "prev_key"
Setting Update "fullscreen_visual_bell"
Setting Update "unresponsive_brightness"
Window 0x4010156 created on ReparentNotify, map state isViewable? 0
Window 0x4010218 created on ReparentNotify, map state isViewable? 0

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: vector::_M_fill_insert

aborting...
Reading symbols from /usr/bin/compiz...(no debugging symbols found)...done.
Attaching to program: /usr/bin/compiz, process 7493
Reading symbols from /usr/lib/x86_64-linux-gnu/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXdamage.so.1
Reading symbols from /usr/lib/x86_64-linux-gnu/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXfixes.so.3
Reading symbols from /usr/lib/x86_64-linux-gnu/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXcomposite.so.1
Reading symbols from /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1
Reading symbols from /usr/lib/x86_64-linux-gnu/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libX11.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libxcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libxcb.so.1
Reading symbols from /usr/lib/x86_64-linux-gnu/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXrandr.so.2
Reading symbols from /usr/lib/x86_64-linux-gnu/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXinerama.so.1
Reading symbols from /usr/lib/x86_64-linux-gnu/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXext.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libICE.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libSM.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
Reading symbols from /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libglibmm-2.4.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglibmm-2.4.so.1
Reading symbols from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
Reading symbols from /usr/lib/libsigc-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsigc-2.0.so.0
Reading symbols from /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0
Reading symbols from /lib/x86_64-linux-gnu/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/librt.so.1
Reading symbols from /lib/x86_64-linux-gnu/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libglib-2.0.so.0
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libboost_serialization.so.1.42.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libboost_serialization.so.1.42.0
Reading symbols from /lib/x86_64-linux-gnu/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0x7fea69dde700 (LWP 7495)]
Loaded symbols for /lib/x86_64-linux-gnu/libpthread.so.0
Reading symbols from /lib/x86_64-linux-gnu/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libdl.so.2
Reading symbols from /usr/lib/x86_64-linux-gnu/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libstdc++.so.6
Reading symbols from /lib/x86_64-linux-gnu/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libm.so.6
Reading symbols from /lib/x86_64-linux-gnu/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libgcc_s.so.1
Reading symbols from /lib/x86_64-linux-gnu/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libc.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXau.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXdmcp.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXrender.so.1
Reading symbols from /lib/x86_64-linux-gnu/libuuid.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libuuid.so.1
Reading symbols from /lib/x86_64-linux-gnu/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libz.so.1
Reading symbols from /lib/x86_64-linux-gnu/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libpcre.so.3
Reading symbols from /lib/x86_64-linux-gnu/libresolv.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libresolv.so.2
Reading symbols from /lib/x86_64-linux-gnu/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libselinux.so.1
Reading symbols from /lib64/ld-linux-x86-64.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Reading symbols from /usr/lib/libxcb-aux.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-aux.so.0
Reading symbols from /usr/lib/libxcb-event.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-event.so.1
Reading symbols from /usr/lib/libxcb-atom.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-atom.so.1
Reading symbols from /usr/lib/compiz/libccp.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/libprotobuf.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libprotobuf.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libXcursor.so.1
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /lib/x86_64-linux-gnu/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_compat.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnsl.so.1
Reading symbols from /lib/x86_64-linux-gnu/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_nis.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libbailer.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libbailer.so
Reading symbols from /usr/lib/compiz/libdetection.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdetection.so
Reading symbols from /usr/lib/compiz/libcomposite.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcomposite.so
Reading symbols from /usr/lib/compiz/libopengl.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libopengl.so
Reading symbols from /usr/lib/nvidia-current/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current/libGL.so.1
Reading symbols from /usr/lib/nvidia-current/tls/libnvidia-tls.so.270.41.06...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current/tls/libnvidia-tls.so.270.41.06
Reading symbols from /usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06
Reading symbols from /usr/lib/compiz/libdecor.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecor.so
Reading symbols from /usr/lib/libdecoration.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libcompiztoolbox.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcompiztoolbox.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libgrid.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgrid.so
Reading symbols from /usr/lib/compiz/libtitleinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtitleinfo.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/x86_64-linux-gnu/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libsession.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libgnomecompat.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgnomecompat.so
Reading symbols from /usr/lib/compiz/libdebugspew.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdebugspew.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libshift.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libtext.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/x86_64-linux-gnu/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libfreetype.so.6
Reading symbols from /usr/lib/x86_64-linux-gnu/libfontconfig.so.1...(no debugging symbols found)...doUndefined command: "-e".  Try "help".
ne.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libfontconfig.so.1
Reading symbols from /usr/lib/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /lib/x86_64-linux-gnu/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libpng12.so.0
Reading symbols from /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0
Reading symbols from /usr/lib/x86_64-linux-gnu/libxcb-render.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/x86_64-linux-gnu/libxcb-render.so.0
Reading symbols from /lib/x86_64-linux-gnu/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libexpat.so.1
Reading symbols from /usr/lib/compiz/libvpswitch.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libimgpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgpng.so
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libregex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libwall.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwall.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libwobbly.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libanimationaddon.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimationaddon.so
Reading symbols from /home/cm0n3y34/.compiz-1/plugins/libanimationplus.so...done.
Loaded symbols for /home/cm0n3y34/.compiz-1/plugins/libanimationplus.so
Reading symbols from /usr/lib/compiz/libmag.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmag.so
Reading symbols from /usr/lib/compiz/libexpo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libezoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/compiz/libstaticswitcher.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libstaticswitcher.so
Reading symbols from /usr/lib/compiz/libfade.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libscale.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
0x00007fea6c53b1ed in waitpid () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) (gdb) 
Thread 2 (Thread 0x7fea69dde700 (LWP 7495)):
#0  0x00007fea6c566f03 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007fea6d8a2104 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007fea6d8a29f2 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007fea6e8cdc44 in ?? () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#4  0x00007fea6d8c93e4 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007fea6d1cdd8c in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#6  0x00007fea6c57404d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fea70a5d820 (LWP 7493)):
#0  0x00007fea6c53b1ed in waitpid () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007fea6c4cfd6e in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007fea6c4d0180 in system () from /lib/x86_64-linux-gnu/libc.so.6
#3  0x00007fea68b9d610 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0x00007fea6c4c1d05 in raise () from /lib/x86_64-linux-gnu/libc.so.6
#6  0x00007fea6c4c5ab6 in abort () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x00007fea6d8aaa22 in g_logv () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#8  0x00007fea6d8aaaaf in g_log () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#9  0x00007fea6e3f27cb in Glib::exception_handlers_invoke() () from /usr/lib/libglibmm-2.4.so.1
#10 0x00007fea6e3f2dee in Glib::Source::dispatch_vfunc(_GSource*, int (*)(void*), void*) () from /usr/lib/libglibmm-2.4.so.1
#11 0x00007fea6d8a1bcd in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#12 0x00007fea6d8a23a8 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#13 0x00007fea6d8a29f2 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#14 0x000000000042a2ea in CompScreen::eventLoop() ()
#15 0x0000000000423160 in main ()
(gdb) 
(gdb) 
(gdb) #0  0x00007fea6c53b1ed in waitpid () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007fea6c4cfd6e in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007fea6c4d0180 in system () from /lib/x86_64-linux-gnu/libc.so.6
#3  0x00007fea68b9d610 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0x00007fea6c4c1d05 in raise () from /lib/x86_64-linux-gnu/libc.so.6
#6  0x00007fea6c4c5ab6 in abort () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x00007fea6d8aaa22 in g_logv () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#8  0x00007fea6d8aaaaf in g_log () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#9  0x00007fea6e3f27cb in Glib::exception_handlers_invoke() () from /usr/lib/libglibmm-2.4.so.1
#10 0x00007fea6e3f2dee in Glib::Source::dispatch_vfunc(_GSource*, int (*)(void*), void*) () from /usr/lib/libglibmm-2.4.so.1
#11 0x00007fea6d8a1bcd in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#12 0x00007fea6d8a23a8 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#13 0x00007fea6d8a29f2 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#14 0x000000000042a2ea in CompScreen::eventLoop() ()
#15 0x0000000000423160 in main ()
(gdb) A debugging session is active.

    Inferior 1 [process 7493] will be detached.

Quit anyway? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz, process 7493

[CRASH_HANDLER]: "/home/cm0n3y34/compizcrashes//compiz_crash-7493.out" created!

---

### Post by ivanovnegro on 2011-06-14
Ok, I am not to an expert to read all your output here, but maybe the problem is with your video card, which one do you use?

---

### Post by cm0n3y34 on 2011-06-14
Nvidia GEforce 8800GT, it DOES have memory corruption very rarely, causing random patterns and colors on the screen, requiring a reboot. but I haven't seen that in ~3 months. And I have no $ for a new card so for me its that or intel onboard)

It started happening after converting back to Ubuntu from Kubuntu (removing all kubuntu packages, and reinstalling the ubuntu-desktop metapackage), and started using compiz + emerald.  

Is there a configuration file for compiz that I can backup and delete, so I can see if that fixes it?

---

### Post by ivanovnegro on 2011-06-14
Do you use the open source driver or the proprietary one for your card?

---

### Post by cm0n3y34 on 2011-06-14
Proprietary. The "version current", not "173"
but it says "this driver is activated but not currently in use.", and has a green light. o_O

---

### Post by cm0n3y34 on 2011-06-14
I'm cosidering doing a complete reinstall again, but I don't want to. (3rd time in 4 months, first 2 were dependency hell, last one was the update from 10.10 to 11.04, left me in initramfs command line.)

---

### Post by ivanovnegro on 2011-06-14
The problem is 11.04 simply does not play well on some hardware. I would gladly help you more but I think I have no more ideas.
You could try Gnome Classic or even better in my opinion 10.10 and wait for 11.10.

---

### Post by cm0n3y34 on 2011-06-14
I am using classic (I don't like how uncustomizable unity is right now)
I might downgrade tomorrow, or even tonight... At least when I was on that version, the need to reinstall was 100% my fault (for breaking the dependencies)

---

### Post by ivanovnegro on 2011-06-14
You could also use Gnome Classic without effects.

---

### Post by cm0n3y34 on 2011-06-14
I LOVE the effects (and showing them off to my windows and mac using friends XD)
Ehh, I guess I will just reinstall, there are a few other issues, and I don't want to bother trying to figure it all out, only to have something else break because of my "fixes". 

Thanks for your help! (is there a thanks button in this forum?)

---

### Post by ivanovnegro on 2011-06-14
:D. No, but you could make the thread as solved, if you think so.

---

