---
title: "VNC and Gnome Desktop in 18.04 still broken?"
date: 2018-10-03
forum: Desktop Environments
---

### Post by alvarosainzpardo on 2018-10-03
> **muktupavels said:**
> ```
#!/bin/sh

export XKL_XMODMAP_DISABLE=1
export XDG_CURRENT_DESKTOP="GNOME-Flashback:GNOME"
export XDG_MENU_PREFIX="gnome-flashback-"

gnome-session --session=gnome-flashback-metacity --disable-acceleration-check &
```

Try that! If does not work then append --debug to gnome-session line and post log file.

gnome-session will try to start full default session (I think) and that will not work as gnome-shell / mutter requires compositing manager or maybe it even does not do that because acceleration-check fails. From log file you probably already know that composite extension is not available...

Worked for me, thank you very much!!!!

For now, I have only one problem: one minute or so after connecting, the application gnome-inital-setup crashes:
package: gnome-initial-setup 3.28.0-2ubuntu6.16.04-2 (although I'm using in the server 18.04)
error: gnome-initial-setup crashed with signal 5 in _XReply()

I can upload a screen capture if it helps.

Thank you in advance!

---

