---
title: "remove and reinstall dead unity? (oneiric)"
date: 2011-10-30
forum: Desktop Environments
---

### Post by blackbird34 on 2011-10-30
Hi
My unity no longer works... I have tried getting it back with ```
 unity --reset
``` and ```
 unity --replace 
``` whicch is what i was told to do in Natty, in Terminal and from the tty. I've also tried reinstalling it through synaptic...
Neither of those seem to work. It's only a test partition, but still, i'd like to find a way to get unity back, i was beginning to like it ;)

Any advice please?:popcorn:

---

### Post by blackbird34 on 2011-10-30
This is what i get when i type "unity" in terminal , to try and make it restart:

 ```
nad@nad-Presario-CQ56-Notebook-PC:~$ unity
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...[ERROR]: Option "next_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "next_no_popup_button" already defined
[ERROR]: Option "next_no_popup_key" already defined
[ERROR]: Option "prev_no_popup_button" already defined
[ERROR]: Option "prev_no_popup_key" already defined
[ERROR]: Option "next_panel_button" already defined
[ERROR]: Option "next_panel_key" already defined
[ERROR]: Option "prev_panel_button" already defined
[ERROR]: Option "prev_panel_key" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "auto_change_vp" already defined
[ERROR]: Option "popup_delay" already defined
[ERROR]: Option "mouse_select" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "brightness" already defined
[ERROR]: Option "opacity" already defined
[ERROR]: Option "icon" already defined
[ERROR]: Option "icon_only" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "row_align" already defined
[ERROR]: Option "focus_on_switch" already defined
[ERROR]: Option "bring_to_front" already defined
[ERROR]: Option "highlight_mode" already defined
[ERROR]: Option "highlight_rect_hidden" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "highlight_border_color" already defined
[ERROR]: Option "highlight_border_inlay_color" already defined
done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
compiz (core) - Warn: no exact match for ConfigureNotify on 0x3a00093!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x43ee95
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1366
compiz (core) - Warn: height: 768
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x30000db



```

and when i do "unity --reset --verbose"

