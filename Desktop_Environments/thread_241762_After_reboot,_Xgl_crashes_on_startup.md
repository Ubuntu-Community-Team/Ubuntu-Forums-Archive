---
title: "After reboot, Xgl crashes on startup"
date: 2006-08-22
forum: Desktop Environments
---

### Post by wyldeone on 2006-08-22
I've been trying to setup Xgl/compiz since reformating and moving to the x86 version of dapper (I became fed up with the state of the x64 repositories), and have for some reason been having a much harder time of it then I did on x64, where everything seemed to work well out of the box.

My problems first started when neither xorg nor Xgl would work with the nvidia binary driver package in the ubuntu repositories. No problem, I installed the one from nVidia's site, and both xorg and Xgl seemed satisfied. I installed compiz, which worked great also.

I then rebooted in order to change hdds (I have four hdds and only three IDE cables), and when I booted up Xgl refused to start. When I try to start it, it gives this error message:
```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  93
  Current serial number in output stream:  94

```

I've looked around the internet for help on this error, but have failed to find something that helps my problems. I'm finding it really hard to go back to an unaccellerated desktop after a month on compiz, and any help would be greatly appreciated.

Edit: I forgot to mention that xorg works fine, it's just Xgl

---

### Post by somedude66 on 2006-08-23
Try reinstalling the nvidia drivers. That sometimes fixes these sorts of problems.

---

