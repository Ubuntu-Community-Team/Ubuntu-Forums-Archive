---
title: "Wine - Cinema 4D [ERROR]"
date: 2006-05-18
forum: Desktop Environments
---

### Post by danrom on 2006-05-18
I have installed cinema 4D 9.5 XL Bundle with no errors.

I can run cinema4d with no wine errors, but cinema 4d gives me this error saying it cannot find the resources folder. So I put the resources folder in the root folder and try to run cinema 4D again. This is the error that wine gives me as cinema 4D does not boot.

```
Xlib:  extension "GLX" missing on display ":0.0".
err:opengl:process_attach Could not create default context.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  8
  Current serial number in output stream:  9

```

---

### Post by WayneZac on 2006-06-02
Have you tried 9.603?
Are you using the nvidia drivers, and loading the glx module in the modules section of you xorg.conf file? I followed the directions [here]("http://www.liquid-light.org/index.php?option=com_content&task=view&id=44&Itemid=44&lang=en") to get Cinema 4D 9.603 under wine, but I get the following dumped to my terminal:
[email]texel@wayne:~/.wine[/email]/drive_c/CINEMA 4D R9$ wine CINEMA\ 4D.exe
Invoking /usr/lib/wine/wine.bin CINEMA 4D.exe ...
fixme: opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme: opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme: opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme: opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme:sync:CreateMailslotW (L"\\\\.\\mailslot\\maxon.c4d",0,-1,(nil)): stub
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
fixme:msvideo: DrawDibDraw wFlags == 0x00001000 not handled
Wine failed with return code 1

There is also an error from Cinema:
Application Error! Cannot create file C:\CINEMA 4D R9\_bugreports\_BugReport.txt'!

After clicking 'OK' scenefiles will be saced as '_recovery_xxx.c4d'

Any ideas?

---