```
nad@nad-Presario-CQ56-Notebook-PC:~$ unity --restart
Usage: unity [options]

unity: error: no such option: --restart
nad@nad-Presario-CQ56-Notebook-PC:~$ man unity
nad@nad-Presario-CQ56-Notebook-PC:~$ man unity-panel-service
nad@nad-Presario-CQ56-Notebook-PC:~$ unity-panel-service
unity-panel-service: command not found
nad@nad-Presario-CQ56-Notebook-PC:~$ unity --reset --verbose
unity-panel-service: no process found
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libccp.so : No such file or directory
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 689
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 27629808, sibling: 0x1a58b30
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 775
compiz (core) - Debug: - event window 0x3c00099
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 27632416, sibling: 0x1a5a1c0
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 853
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 768 border: 4, sibling: 0x406bbd7c
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 872
compiz (core) - Debug: - event window 0x3c00099
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 768 border: 4, sibling: 0x406bbd7c
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 897
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1221 y: 0 width: 48 height: 304 border: 4, sibling: 0x406bbd7c
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libbailer.so : No such file or directory
Initializing bailer options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libdetection.so : No such file or directory
Initializing detection options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libcomposite.so : No such file or directory
Initializing composite options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libopengl.so : No such file or directory
Initializing opengl options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libdecor.so : No such file or directory
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 2194
compiz (core) - Debug: - event window 0x3c00090
compiz (core) - Debug: - x: -8 y: -29 width: 738 height: 492 border: -1308927600, sibling: 0x43e722
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 2222
compiz (core) - Debug: - event window 0x3c00093
compiz (core) - Debug: - x: -8 y: -29 width: 738 height: 492 border: -1308927600, sibling: 0x43e722
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 2272
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 768 border: 27626288, sibling: 0x44550d
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 2324
compiz (core) - Debug: - event window 0x3c00099
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 768 border: 27632064, sibling: 0x44550d
Initializing decor options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libmousepoll.so : No such file or directory
Initializing mousepoll options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libvpswitch.so : No such file or directory
Initializing vpswitch options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libregex.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libanimation.so : No such file or directory
Initializing animation options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libsnap.so : No such file or directory
Initializing snap options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libexpo.so : No such file or directory
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libmove.so : No such file or directory
Initializing move options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libcompiztoolbox.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libplace.so : No such file or directory
Initializing place options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libgrid.so : No such file or directory
Initializing grid options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libimgpng.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libgnomecompat.so : No such file or directory
Initializing gnomecompat options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libwall.so : No such file or directory
Initializing wall options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libezoom.so : No such file or directory
Initializing ezoom options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libworkarounds.so : No such file or directory
Initializing workarounds options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libstaticswitcher.so : No such file or directory
Initializing staticswitcher options...[ERROR]: Option "next_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "next_no_popup_button" already defined
[ERROR]: Option "next_no_popup_key" already defined
[ERROR]: Option "prev_no_popup_button" already defined
[ERROR]: Option "prev_no_popup_key" already defined
[ERROR]: Option "next_panel_button" already defined
[ERROR]: Option "next_panel_key" already defined
[ERROR]: Option "prev_panel_button" already defined
[ERROR]: Option "prev_panel_key" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "auto_change_vp" already defined
[ERROR]: Option "popup_delay" already defined
[ERROR]: Option "mouse_select" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "brightness" already defined
[ERROR]: Option "opacity" already defined
[ERROR]: Option "icon" already defined
[ERROR]: Option "icon_only" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "row_align" already defined
[ERROR]: Option "focus_on_switch" already defined
[ERROR]: Option "bring_to_front" already defined
[ERROR]: Option "highlight_mode" already defined
[ERROR]: Option "highlight_rect_hidden" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "highlight_border_color" already defined
[ERROR]: Option "highlight_border_inlay_color" already defined
done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libresize.so : No such file or directory
Initializing resize options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libfade.so : No such file or directory
Initializing fade options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libscale.so : No such file or directory
Initializing scale options...done
compiz (core) - Debug: Could not stat() file /home/nad/.compiz-1/plugins/libsession.so : No such file or directory
Initializing session options...done
compiz (core) - Debug: refusing to manage window 0x3c00090
compiz (core) - Debug: refusing to manage window 0x3c00093
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3383
compiz (core) - Debug: - event window 0x3c00093
compiz (core) - Debug: - x: -9 y: -58 width: 738 height: 492 border: -1308935904, sibling: 0x2
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3430
compiz (core) - Debug: - event window 0x3c00093
compiz (core) - Debug: - x: -1 y: -29 width: 722 height: 455 border: 412, sibling: 0x19d
compiz (core) - Debug: refusing to manage window 0x3c00096
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 689
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 27629808, sibling: 0x1a58b30
compiz (core) - Debug: refusing to manage window 0x3c00099
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 775
compiz (core) - Debug: - event window 0x3c00099
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 27632416, sibling: 0x1a5a1c0
compiz (core) - Debug: refusing to manage window 0x3c0009c
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 853
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 768 border: 4, sibling: 0x406bbd7c
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 872
compiz (core) - Debug: - event window 0x3c00099
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 768 border: 4, sibling: 0x406bbd7c
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 897
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1221 y: 0 width: 48 height: 304 border: 4, sibling: 0x406bbd7c
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3579
compiz (core) - Debug: - event window 0x3c00099
compiz (core) - Debug: - x: 0 y: -29 width: 1318 height: 768 border: -1308935904, sibling: 0x2
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3626
compiz (core) - Debug: - event window 0x3c00099
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 738 border: 412, sibling: 0x19d
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3721
compiz (core) - Debug: - event window 0x3c00090
compiz (core) - Debug: - x: -9 y: -58 width: 738 height: 492 border: -1308935904, sibling: 0x2
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3768
compiz (core) - Debug: - event window 0x3c00090
compiz (core) - Debug: - x: -1 y: -29 width: 722 height: 455 border: 412, sibling: 0x19d
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3800
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1318 y: 232 width: 48 height: 304 border: 0, sibling: 0x0
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3826
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 4, sibling: 0x406bbd7c
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 3976
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1318 y: 232 width: 145 height: 768 border: 0, sibling: 0x0
compiz (core) - Debug: refusing to manage window 0x3c000de
compiz (core) - Debug: refusing to manage window 0x3c000e0
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 2272
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1318 height: 768 border: 27626288, sibling: 0x44550d
compiz (core) - Debug: refusing to manage window 0x3c000e2
compiz (core) - Debug: refusing to manage window 0x3c000e4
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4142
compiz (core) - Debug: - event window 0x3c0015d
compiz (core) - Debug: - x: -8 y: -29 width: 738 height: 492 border: 412, sibling: 0x19d
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4165
compiz (core) - Debug: - event window 0x3c0015d
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 27062176, sibling: 0x1f58cd0
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4185
compiz (core) - Debug: - event window 0x3c0015d
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 3545002, sibling: 0x1000ab5
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4318
compiz (core) - Debug: - event window 0x3c00164
compiz (core) - Debug: - x: 0 y: -29 width: 722 height: 485 border: 412, sibling: 0x19d
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4341
compiz (core) - Debug: - event window 0x3c00164
compiz (core) - Debug: - x: 0 y: 0 width: 722 height: 485 border: 27062176, sibling: 0x1f62850
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4361
compiz (core) - Debug: - event window 0x3c00164
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 3545002, sibling: 0x3c0015d
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4466
compiz (core) - Debug: - event window 0x3c00168
compiz (core) - Debug: - x: -8 y: -29 width: 738 height: 492 border: 412, sibling: 0x19d
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4489
compiz (core) - Debug: - event window 0x3c00168
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 27062176, sibling: 0x1f593b0
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4509
compiz (core) - Debug: - event window 0x3c00168
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 3545002, sibling: 0x3c00164
compiz (core) - Debug: stacks are out of sync
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4546
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1221 y: 0 width: 145 height: 768 border: 0, sibling: 0x0
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 3800
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1318 y: 232 width: 48 height: 304 border: 0, sibling: 0x0
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 3826
compiz (core) - Debug: - event window 0x3c00096
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 4, sibling: 0x406bbd7c
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 3976
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1318 y: 232 width: 145 height: 768 border: 0, sibling: 0x0
compiz (core) - Debug: refusing to manage window 0x3c0015d
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4142
compiz (core) - Debug: - event window 0x3c0015d
compiz (core) - Debug: - x: -8 y: -29 width: 738 height: 492 border: 412, sibling: 0x19d
compiz (core) - Debug: refusing to manage window 0x3c0015f
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4165
compiz (core) - Debug: - event window 0x3c0015d
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 27062176, sibling: 0x1f58cd0
compiz (core) - Debug: refusing to manage window 0x3c00164
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4318
compiz (core) - Debug: - event window 0x3c00164
compiz (core) - Debug: - x: 0 y: -29 width: 722 height: 485 border: 412, sibling: 0x19d
compiz (core) - Debug: refusing to manage window 0x3c00166
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4341
compiz (core) - Debug: - event window 0x3c00164
compiz (core) - Debug: - x: 0 y: 0 width: 722 height: 485 border: 27062176, sibling: 0x1f62850
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4361
compiz (core) - Debug: - event window 0x3c00164
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 3545002, sibling: 0x3c0015d
compiz (core) - Debug: refusing to manage window 0x3c00168
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4466
compiz (core) - Debug: - event window 0x3c00168
compiz (core) - Debug: - x: -8 y: -29 width: 738 height: 492 border: 412, sibling: 0x19d
compiz (core) - Debug: refusing to manage window 0x3c0016a
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4489
compiz (core) - Debug: - event window 0x3c00168
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 27062176, sibling: 0x1f593b0
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4546
compiz (core) - Debug: - event window 0x3c0009c
compiz (core) - Debug: - x: 1221 y: 0 width: 145 height: 768 border: 0, sibling: 0x0
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1000acf

compiz (core) - Debug: - event serial: 4185
compiz (core) - Debug: - event window 0x3c0015d
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 3545002, sibling: 0x1000ab5
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1000aeb

compiz (core) - Debug: - event serial: 4509
compiz (core) - Debug: - event window 0x3c00168
compiz (core) - Debug: - x: -7 y: 0 width: 738 height: 492 border: 3545002, sibling: 0x3c00164
compiz (stackdebugger) - Warn: 0x2400027 requested invalid layer 0x7ffffff
compiz (core) - Debug: windows are stacked incorrectly


```

