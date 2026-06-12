---
title: "file manager unable to handle mounted drives"
date: 2012-10-03
forum: Desktop Environments
---

### Post by schwim on 2012-10-03
Hi there everyone,

I've got three mounted network shares in a new xubuntu install inside a vm.  When I try to explore the mounted shares of the parent folder, it just hangs with a loading icon, like it's trying to determine the contents.  I tried both in the file manager and in the stock audio player and both had the same issue.  Sudo mount -a in terminal does not bring up any errors.

I've also got an Ubu 12.04 install with KDE, Mate and Gnome installed in this vm and using the same method of mounting drives, none of them have this issue.  It's only in XFCE.

To mount these drives, all I've done is installed cifs-utils and edited my fstab.  I've used the same method for years(installing smbfs when it existed) and this is the first time I've run into this issue.

Booting into the KDE environment the issue disappears.  Booting back into XFCE and the problem returns.

Any help on getting me to see these shares in XFCE would be greatly appreciated!

---

### Post by rai4shu2 on 2012-10-03
Sounds like you've run into that infamous Thunar bug. See:

[https://bugzilla.xfce.org/show_bug.cgi?id=7373](https://bugzilla.xfce.org/show_bug.cgi?id=7373)
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117)

```
sudo leafpad /usr/share/gvfs/mounts/network.mount
```

Then change the "AutoMount=true" part to "AutoMount=false".

You'll then want to start Thunar with:

```
gvfs-mount network: > /dev/null  && gvfs-ls network: > /dev/null
```

I think one of the above links has a .desktop file with this that you can just put into ~/.config/autostart and that will fix that.

---

