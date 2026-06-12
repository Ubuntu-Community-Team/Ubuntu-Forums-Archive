---
title: "wine, mechwarrior mercenaries"
date: 2011-05-01
forum: Desktop Environments
---

### Post by bobdobbs on 2011-05-01
Hi all.

winehq has a howto on installing mercs on linux. Looks like some people have gotten it running on linux.

I've been following this howto:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20739&iTestingId=57115](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20739&iTestingId=57115)

However, when I enter the command:
```
wine MW4Mercs.exe -noautoconfig -window /gosnoblade /gosnodialogs /gosnovideo

```
... the program fails to run. I get this output:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32d2fc,0x00000000), stub!
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x1e64b50)
fixme:imm:ImmReleaseContext (0x20056, 0x1e60378): stub
fixme:imm:ImmGetOpenStatus (0x1e60378): semi-stub
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000007 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32d448,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 58
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 64
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  27 (X_GLXCreatePbuffer)
  Serial number of failed request:  1887
  Current serial number in output stream:  1888

```

What is happening here? Is there a remedy?

---

