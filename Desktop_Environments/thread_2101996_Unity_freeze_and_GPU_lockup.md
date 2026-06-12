---
title: "Unity freeze and GPU lockup"
date: 2013-01-06
forum: Desktop Environments
---

### Post by tuuk on 2013-01-06
Every couple of days, the Unity (Ubuntu 12.10) on my laptop (DELL Latitude 6510) freezes. I cannot get any response from the desktop. If I switch to a text terminal (Ctrl-Alt-F1) and switch back (Ctrl-Alt-F7), the desktop unfreezes but the Unity launcher, the top panel, and the title bars of the windows all disappear. Logging out (with Ctrl-Alt-Delete) does not solve the problem; a restart is needed. All the logged-in users are affected by this.

From the apport error messages I get, it looks like it is related to a GPU lockup and the package xserver-xorg-video-intel is implicated.

Does anyone have any ideas that can help with my problem?

Please let me know if I can provide more information that will be useful in diagnosis.

Thanks.
tuuk

---

### Post by fdrake on 2013-01-06
> **tuuk said:**
> Every couple of days, the Unity (Ubuntu 12.10) on my laptop (DELL Latitude 6510) freezes. I cannot get any response from the desktop. If I switch to a text terminal (Ctrl-Alt-F1) and switch back (Ctrl-Alt-F7), the desktop unfreezes but the Unity launcher, the top panel, and the title bars of the windows all disappear. Logging out (with Ctrl-Alt-Delete) does not solve the problem; a restart is needed. All the logged-in users are affected by this.

From the apport error messages I get, it looks like it is related to a GPU lockup and the package xserver-xorg-video-intel is implicated.

Does anyone have any ideas that can help with my problem?

Please let me know if I can provide more information that will be useful in diagnosis.

Thanks.
tuuk

if the freeze happens again login into the console and save the logs into a file```

 dmesg >> ~/dmesg.txt
less .xsession-errors > ~/xerrors.txt
```
and post here the files.

or provides us the dmesg (with the time the freeze happened) and the .xsession-errors.old

---

### Post by tuuk on 2013-01-11
Thanks fdrake. Attached are the logs as you asked. I hope it helps. It seems like there are some clues in there, but they do not mean much to me.

I am looking forward to hearing more.

Best,
tuuk

---

