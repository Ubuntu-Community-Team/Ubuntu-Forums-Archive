---
title: "Steam unable to update. Posting paste link of log."
date: 2020-05-10
forum: Gaming &amp; Leisure
---

### Post by Tadaen_Sylvermane on 2020-05-10
[https://paste.ubuntu.com/p/tsvj4t7T8k/](https://paste.ubuntu.com/p/tsvj4t7T8k/)

```
$ df -hFilesystem                          Size  Used Avail Use% Mounted on
udev                                3.9G     0  3.9G   0% /dev
tmpfs                               795M  1.5M  793M   1% /run
/dev/nbd0                           2.5G  2.5G     0 100% /run/initramfs/rofs
tmpfs                               3.9G   44M  3.9G   2% /run/initramfs/cow
overlay                             3.9G   44M  3.9G   2% /
tmpfs                               3.9G   49M  3.9G   2% /dev/shm
tmpfs                               5.0M  4.0K  5.0M   1% /run/lock
tmpfs                               3.9G     0  3.9G   0% /sys/fs/cgroup
server:/home/jason                  229G   49G  169G  23% /home/jason
tmpfs                               795M   16K  795M   1% /run/user/5000
megalith.mylan.home:/snapraid/pool  2.7T  2.0T  659G  75% /snapraid/pool
```

This is a network booted machine. I can get a good run with no trouble on a local install on ssd but this just doesn't work. It fails like this everytime. I'm not sure why it didn't append to the log but there were a ton of lines like this as well. The home directory is mounted via sshfs.

```
tar: steam-runtime/usr/lib/x86_64-linux-gnu/libxcb-xvmc.so.0: Cannot utime: No such file or directorytar: steam-runtime/usr/lib/x86_64-linux-gnu/libxcb.so.1: Cannot utime: No such file or directory
tar: steam-runtime/usr/lib/x86_64-linux-gnu/libxml2.so.2: Cannot utime: No such file or directory
tar: steam-runtime/usr/lib/x86_64-linux-gnu/sasl2/libsasldb.so: Cannot utime: No such file or directory
tar: steam-runtime/usr/lib/x86_64-linux-gnu/sasl2/libsasldb.so.2: Cannot utime: No such file or directory
tar: steam-runtime/usr/lib/x86_64-linux-gnu/vdpau/libvdpau_trace.so.1: Cannot utime: No such file or directory
tar: steam-runtime/usr/share/man/man5/hosts.allow.5.gz: Cannot utime: No such file or directory
tar: steam-runtime/usr/share/man/man5/hosts.deny.5.gz: Cannot utime: No such file or directory
tar: steam-runtime/i386/selinux: Cannot utime: No such file or directory
tar: steam-runtime/amd64/selinux: Cannot utime: No such file or directory
tar: Exiting with failure status due to previous errors
```

---

### Post by mastablasta on 2020-05-11
have you tried turning it off an on again? i mean uninstall and reinstall?

what do you mean "network booted"?

it's as if it was searchign for some libraries but could not find them. 20.04 LTS ?

---

### Post by Tadaen_Sylvermane on 2020-05-11
18.04 LTSP based pxe booted machine. I've been using it for most everything around my home, but this and PlayonLinux have had me hit a wall, both with similar issues. I've posted about it over the last few years but never get anywhere. I've been tinkering with it off and on. I just can't figure it out. Everything seems to work just like a desktop installation. I can even run Virtualbox on it. But these 2 things just don't happen. Wine works by itself but installing additional versions of wine via playonlinux utime erros and says file doesn't exist. and the above is steam after installing package. first run trying to download and setup results in the above.

Not a necessity by any means. Just a problem I've been banging my head on for awhile. Kind of like police and cold cases? I assume some of them work them occasionally.

---

### Post by mastablasta on 2020-05-12
well i don't know this type of setup. However, the way i would approach this is first check if libs are where the applications is calling them from. so just make sure they are at the place where steam is looking fo them.
For example is [COLOR=#000000][FONT=&amp]libvdpau_trace.so.1 found in folder [/FONT][/COLOR][COLOR=#000000][FONT=&amp]steam-runtime/usr/lib/x86_64-linux-gnu/vdpau/[/FONT][/COLOR]?

[COLOR=#000000][FONT=&amp]steam-runtime/usr/lib/x86_64-linux-gnu/vdpau/libvdpau_trace.so.1: Cannot utime: No such file or directory

and then second - if it is there, does the application have at least read access?

and third you might need to do some symlinks. not sure. are the PoL files ([/FONT][/COLOR]prefixes) [COLOR=#000000][FONT=&amp]installed in home?


[/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2020-05-12
```
[COLOR=#000000][2020-05-10 18:21:10] Shutdown[/COLOR]Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
Unpack runtime failed, error code 3
Error: Couldn't set up the Steam Runtime. Are you running low on disk space?
Continuing...
```

This is the part that is probably causing all of that utime business then. This is the problem I can't figure for Steam. Even though as posted above /home/"$USER" has tons of space.

I did attempt extracting and setting up steam on my desktop linux and rsync the proper steam folders into place on the pxe server /home/"$USER". It still tried to do an install and failed as above.

---

### Post by mastablasta on 2020-05-13
if it doesn't have proper permissions in the folder it could appear to the app that there is 0 kb disk space in that folder.  check the ownership and group of the folder.

---

