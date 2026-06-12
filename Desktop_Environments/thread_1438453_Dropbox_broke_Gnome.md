---
title: "Dropbox broke Gnome"
date: 2010-03-25
forum: Desktop Environments
---

### Post by nixbus on 2010-03-25
****Hey all,

I installed Dropbox on my system (Hardy) and now Gnome is broken. Naturally, I removed Dropbox, and no luck. I don't know what I was expecting. Anyway, if I try to start it from the terminal I get this message:

 
[I]Initializing gnome-mount extension
/home/ginger/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
Nautilus-Share-Message: REFRESHING SHARES
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: spawn arg "net"
Nautilus-Share-Message: spawn arg "usershare"
Nautilus-Share-Message: spawn arg "info"
Nautilus-Share-Message: end of spawn args; SPAWNING

Nautilus-Share-Message: returned from spawn: SUCCESS: 
Nautilus-Share-Message: exit code 255
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: usershares are currently disabled

nautilus: symbol lookup error: /usr/lib/nautilus/extensions-1.0/libgnome-mount.so: undefined symbol: nautilus_file_info_get_drive[/I][/INDENT]
[/I]

Any help that can be provided would be very appreciated.

Thanks.

Regards.

---

### Post by nixbus on 2010-03-25
I've seen other posts about this, but the error messages seem to be different than mine.

So, any help or guidance would be great.

---

### Post by krismatth3 on 2010-03-26
This is a long shot, but it really looks like your /home/ginger/.gtkrc-2.0 file got messed up somehow. Can you paste it here?

---

### Post by nixbus on 2010-04-02
this?

*gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0*

---

