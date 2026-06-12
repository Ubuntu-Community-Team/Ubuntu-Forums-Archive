---
title: "Problem With Beryl"
date: 2007-02-14
forum: Desktop Environments
---

### Post by Th1eF` on 2007-02-14
yesterday Beryl was working fine.
today when i start ubuntu beryl does not load and i load it manually.
but nothing change no effects no nothing.

any ideas?

also there are 2 updates for beryl in the update manager
beryl-plugins
and
beryl-plugins-dbg

when i try to install those updates i get the following error:
> 
E: /var/cache/apt/archives/beryl-plugins_0.1.9999.2~0beryl1_amd64.deb: trying to overwrite `/usr/lib/beryl/libthumbnail.so', which is also in package beryl-plugins-extra
E: /var/cache/apt/archives/beryl-plugins-dbg_0.1.9999.2~0beryl1_amd64.deb: trying to overwrite `/usr/lib/debug/usr/lib/beryl/libthumbnail.so', which is also in package beryl-plugins-extra-dbg


---

### Post by mssever on 2007-02-14
When I have trouble starting Beryl, it's usually due to direct rendering being off. To find out if direct rendering is on, type ```
glxinfo | grep 'direct rendering'
```If you don't have direct rendering, try logging out, hitting Ctrl+Alt+Backspace, and logging in again. If that doesn't enable direct rendering, reboot.

For some reason, on my machine, I used to have direct rendering all the time. Since I upgraded to edgy, though, I only get it the first time I log in after rebooting.

---

### Post by Th1eF` on 2007-02-14
mssever: i have try it and
> -desktop:~$ glxinfo | grep 'direct rendering'
direct rendering: Yes

but the same thing again.
i also have ubuntu 6.10 64bit

---

### Post by mssever on 2007-02-14
Hmm...

In that case, the only things I can think of are:
[LIST]
[*]Wait for the next release and hope it fixes your problems
[*]Reinstall Beryl
[*]Purge and reinstall Beryl (this will probably destroy all your settings)[/LIST]I guess that's the difficulty with using beta software. Maybe someone else has some better ideas...

---

### Post by NickPresta on 2007-02-14
To me,
> E: /var/cache/apt/archives/beryl-plugins_0.1.9999.2~0beryl1_amd64.deb: trying to overwrite `/usr/lib/beryl/libthumbnail.so', which is also in package beryl-plugins-extra
E: /var/cache/apt/archives/beryl-plugins-dbg_0.1.9999.2~0beryl1_amd64.deb: trying to overwrite `/usr/lib/debug/usr/lib/beryl/libthumbnail.so', which is also in package beryl-plugins-extra-dbg

It looks like you have an older version of beryl before the package beryl-plugins(-extra) was required. I would just purge + reinstall.

---

