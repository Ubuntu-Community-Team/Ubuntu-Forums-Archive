---
title: "Update caused icons and appearance to change drastically!"
date: 2011-08-04
forum: Desktop Environments
---

### Post by zephyr707 on 2011-08-04
Hi All,

I just updated a bunch of things on my system (10.10 x86_64) via synaptic and when I rebooted to finish the update everything looks horrible.  All the Icons are different, taskbar is all gray, compiz is acting funny, and the top bar has different icons and coloring.  I'm wondering what happened and how I can fix this...  I'm guessing it might be the nvidia update, but I'm not sure, here is what I did for the update/install:

Upgraded the following packages:
libsmbclient (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
libwbclient0 (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
linux-headers-2.6.35-30 (2.6.35-30.54) to 2.6.35-30.56
linux-headers-2.6.35-30-generic (2.6.35-30.54) to 2.6.35-30.56
linux-image-2.6.35-30-generic (2.6.35-30.54) to 2.6.35-30.56
linux-libc-dev (2.6.35-1030.54) to 2.6.35-1030.56
nvidia-current (275.19-0ubuntu1~maverick~xup1) to 280.13-0ubuntu1~maverick~xup1
nvidia-current-modaliases (275.19-0ubuntu1~maverick~xup1) to 280.13-0ubuntu1~maverick~xup1
nvidia-settings (275.19-0ubuntu1~maverick~xup1) to 280.13-0ubuntu1~maverick~xup1
samba-common (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
samba-common-bin (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
smbclient (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
winbind (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5

Installed the following packages:
asunder (1.9.3-2)
cdparanoia (3.10.2+debian-9)
flac (1.2.1-3)
libao-common (1.0.0-4)
libao4 (1.0.0-4)
vorbis-tools (1.4.0-1ubuntu1)
wavpack (4.60.1-1)

The only other thing I changed was to turn off the auto-login so I wouldn't have that damn keyring password dialog pop up during login.

Should I try downgrading the NVIDIA package update or look through any particular logs to see what happened?  Any help is appreciated,
thanks
z

---

### Post by zephyr707 on 2011-08-04
ok, I just ran the following in /var/cache/apt and everything is back to normal:

sudo dpkg -i nvidia-current-modaliases_275.19-0ubuntu1~maverick~xup1_amd64.deb
sudo dpkg -i nvidia-current_275.19-0ubuntu1~maverick~xup1_amd64.deb
sudo dpkg -i nvidia-settings_275.19-0ubuntu1~maverick~xup1_amd64.deb

guess there is something that it doesn't like in the latest nvidia package...

---

### Post by zephyr707 on 2011-08-12
I  think I know what the problem is, on their ppa:

```
If you are uprading from one release to another with this PPA activated,  please install the ppa-purge package and use it to downgrade everything  in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.

```

will try that.

---

