---
title: "Apt-get &quot;Operation not permitted&quot;"
date: 2006-07-12
forum: Desktop Environments
---

### Post by SigmaX on 2006-07-12
Good morning.

Kubuntu Dapper, apt-get troubles; it either happened during or right after upgrading from Breezy, I don't remember, but I'm stuck on the following:

```
eric@zeus:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kcontrol
The following NEW packages will be installed:
  kcontrol
0 upgraded, 1 newly installed, 0 to remove and 50 not upgraded.
119 not fully installed or removed.
Need to get 0B/8026kB of archives.
After unpacking 17.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 146253 files and directories currently installed.)
Preparing to replace desktop-file-utils 0.10-1ubuntu12 (using .../desktop-file-utils_0.10-1ubuntu12_i386.deb) ...
Unpacking replacement desktop-file-utils ...
dpkg: error processing /var/cache/apt/archives/desktop-file-utils_0.10-1ubuntu12_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Operation not permitted
Unpacking kcontrol (from .../kcontrol_4%3a3.5.2-0ubuntu27_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kcontrol_4%3a3.5.2-0ubuntu27_i386.deb (--unpack):
 unable to make backup link of `./usr/lib/kde3/kcm_style.la' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/desktop-file-utils_0.10-1ubuntu12_i386.deb
 /var/cache/apt/archives/kcontrol_4%3a3.5.2-0ubuntu27_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried anything I could to change the permissions of /usr/lib/kde3/kcm_styl.la, hoping for a quick-and-dirty solution:

```

eric@zeus:~$ ls -l /usr/lib/kde3/kcm_style.la
?-ws-wS-wt 65508 4008116194 4293845205 4279242511 1969-12-09 16:42 /usr/lib/kde3/kcm_style.la
eric@zeus:~$ sudo chown root /usr/lib/kde3/kcm_style.la
chown: changing ownership of `/usr/lib/kde3/kcm_style.la': Operation not permitted
eric@zeus:~$ sudo chmod 775 /usr/lib/kde3/kcm_style.la
chmod: changing permissions of `/usr/lib/kde3/kcm_style.la': Operation not permitted

```

So that didn't work.

Aptitude happily offers to delete gnome and what-naught for me, apparently to solve my 119 half-installed packages that are waiting for kcontrol to be fixed.  But that won't do me any good.

Any tips on how I could get kcontrol to install properly?

SigmaX

---

### Post by Bossieman on 2006-07-12
Try this.
> 
eric@zeus:~$ sudo -s -H
root@zeus:~$ chown root /usr/lib/kde3/kcm_style.la


---

### Post by SigmaX on 2006-07-12
Nope.  Same result.

SigmaX

---

### Post by metalheart on 2006-07-12
Try

```
dpkg --purge --force kcontrol
```

and then install kcontrol again.

---

### Post by SigmaX on 2006-07-12
```
root@zeus:/home/eric# dpkg --purge --force-all kcontrol
dpkg: kcontrol: dependency problems, but removing anyway as you request:
 k3b depends on kcontrol; however:
  Package kcontrol is to be removed.
 kde-systemsettings depends on kcontrol; however:
  Package kcontrol is to be removed.
(Reading database ... 146251 files and directories currently installed.)
Removing kcontrol ...
Purging configuration files for kcontrol ...
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/libkshorturifilter.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/libkshorturifilter.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/libkfontviewpart.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/libkfontviewpart.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kstyle_keramik_config.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kio_fonts.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kio_fonts.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kfile_font.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kfile_font.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcontrol.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcontrol.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_xinerama.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_xinerama.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_view1394.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_view1394.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_usb.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_usb.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_taskbar.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_taskbar.la': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_style.so': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing kcontrol, unable to remove directory `/usr/lib/kde3/kcm_style.la': Operation not permitted - directory may be a mount point ?
```

I think I've tried this before anyway.  Kcontrol itself is removed, or at least partially so.  Luckily I like the desktop picture I hae and can live with it for now, but it's still got apt all in a flurry.

SigmaX

---

### Post by SigmaX on 2006-07-12
Hold up.  Could these files be locked when a KDE session is active?  When my CD finishes burning I'll stop X and give it a shot... it's worth a try.

SigmaX

---

### Post by SigmaX on 2006-07-13
Didn't work.

*bump*

SigmaX

---

### Post by SigmaX on 2006-07-16
[didn't solve; reinstalled]

SigmaX

---

