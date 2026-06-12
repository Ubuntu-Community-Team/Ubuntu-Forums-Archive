---
title: "&quot;Places&quot; menu items not working"
date: 2006-01-11
forum: Desktop Environments
---

### Post by psYchotic on 2006-01-11
I've got a weird problem here : some of the items in the "Places" menu stopped working yesterday for some reason. Whenever I click on any of my bookmarks, or on one of my /media mounts, I'm being told the following :> Cannot display location 'file:///media/E'

Details: There is no default action associated with this location.

There are two things that I have been tampering with lately (at least, those are the only two I can remember). I tried to change the PATH environment variable a little, but I think I changed it back to default> env|grep PATH
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

Anything weird there?
Also I deleted some things in my /usr/local/bin (some winetools stuff)> ls /usr/local/bin
advcfg   advs           polymer-config  qemu-ppc            qjoypad
advj     advv           qemu            qemu-sparc          svlc
advk     chdman         qemu-arm        qemu-system-mips    vlc
advm     corrupt_mpeg2  qemu-armeb      qemu-system-ppc     vlc-config
advmame  extract_mpeg2  qemu-i386       qemu-system-sparc   wxvlc
advmenu  mpeg2dec       qemu-img        qemu-system-x86_64
Is there anything you can think of that I would be missing in there?

If it's neither of these two things, what could be causing this?

---

### Post by psYchotic on 2006-01-11
Never mind, for some odd reason, when I did CTRL+C during some script being run with sudo, I was locked out of ubuntu, until I did a "chmod 755 /", and I also had to do the same for my home directory, because I thought that was the problem. Anyway, now those menu items work again, don't ask me why.

---