---

### Post by Mark Phelps on 2011-10-30
Good luck.  I've been using Ubuntu since 7.04, installed 11.10 this weekend -- and think this is the worst version I've ever encountered, bar none!!

I only installed this on Saturday and already, it's crashed on me over a half dozen times and frozen on me nearly as many.

I installed ccsm to make the same minor tweaks as I did successfully in 11.04 and -- NOW -- No unity anymore.  Probably same thing as you get.

Maybe if Canonical would quit trying to force cell-phone desktops on people and pushing us all into the cloud, they could take some time and stop pushing out garbage like this.

I even tried Recovery Mode -- something that always worked with the previous record-bad version  (10.10), but even that doesn't work!

I'm going to post in the General forum to see if anyone knows HOW to recovery from this.  But, given the poor level of this release, I'm guessing a reinstall is going to be needed.

---

### Post by Mark Phelps on 2011-10-30
You're in luck -- I found the solution!!

I tried each of the following in turn, hoping to NOT have to reinstall compiz and unity, so maybe you won't have to go that far -- I did.

For each of these, do the following:
1) Exit the desktop and get into tty mode -- using Ctl+alt+F1
2) Enter ALL of the commands
3) Press Ctl_Alt_F7 to get the desktop back
4) If it's all back, you're done

First, try these commands:
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

Second, try these commands:
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config

If these didn't return the unity stuff, then you'll have to uninstall and reinstall, as follows:
sudo apt-get remove --purge compiz*
rm -rf .compiz-1
rm -rf .gconf/apps/compiz*
sudo apt-get install compiz compiz-core
sudo apt-get install unity

NOW, when you return to the desktop, you should have Unity again.

