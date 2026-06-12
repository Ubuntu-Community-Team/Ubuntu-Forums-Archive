---
title: "Vino 2.28.2 unstable on Ubuntu 10.4"
date: 2011-05-05
forum: Desktop Environments
---

### Post by aruckert on 2011-05-05
Hi!
I have a Linux box with Ubuntu 10.4 that I use basically to play music and download files.

It doesn't have a monitor or keyboard, the only way I access it is using Ultra VNC.

Yesterday, the automatic update service offered to update Vino (among other things) to version 2.28.2 and, as usual, I accepted.

After the update Ultra VNC has had trouble negotiating the protocol with Vino. The only way I got it to work was to force using Tight as the compression method, which provides a crappy image quality.

Besides that, at some unexpected moment, the connection just dies.

Can anyone help me to:
1.- Solve this issue with the current Vino version or
2.- Go back to the previous version that was working perfectly.

Thank you in advance!


Augusto

---

### Post by aruckert on 2011-05-05
Well... It seems that the only thing unstable are my diagnosis skills...

The problem was totally unrelated to Vino.

For a reason that's too long to explain here the DHCP server assigned the same IP to two machines.

That's why the connection with the Linux server was unstable and sometimes died. And that's why Ultra VNC couldn't negotiate the protocol properly.

My apologies if anyone wasted time reading this thread!

Thanks anyway for stopping by :)

It hope it is useful at least to diagnose this problem in the future.

Cheers,


Augusto

---

