---
title: "getty and console services failing at boot."
date: 2023-04-17
forum: Desktop Environments
---

### Post by johntelek on 2023-04-17
Hello,

   I really seed help as I really do not want to wipe my system. I was looking through my services
with a program called Stacer and I turned some thing off by accident. all of a sudden X11 crashed and all consoles disapeared.
 I could get in with single user but the ttys were printing garbage and not accepting my password.
But I persevered and eventually got in as root. I don't know much about systemctl and journalctl
but my various services are all over the place. It's like trying to log in while its having a seizure.

Is there any way I can reset systemd or reinstall the original files as at install 
I was playing around with opevpn and it was problematic. I tried with apt first
then I found a script claiming it did evrything and then another one which sort of
worked  and thats where systemctl status came back with erros.

Help please.

   John.

---

### Post by johntelek on 2023-04-19
I fixed it and I have a working GUI again. I basically had to reinstall several packages.

apt reinstall task-gnome-desktop
apt reinstall --purge getty-run
apt reinstall systemctl
and
apt reinstall --purge linux-base

This stopped the console from going berko and I could start gdm.

Cheers,
   JT.

---

