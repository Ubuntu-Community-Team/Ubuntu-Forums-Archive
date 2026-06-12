---
title: "Remote Desktop"
date: 2009-06-20
forum: General Help
---

### Post by opus_az on 2009-06-20
Hello...

In System -> Preferences -> Remote Desktop, I have Sharing set to allow others to view and control the desktop, and on my Mac I can connect to the Ubuntu with Mac Screen Sharing or Chicken of the VNC.

But the screen is not refreshing on my Mac. My Mac keyboard and mouse are controlling the Ubuntu desktop. It's just that the changes to the Ubuntu screen are not reflected back to the Mac.

Any suggestions? 9.04 updated and upgraded.

---

### Post by zadehas on 2009-06-21
Do you have visual effects running?
If so, try turning them off. I remember I once had the same problem because of that.

---

### Post by XCan on 2009-06-21
Unfortunately, this is a known bug in 9.04. Also, don't expect it to be fixed as apparently people consider it to be less important... There is a workaround which involves enabling -noxdamage in vino, but it makes the whole remote desktop experience terribly slow.

If you really want to use it, unfortunately you would have to disable visual effects. :(

See [https://bugs.launchpad.net/bugs/353126](https://bugs.launchpad.net/bugs/353126) for more information.

---

