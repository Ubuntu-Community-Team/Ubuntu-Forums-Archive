---
title: "Strange invisible window causing 'dead zone' in Unity"
date: 2011-06-13
forum: Desktop Environments
---

### Post by flibs69 on 2011-06-13
I have a very strange problem.  Every so often a strange window will appear on the screen - well, I say "appear", but it can't be seen.  I know it's there though.  It creates a sort of 'dead zone' on the screen - always in the same place.

xwininfo: Window id: 0xe1ce72 (has no name)

  Absolute upper-left X:  438
  Absolute upper-left Y:  299
  Relative upper-left X:  438
  Relative upper-left Y:  299
  Width: 502
  Height: 222
  Depth: 0
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOnly
  Colormap: 0x0 (not installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: yes
  Corners:  +438+299  -426+299  -426-247  +438-247
  -geometry 502x222+438+299

I can't identify what process has created it, and I can't get rid of it without logging out (xkill does nothing).

Any ideas for how I can find out what is opening the window?  Has anyone else come across this happening?

Ubuntu 11.04

Linux laptop01 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by flibs69 on 2011-06-13
I am looking at the /usr/lib/unity/unity-panel-service process - I killed it, the process auto-restarted, and the window seems to have vanished.  I will try it again next time it appears.

---

### Post by flibs69 on 2011-06-13
Ok, I understand this is a known bug, #755459 - [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/755459](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/755459)

---

