---
title: "Ubuntu 9.04 fails to login to account"
date: 2009-05-03
forum: General Help
---

### Post by rjw201 on 2009-05-03
I am attempting to login to an account, where the accounts home directory (/home/richard) is located on a different volume. That volume is formated as ntfs. This worked fine in Ubuntu 8.10, but fails when logging in graphically under 9.04 following an upgrade. 

When I login using the command line using the same account, it is a success, and listing the home directory works. However logging in under GNOME fails. When I attempt to login, the login prompt clears and a black screen appears with only a pointer displaying.

By changing console, and using sudo ps -Urichard using a different account the following appears.

```

  PID TTY          TIME CMD
 7939 ?        00:00:00 gnome-keyring-d
 7951 ?        00:00:00 pulse-session
 8050 ?        00:00:00 ssh-agent
 8055 ?        00:00:00 dbus-daemon
 8057 ?        00:00:00 dbus-launch
 8059 ?        00:00:00 start-pulseaudi
 8060 ?        00:00:00 pulseaudio

```

If all these programs are killed using sudo kill -9, then the console returns to the login screen.

I have attempted removing all the .files and folders from the root of the home directory to no gain. I have tried recreating the account, but this fails as well, when the home directory is reconnected.

The volume is mounted in fstab using the following:

```

/dev/sda1    /home/richard    ntfs-3g    rw,utf8,uid=1002,gid=1002,umask=022    0    0

```

Any help or suggestions would be appreciated

---

