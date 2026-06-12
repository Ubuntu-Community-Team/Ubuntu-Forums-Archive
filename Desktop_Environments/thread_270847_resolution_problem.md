---
title: "resolution problem"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Naegling23 on 2006-10-03
Ok, so Im trying to play NWN at 1024x768 resolution, but I get the following error:

naegling23@naegling23-kubuntu:/usr/local/games/nwn$ ./nwn
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x138
  Serial number of failed request:  106
  Current serial number in output stream:  108

After spending 3 days researching the problem, it appears that it could be a problem with my xorg.conf file.  Currently my desktop resolution is set to 1024x768, and I can run doom3 at 1024x768 without a problem.  The resolution appears in my xorg.conf file.  So what am I missing here?  Why do I still have this problem.

One interesting note, is that NWN runs in xgl/compiz at 1024x768, but not in regular kde running x.  I dont want to run in xgl/compiz, because the graphics load causes the game to run really choppy.

---

