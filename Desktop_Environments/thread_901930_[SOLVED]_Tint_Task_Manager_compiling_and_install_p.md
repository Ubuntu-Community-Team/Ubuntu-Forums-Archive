---
title: "[SOLVED] Tint Task Manager compiling and install problems"
date: 2008-08-26
forum: Desktop Environments
---

### Post by mp3_freak_721 on 2008-08-26
I am having issues install the new ttm 0.6. When I try to compile  the program following the instructions I get an error:

make: *** [tint] Error 1

and there are alot more errors before that. Could someone help me because I don't want to use pypanel any more and want to try ttm. Thanks in advance.

---

### Post by thil77 on 2008-08-27
you can try this binary package
[http://ubuntuforums.org/showpost.php?p=5431755&postcount=74](http://ubuntuforums.org/showpost.php?p=5431755&postcount=74)

---

### Post by mp3_freak_721 on 2008-08-27
Ok. I tried the binary package and that didn't want to install either. Any more ideas? I'm kind of mad at my computer for not wanting to let me install tint. :confused:

---

### Post by thil77 on 2008-08-27
not sure i can help, 
but if you want better support send more valuable information.

if you want help to install from source, cut and paste all error message
because "make: *** [tint] Error 1" doesn't give enough information.

if you want help with binary package, explain what you try and what is the result. 
because "didn't want to install either" doesn't give enough information.

---

### Post by mp3_freak_721 on 2008-08-27
Well here what it says when I try to compile from source:

```
cc  -Wall -g `pkg-config --cflags --libs cairo pangocairo x11 xinerama imlib2 glib-2.0` -o tint tint.c server.c window.c task.c launcher.c visual.c config.c
Package imlib2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `imlib2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'imlib2' found
tint.c:38:20: error: Imlib2.h: No such file or directory
In file included from tint.c:42:
config.h:5:30: error: pango/pangocairo.h: No such file or directory
In file included from tint.c:42:
config.h:84: error: expected specifier-qualifier-list before ‘PangoFontDescription’
tint.c: In function ‘init’:
tint.c:79: warning: implicit declaration of function ‘imlib_context_set_display’
tint.c:80: warning: implicit declaration of function ‘imlib_context_set_visual’
tint.c:81: warning: implicit declaration of function ‘imlib_context_set_colormap’
tint.c: In function ‘event_button_release’:
tint.c:126: error: ‘Panel’ has no member named ‘mouse_middle’
tint.c:129: error: ‘Panel’ has no member named ‘mouse_right’
tint.c:132: error: ‘Panel’ has no member named ‘mouse_scroll_up’
tint.c:135: error: ‘Panel’ has no member named ‘mouse_scroll_down’
tint.c: In function ‘event_property_notify’:
tint.c:228: error: ‘Panel’ has no member named ‘redraw_clock’
tint.c: In function ‘event_timer’:
tint.c:291: error: ‘Panel’ has no member named ‘time1_format’
tint.c:295: error: ‘Panel’ has no member named ‘clock’
tint.c:295: error: ‘Panel’ has no member named ‘time_precision’
tint.c:298: error: ‘Panel’ has no member named ‘clock’
tint.c:299: error: ‘Panel’ has no member named ‘clock’
tint.c:299: error: ‘Panel’ has no member named ‘clock’
tint.c:299: error: ‘Panel’ has no member named ‘time_precision’
tint.c:300: error: ‘Panel’ has no member named ‘redraw_clock’
In file included from server.c:36:
config.h:5:30: error: pango/pangocairo.h: No such file or directory
In file included from server.c:36:
config.h:84: error: expected specifier-qualifier-list before ‘PangoFontDescription’
server.c: In function ‘get_property32’:
server.c:119: error: ‘gulong’ undeclared (first use in this function)
server.c:119: error: (Each undeclared identifier is reported only once
server.c:119: error: for each function it appears in.)
server.c:119: error: expected expression before ‘)’ token
window.c:35:20: error: Imlib2.h: No such file or directory
In file included from window.c:39:
config.h:5:30: error: pango/pangocairo.h: No such file or directory
In file included from window.c:39:
config.h:84: error: expected specifier-qualifier-list before ‘PangoFontDescription’
window.c: In function ‘set_panel_properties’:
window.c:318: error: ‘gsize’ undeclared (first use in this function)
window.c:318: error: (Each undeclared identifier is reported only once
window.c:318: error: for each function it appears in.)
window.c:318: error: expected ‘;’ before ‘len’
window.c:319: error: ‘gchar’ undeclared (first use in this function)
window.c:319: error: ‘name’ undeclared (first use in this function)
window.c:319: warning: implicit declaration of function ‘g_locale_to_utf8’
window.c:319: error: ‘len’ undeclared (first use in this function)
window.c:322: warning: implicit declaration of function ‘g_free’
task.c:35:18: error: glib.h: No such file or directory
In file included from task.c:39:
config.h:5:30: error: pango/pangocairo.h: No such file or directory
In file included from task.c:39:
config.h:84: error: expected specifier-qualifier-list before ‘PangoFontDescription’
task.c: In function ‘resize_tasks’:
task.c:207: error: ‘Panel’ has no member named ‘task_border’
visual.c:34:19: error: cairo.h: No such file or directory
visual.c:35:24: error: cairo-xlib.h: No such file or directory
visual.c:36:30: error: pango/pangocairo.h: No such file or directory
visual.c:39:20: error: Imlib2.h: No such file or directory
In file included from visual.c:42:
config.h:84: error: expected specifier-qualifier-list before ‘PangoFontDescription’
visual.c: In function ‘visual_refresh’:
visual.c:56: error: ‘Panel’ has no member named ‘time1_format’
visual.c:57: error: ‘Panel’ has no member named ‘redraw_clock’
visual.c:59: error: ‘Panel’ has no member named ‘pmap_clock’
visual.c:59: error: ‘Panel’ has no member named ‘clock_width’
visual.c:59: error: ‘Panel’ has no member named ‘clock_height’
visual.c:59: error: ‘Panel’ has no member named ‘clock_posx’
visual.c:59: error: ‘Panel’ has no member named ‘clock_posy’
visual.c: In function ‘draw_task_icon’:
visual.c:101: error: ‘Panel’ has no member named ‘task_border’
visual.c:105: error: ‘Imlib_Image’ undeclared (first use in this function)
visual.c:105: error: (Each undeclared identifier is reported only once
visual.c:105: error: for each function it appears in.)
visual.c:105: error: expected ‘;’ before ‘icon’
visual.c:106: error: ‘Imlib_Color_Modifier’ undeclared (first use in this function)
visual.c:106: error: expected ‘;’ before ‘cmod’
visual.c:107: error: ‘DATA8’ undeclared (first use in this function)
visual.c:107: error: expected ‘;’ before ‘red’
visual.c:110: error: ‘DATA32’ undeclared (first use in this function)
visual.c:110: error: ‘data’ undeclared (first use in this function)
visual.c:119: error: expected expression before ‘)’ token
visual.c:121: error: ‘icon’ undeclared (first use in this function)
visual.c:121: warning: implicit declaration of function ‘imlib_create_image_using_data’
visual.c:122: warning: implicit declaration of function ‘imlib_context_set_image’
visual.c:123: warning: implicit declaration of function ‘imlib_context_set_drawable’
visual.c:125: error: ‘cmod’ undeclared (first use in this function)
visual.c:125: warning: implicit declaration of function ‘imlib_create_color_modifier’
visual.c:126: warning: implicit declaration of function ‘imlib_context_set_color_modifier’
visual.c:127: warning: implicit declaration of function ‘imlib_image_set_has_alpha’
visual.c:128: warning: implicit declaration of function ‘imlib_get_color_modifier_tables’
visual.c:128: error: ‘red’ undeclared (first use in this function)
visual.c:128: error: ‘green’ undeclared (first use in this function)
visual.c:128: error: ‘blue’ undeclared (first use in this function)
visual.c:128: error: ‘alpha’ undeclared (first use in this function)
visual.c:136: warning: implicit declaration of function ‘imlib_set_color_modifier_tables’
visual.c:139: warning: implicit declaration of function ‘imlib_render_image_on_drawable_at_size’
visual.c:141: warning: implicit declaration of function ‘imlib_free_color_modifier’
visual.c:142: warning: implicit declaration of function ‘imlib_free_image’
visual.c: At top level:
visual.c:147: error: expected ‘)’ before ‘*’ token
visual.c:190: error: expected ‘)’ before ‘*’ token
visual.c:210: error: expected ‘)’ before ‘*’ token
visual.c: In function ‘draw_panel_background’:
visual.c:247: error: ‘cairo_surface_t’ undeclared (first use in this function)
visual.c:247: error: ‘cs’ undeclared (first use in this function)
visual.c:248: error: ‘cairo_t’ undeclared (first use in this function)
visual.c:248: error: ‘c’ undeclared (first use in this function)
visual.c:251: warning: implicit declaration of function ‘cairo_xlib_surface_create’
visual.c:252: warning: implicit declaration of function ‘cairo_create’
visual.c:258: warning: implicit declaration of function ‘draw_rect’
visual.c:260: warning: implicit declaration of function ‘cairo_set_source_rgba’
visual.c:262: warning: implicit declaration of function ‘cairo_fill’
visual.c:265: warning: implicit declaration of function ‘cairo_set_line_width’
visual.c:272: warning: implicit declaration of function ‘cairo_stroke’
visual.c:275: warning: implicit declaration of function ‘cairo_destroy’
visual.c:276: warning: implicit declaration of function ‘cairo_surface_destroy’
visual.c: In function ‘redraw_task’:
visual.c:282: error: ‘cairo_surface_t’ undeclared (first use in this function)
visual.c:282: error: ‘cs’ undeclared (first use in this function)
visual.c:283: error: ‘cairo_t’ undeclared (first use in this function)
visual.c:283: error: ‘c’ undeclared (first use in this function)
visual.c:302: warning: implicit declaration of function ‘draw_task_background’
visual.c:303: warning: implicit declaration of function ‘draw_task_title’
visual.c: In function ‘redraw_clock’:
visual.c:326: error: ‘cairo_surface_t’ undeclared (first use in this function)
visual.c:326: error: ‘cs’ undeclared (first use in this function)
visual.c:327: error: ‘cairo_t’ undeclared (first use in this function)
visual.c:327: error: ‘c’ undeclared (first use in this function)
visual.c:328: error: ‘PangoLayout’ undeclared (first use in this function)
visual.c:328: error: ‘layout’ undeclared (first use in this function)
visual.c:333: warning: implicit declaration of function ‘strftime’
visual.c:333: warning: incompatible implicit declaration of built-in function ‘strftime’
visual.c:333: error: ‘Panel’ has no member named ‘time1_format’
visual.c:333: warning: implicit declaration of function ‘localtime’
visual.c:333: error: ‘Panel’ has no member named ‘clock’
visual.c:333: warning: passing argument 4 of ‘strftime’ makes pointer from integer without a cast
visual.c:334: error: ‘Panel’ has no member named ‘time2_format’
visual.c:335: error: ‘Panel’ has no member named ‘time2_format’
visual.c:335: error: ‘Panel’ has no member named ‘clock’
visual.c:335: warning: passing argument 4 of ‘strftime’ makes pointer from integer without a cast
visual.c:338: error: ‘Panel’ has no member named ‘pmap_clock’
visual.c:338: error: ‘Panel’ has no member named ‘pmap_clock’
visual.c:339: error: ‘Panel’ has no member named ‘pmap_clock’
visual.c:339: error: ‘Panel’ has no member named ‘clock_width’
visual.c:339: error: ‘Panel’ has no member named ‘clock_height’
visual.c:341: error: ‘Panel’ has no member named ‘pmap_clock’
visual.c:341: error: ‘Panel’ has no member named ‘clock_posx’
visual.c:341: error: ‘Panel’ has no member named ‘clock_posy’
visual.c:341: error: ‘Panel’ has no member named ‘clock_width’
visual.c:341: error: ‘Panel’ has no member named ‘clock_height’
visual.c:343: error: ‘Panel’ has no member named ‘pmap_clock’
visual.c:343: error: ‘Panel’ has no member named ‘clock_width’
visual.c:343: error: ‘Panel’ has no member named ‘clock_height’
visual.c:345: warning: implicit declaration of function ‘pango_cairo_create_layout’
visual.c:348: warning: implicit declaration of function ‘pango_layout_set_font_description’
visual.c:348: error: ‘Panel’ has no member named ‘time1_font_desc’
visual.c:349: warning: implicit declaration of function ‘pango_layout_set_indent’
visual.c:350: warning: implicit declaration of function ‘pango_layout_set_text’
visual.c:351: warning: implicit declaration of function ‘pango_layout_get_pixel_size’
visual.c:352: error: ‘Panel’ has no member named ‘time2_format’
visual.c:353: error: ‘Panel’ has no member named ‘time2_font_desc’
visual.c:358: error: ‘Panel’ has no member named ‘clock_width’
visual.c:358: error: ‘Panel’ has no member named ‘clock_width’
visual.c:363: warning: implicit declaration of function ‘g_object_unref’
visual.c:372: error: ‘Panel’ has no member named ‘time1_font_desc’
visual.c:373: warning: implicit declaration of function ‘pango_layout_set_width’
visual.c:373: error: ‘Panel’ has no member named ‘clock_width’
visual.c:373: error: ‘PANGO_SCALE’ undeclared (first use in this function)
visual.c:374: warning: implicit declaration of function ‘pango_layout_set_alignment’
visual.c:374: error: ‘PANGO_ALIGN_CENTER’ undeclared (first use in this function)
visual.c:377: error: ‘Panel’ has no member named ‘clock_font’
visual.c:377: error: ‘Panel’ has no member named ‘clock_font’
visual.c:377: error: ‘Panel’ has no member named ‘clock_font’
visual.c:377: error: ‘Panel’ has no member named ‘clock_font’
visual.c:379: warning: implicit declaration of function ‘pango_cairo_update_layout’
visual.c:380: warning: implicit declaration of function ‘cairo_move_to’
visual.c:380: error: ‘Panel’ has no member named ‘time1_posy’
visual.c:381: warning: implicit declaration of function ‘pango_cairo_show_layout’
visual.c:383: error: ‘Panel’ has no member named ‘time2_format’
visual.c:384: error: ‘Panel’ has no member named ‘time2_font_desc’
visual.c:387: error: ‘Panel’ has no member named ‘clock_width’
visual.c:390: error: ‘Panel’ has no member named ‘time2_posy’
visual.c:397: error: ‘Panel’ has no member named ‘redraw_clock’
visual.c: In function ‘resize_clock’:
visual.c:404: error: ‘Panel’ has no member named ‘clock_width’
visual.c:405: error: ‘Panel’ has no member named ‘clock_posx’
visual.c: In function ‘resize_taskbar’:
visual.c:417: error: ‘Panel’ has no member named ‘launcher_width’
visual.c:418: error: ‘Panel’ has no member named ‘time1_format’
visual.c:419: error: ‘Panel’ has no member named ‘clock_width’
config.c:32:19: error: cairo.h: No such file or directory
config.c:33:24: error: cairo-xlib.h: No such file or directory
config.c:41:25: error: glib/gstdio.h: No such file or directory
config.c:42:30: error: pango/pangocairo.h: No such file or directory
config.c:43:20: error: Imlib2.h: No such file or directory
In file included from config.c:45:
config.h:84: error: expected specifier-qualifier-list before ‘PangoFontDescription’
config.c: In function ‘cleanup’:
config.c:72: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:72: warning: implicit declaration of function ‘pango_font_description_free’
config.c:72: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:73: error: ‘Panel’ has no member named ‘time1_font_desc’
config.c:73: error: ‘Panel’ has no member named ‘time1_font_desc’
config.c:74: error: ‘Panel’ has no member named ‘time2_font_desc’
config.c:74: error: ‘Panel’ has no member named ‘time2_font_desc’
config.c:76: error: ‘Panel’ has no member named ‘time1_format’
config.c:76: warning: implicit declaration of function ‘g_free’
config.c:76: error: ‘Panel’ has no member named ‘time1_format’
config.c:77: error: ‘Panel’ has no member named ‘time2_format’
config.c:77: error: ‘Panel’ has no member named ‘time2_format’
config.c: At top level:
config.c:83: error: expected ‘)’ before ‘*’ token
config.c: In function ‘extract_values’:
config.c:137: warning: implicit declaration of function ‘g_strstrip’
config.c: In function ‘add_entry’:
config.c:221: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:221: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:222: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:222: warning: implicit declaration of function ‘pango_font_description_from_string’
config.c:226: error: ‘Panel’ has no member named ‘task_font’
config.c:227: error: ‘Panel’ has no member named ‘task_font’
config.c:228: error: ‘Panel’ has no member named ‘task_font’
config.c:232: error: ‘Panel’ has no member named ‘task_font_active’
config.c:233: error: ‘Panel’ has no member named ‘task_font_active’
config.c:234: error: ‘Panel’ has no member named ‘task_font_active’
config.c:281: error: ‘Panel’ has no member named ‘time1_format’
config.c:281: error: ‘Panel’ has no member named ‘time1_format’
config.c:282: error: ‘Panel’ has no member named ‘time1_format’
config.c:283: error: ‘Panel’ has no member named ‘time1_format’
config.c:286: error: ‘Panel’ has no member named ‘time2_format’
config.c:286: error: ‘Panel’ has no member named ‘time2_format’
config.c:287: error: ‘Panel’ has no member named ‘time2_format’
config.c:288: error: ‘Panel’ has no member named ‘time2_format’
config.c:291: error: ‘Panel’ has no member named ‘time1_font_desc’
config.c:291: error: ‘Panel’ has no member named ‘time1_font_desc’
config.c:292: error: ‘Panel’ has no member named ‘time1_font_desc’
config.c:295: error: ‘Panel’ has no member named ‘time2_font_desc’
config.c:295: error: ‘Panel’ has no member named ‘time2_font_desc’
config.c:296: error: ‘Panel’ has no member named ‘time2_font_desc’
config.c:300: error: ‘Panel’ has no member named ‘clock_font’
config.c:301: error: ‘Panel’ has no member named ‘clock_font’
config.c:302: error: ‘Panel’ has no member named ‘clock_font’
config.c:338: error: ‘Panel’ has no member named ‘task_back’
config.c:339: error: ‘Panel’ has no member named ‘task_back’
config.c:340: error: ‘Panel’ has no member named ‘task_back’
config.c:344: error: ‘Panel’ has no member named ‘task_active_back’
config.c:345: error: ‘Panel’ has no member named ‘task_active_back’
config.c:346: error: ‘Panel’ has no member named ‘task_active_back’
config.c:350: error: ‘Panel’ has no member named ‘task_border’
config.c:351: error: ‘Panel’ has no member named ‘task_active_border’
config.c:354: error: ‘Panel’ has no member named ‘task_border’
config.c:355: error: ‘Panel’ has no member named ‘task_active_border’
config.c:359: error: ‘Panel’ has no member named ‘task_border’
config.c:360: error: ‘Panel’ has no member named ‘task_border’
config.c:361: error: ‘Panel’ has no member named ‘task_border’
config.c:365: error: ‘Panel’ has no member named ‘task_active_border’
config.c:366: error: ‘Panel’ has no member named ‘task_active_border’
config.c:367: error: ‘Panel’ has no member named ‘task_active_border’
config.c:372: error: ‘Panel’ has no member named ‘mouse_middle’
config.c:374: error: ‘Panel’ has no member named ‘mouse_right’
config.c:376: error: ‘Panel’ has no member named ‘mouse_scroll_up’
config.c:378: error: ‘Panel’ has no member named ‘mouse_scroll_down’
config.c:391: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:391: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:392: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:397: error: ‘Panel’ has no member named ‘task_font’
config.c:399: error: ‘Panel’ has no member named ‘task_font’
config.c:401: error: ‘Panel’ has no member named ‘task_font_active’
config.c:403: error: ‘Panel’ has no member named ‘task_font_active’
config.c:423: error: ‘Panel’ has no member named ‘task_back’
config.c:425: error: ‘Panel’ has no member named ‘task_active_back’
config.c:427: error: ‘Panel’ has no member named ‘task_border’
config.c:429: error: ‘Panel’ has no member named ‘task_active_border’
config.c: In function ‘config_taskbar’:
config.c:475: error: ‘Panel’ has no member named ‘task_border’
config.c:476: error: ‘Panel’ has no member named ‘task_border’
config.c: In function ‘config_clock’:
config.c:507: error: ‘Panel’ has no member named ‘time1_format’
config.c:509: error: ‘Panel’ has no member named ‘time1_format’
config.c:509: error: ‘Panel’ has no member named ‘time_precision’
config.c:510: error: ‘Panel’ has no member named ‘time_precision’
config.c:512: error: ‘Panel’ has no member named ‘clock’
config.c:513: error: ‘Panel’ has no member named ‘clock’
config.c:513: error: ‘Panel’ has no member named ‘clock’
config.c:513: error: ‘Panel’ has no member named ‘time_precision’
config.c:515: error: ‘Panel’ has no member named ‘clock_posy’
config.c:516: error: ‘Panel’ has no member named ‘clock_height’
config.c:518: warning: implicit declaration of function ‘config_get_text_size’
config.c:518: error: ‘Panel’ has no member named ‘time1_font_desc’
config.c:519: error: ‘Panel’ has no member named ‘time2_format’
config.c:520: error: ‘Panel’ has no member named ‘time2_font_desc’
config.c:522: error: ‘Panel’ has no member named ‘time1_posy’
config.c:522: error: ‘Panel’ has no member named ‘clock_height’
config.c:523: error: ‘Panel’ has no member named ‘time1_posy’
config.c:525: error: ‘Panel’ has no member named ‘time2_posy’
config.c:525: error: ‘Panel’ has no member named ‘time1_posy’
config.c:528: error: ‘Panel’ has no member named ‘time1_posy’
config.c:528: error: ‘Panel’ has no member named ‘clock_height’
config.c:530: error: ‘Panel’ has no member named ‘redraw_clock’
config.c: In function ‘config_finish’:
config.c:558: error: ‘Panel’ has no member named ‘launcher_width’
config.c:569: error: ‘Panel’ has no member named ‘task_font_desc’
config.c:573: error: ‘Panel’ has no member named ‘task_border’
config.c: In function ‘config_read’:
config.c:584: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
config.c:584: error: expected expression before ‘const’
config.c:586: error: ‘gint’ undeclared (first use in this function)
config.c:586: error: (Each undeclared identifier is reported only once
config.c:586: error: for each function it appears in.)
config.c:586: error: expected ‘;’ before ‘i’
config.c:589: warning: implicit declaration of function ‘g_build_filename’
config.c:589: warning: implicit declaration of function ‘g_get_user_config_dir’
config.c:589: warning: assignment makes pointer from integer without a cast
config.c:590: warning: implicit declaration of function ‘g_file_test’
config.c:590: error: ‘G_FILE_TEST_EXISTS’ undeclared (first use in this function)
config.c:593: error: ‘system_dirs’ undeclared (first use in this function)
config.c:593: warning: implicit declaration of function ‘g_get_system_config_dirs’
config.c:594: error: ‘i’ undeclared (first use in this function)
config.c:595: warning: assignment makes pointer from integer without a cast
config.c:604: warning: assignment makes pointer from integer without a cast
config.c:605: error: ‘G_FILE_TEST_IS_DIR’ undeclared (first use in this function)
config.c:605: warning: implicit declaration of function ‘g_mkdir’
config.c:616: warning: control reaches end of non-void function
config.c: In function ‘save_config’:
config.c:643: error: ‘Panel’ has no member named ‘task_back’
config.c:644: error: ‘Panel’ has no member named ‘task_active_back’
config.c:646: error: ‘Panel’ has no member named ‘task_border’
config.c:646: error: ‘Panel’ has no member named ‘task_border’
config.c:647: error: ‘Panel’ has no member named ‘task_active_border’
config.c:647: error: ‘Panel’ has no member named ‘task_border’
config.c:653: warning: assignment makes pointer from integer without a cast
config.c:694: error: ‘Panel’ has no member named ‘task_font’
config.c:694: error: ‘Panel’ has no member named ‘task_font’
config.c:694: error: ‘Panel’ has no member named ‘task_font’
config.c:694: error: ‘Panel’ has no member named ‘task_font’
config.c:695: error: ‘Panel’ has no member named ‘task_font_active’
config.c:695: error: ‘Panel’ has no member named ‘task_font_active’
config.c:695: error: ‘Panel’ has no member named ‘task_font_active’
config.c:695: error: ‘Panel’ has no member named ‘task_font_active’
config.c:700: error: ‘Panel’ has no member named ‘task_border’
config.c:701: error: ‘Panel’ has no member named ‘task_back’
config.c:701: error: ‘Panel’ has no member named ‘task_back’
config.c:701: error: ‘Panel’ has no member named ‘task_back’
config.c:701: error: ‘Panel’ has no member named ‘task_back’
config.c:702: error: ‘Panel’ has no member named ‘task_active_back’
config.c:702: error: ‘Panel’ has no member named ‘task_active_back’
config.c:702: error: ‘Panel’ has no member named ‘task_active_back’
config.c:702: error: ‘Panel’ has no member named ‘task_active_back’
config.c:703: error: ‘Panel’ has no member named ‘task_border’
config.c:704: error: ‘Panel’ has no member named ‘task_border’
config.c:704: error: ‘Panel’ has no member named ‘task_border’
config.c:704: error: ‘Panel’ has no member named ‘task_border’
config.c:704: error: ‘Panel’ has no member named ‘task_border’
config.c:705: error: ‘Panel’ has no member named ‘task_active_border’
config.c:705: error: ‘Panel’ has no member named ‘task_active_border’
config.c:705: error: ‘Panel’ has no member named ‘task_active_border’
config.c:705: error: ‘Panel’ has no member named ‘task_active_border’
config.c:719: error: ‘Panel’ has no member named ‘mouse_middle’
config.c:720: error: ‘Panel’ has no member named ‘mouse_middle’
config.c:721: error: ‘Panel’ has no member named ‘mouse_middle’
config.c:722: error: ‘Panel’ has no member named ‘mouse_middle’
config.c:723: error: ‘Panel’ has no member named ‘mouse_middle’
config.c:726: error: ‘Panel’ has no member named ‘mouse_right’
config.c:727: error: ‘Panel’ has no member named ‘mouse_right’
config.c:728: error: ‘Panel’ has no member named ‘mouse_right’
config.c:729: error: ‘Panel’ has no member named ‘mouse_right’
config.c:730: error: ‘Panel’ has no member named ‘mouse_right’
config.c:733: error: ‘Panel’ has no member named ‘mouse_scroll_up’
config.c:734: error: ‘Panel’ has no member named ‘mouse_scroll_up’
config.c:735: error: ‘Panel’ has no member named ‘mouse_scroll_up’
config.c:736: error: ‘Panel’ has no member named ‘mouse_scroll_up’
config.c:737: error: ‘Panel’ has no member named ‘mouse_scroll_up’
config.c:740: error: ‘Panel’ has no member named ‘mouse_scroll_down’
config.c:741: error: ‘Panel’ has no member named ‘mouse_scroll_down’
config.c:742: error: ‘Panel’ has no member named ‘mouse_scroll_down’
config.c:743: error: ‘Panel’ has no member named ‘mouse_scroll_down’
config.c:744: error: ‘Panel’ has no member named ‘mouse_scroll_down’
make: *** [tint] Error 1

```

Then here's what happens when I do sudo make install:

```
mkdir -p /usr/bin
mkdir -p /etc/xdg/tint
install tint /usr/bin
install: cannot stat `tint': No such file or directory
make: *** [install] Error 1

```

Then I have a screenshot of what I get when I use the .deb.

---

### Post by thil77 on 2008-08-28
ok, message show you are missing devel packages.

try
sudo aptitude install libcairo2-dev libpango1.0-dev libglib2.0-dev libimlib2-dev

and then in directory /src
make
sudo make install

and run tint

---

### Post by mp3_freak_721 on 2008-08-28
Cool. I got it. Thanks.

---

### Post by e2k on 2008-09-21
I get this same error even though I have all the dev's? What gives?

EDIT: Nevermind, I needed libxinerama-dev and libxrandr-dev to make it happen!

---

### Post by easybake on 2009-01-07
> **e2k said:**
> I get this same error even though I have all the dev's? What gives?

EDIT: Nevermind, I needed libxinerama-dev and libxrandr-dev to make it happen!

+1

Thanks listing those, they aren't in the readme as dependencies.

---