You may have to open System Settings -->< Display and reconfigure your displays, if you have multiple monitors or non-default resolution set -- I did.

NOW, isn't this "intuitively obvious to the most casual observer"??  This must be absurdly simple to folks coming over from MS Windows who simply try to shrink the icons in the Unity bar (which is all I did).

---

### Post by JasonR on 2011-10-30
> **blackbird34 said:**
> Hi
My unity no longer works... I have tried getting it back with ```
 unity --reset
``` and ```
 unity --replace 
``` whicch is what i was told to do in Natty, in Terminal and from the tty. I've also tried reinstalling it through synaptic...
Neither of those seem to work. It's only a test partition, but still, i'd like to find a way to get unity back, i was beginning to like it ;)

Any advice please?:popcorn:

Get into compizconfig settings manager (ccsm) and check the box for the Unity plugin.  Somehow, when you install and open ccsm, this thing gets unchecked and Unity 3d no longer works.

---

### Post by blackbird34 on 2011-10-31
I hope you're right JasonR. because i dont have two computers to follow mark phelps' instructions on ... But i think mine's more thoroughly broken than that. Good thing i installed docky after the first glitches or i'd be running everything in terminal...

---

### Post by arisp on 2011-10-31
Mine was broken like that with the line "unity-panel-service: no process found" coming up whatever i did to fix it. 
Finally I purged the xorg edgers ppa and everything went back to normal.
Just another thing to check out, just in case you have that ppa for the Xorg and drivers updates.

---

### Post by blackbird34 on 2011-10-31
I got that message too, but i didn't have that ppa. I had shrunk the unity icons ;) ...
But now i can't even get a terminal with ctrl + alt + T so i think i'll give up and reinstall.

Long live Natty with Gnome 2!!

---

### Post by Langleyo on 2011-11-02
Only thing that worked like a charm on my Toshiba satellite with Oneiric system which wouldn't hide the task bar. Thanks for sharing.

---

### Post by martinjo621 on 2011-11-19
> **Mark Phelps said:**
> You're in luck -- I found the solution!!

I tried each of the following in turn, hoping to NOT have to reinstall compiz and unity, so maybe you won't have to go that far -- I did.

For each of these, do the following:
1) Exit the desktop and get into tty mode -- using Ctl+alt+F1
2) Enter ALL of the commands
3) Press Ctl_Alt_F7 to get the desktop back
4) If it's all back, you're done

First, try these commands:
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

Second, try these commands:
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config

If these didn't return the unity stuff, then you'll have to uninstall and reinstall, as follows:
sudo apt-get remove --purge compiz*
rm -rf .compiz-1
rm -rf .gconf/apps/compiz*
sudo apt-get install compiz compiz-core
sudo apt-get install unity

NOW, when you return to the desktop, you should have Unity again.

You may have to open System Settings -->< Display and reconfigure your displays, if you have multiple monitors or non-default resolution set -- I did.

NOW, isn't this "intuitively obvious to the most casual observer"??  This must be absurdly simple to folks coming over from MS Windows who simply try to shrink the icons in the Unity bar (which is all I did).

thank you phelps i had this problem also and your post worked.  so tired of this unity garbage.  i have spent more time trying to fix and restore unity than i would like to admit. horrible

---

### Post by bacardiandwatermelon on 2011-11-22
Yeah thanks Mark, I only needed to run the first part. Who knew that trying to enable desktop cube would break so much hehe.

---

### Post by jimmydean886-2 on 2011-11-22
Over the past while people had started to complain (among them myself) about the Natty version of Unity. The reason being: It would crash if I did 3 consecutive actions on my laptop, until I got rid of all of the custom settings. I really can't see how Oneiric can be any worse than that, especially since it's working fine for me in this release. Anyway,

Another thing to try (this works with a lot of things) is to purge all of the configuration files in your home directory pertaining to Unity. I had problems with nautilus in the last release, and that solved them all.

The files will be either loose in your home dir, (just hidden) or in ./.config. (also hidden)

This may or may not help for the user who comes across this page looking for answers to their own problem with just about anything, Unity, Nautilus, Evolution, Shotwell, Banshee, etc. Pretty much anything except Mozilla applications has this problem.

---

### Post by frncz on 2012-01-08
I had the same problem after playing with compiz - there should be a warning on Compiz - not to be used by anyone over 50!

Anyway, Mark Phelps' solution was great.
I have to add that to check whether the commands actually worked, it is necessary to reboot.
From the tty I typed 'sudo reboot now', and everything re-started fine (oneiric amd64).
and of course compiz needs to be reinstalled, if for example, one wants to minimize the unity icons to 32 and make them permanent (which I do). To re-install compiz: 
'sudo apt-get install compiz-config-settings-manager'

Cheers

Mike

---

