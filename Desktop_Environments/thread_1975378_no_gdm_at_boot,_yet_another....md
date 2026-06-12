---
title: "no gdm at boot, yet another..."
date: 2012-05-07
forum: Desktop Environments
---

### Post by lo.j on 2012-05-07
hi all.

let's says that with upstart and the backward compatibility for sysv, things could not more complicated! :-\"

i've already tried:
[LIST]
[*]unset gdm with sysv-rc-conf
[*]sudo update-rc.d -f gdm remove
[*]GRUB_CMDLINE_LINUX_DEFAULT="text" + sudo update-grub
[/LIST]

the only thing that seems to have some effect is:
[LIST]
[*]echo "manual" | sudo tee -a /etc/init/gdm.override
[/LIST]
but it makes ubuntu boot into tty7 (or 8?) and hang there without returning any prompt.
so i need to manually go to tty1 but it's clearly not what i'm trying to achieve...

well, i'd prefer not to completely remove gdm...

thanks!

---

### Post by lo.j on 2012-05-08
> **lo.j said:**
> it makes ubuntu boot into tty7 (or 8?) and hang there without returning any prompt.

is this expected?

---

