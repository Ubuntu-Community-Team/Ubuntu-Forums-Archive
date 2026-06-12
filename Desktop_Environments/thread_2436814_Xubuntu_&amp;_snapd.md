---
title: "Xubuntu &amp; snapd"
date: 2020-02-13
forum: Desktop Environments
---

### Post by richolad-k on 2020-02-13
Does Xubuntu 19.10 include any snap packages?  Will it download any if I  install new packages?  What is the distro's plan for the future  regarding snapd?

---

### Post by The Cog on 2020-02-13
I know chromium-browser is only available in a snap package from 19.10 onwards. I gather most other packages are not forcing you to use snap yet. I think the distro's plan is for more snap packages but haven't seen any official statements to that effect. I don't know if they plan to force users to use snap in general, or to offer both packages ongoing.

EDIT: I corrected 10.10 onwards to 19.10 onwards (typo)

---

### Post by richolad-k on 2020-02-13
OK.  You have the same questions I do, then.  I'll await more responses.  Disregard that -- I have just learned that Xubuntu includes snapd, and that removing all snaps and/or ensuring it remains snap-free is difficult.  This means it is not what I want.

---

### Post by The Cog on 2020-02-13
**sudo apt purge snapd** seemed to do it for me. I haven't seen them come back yet.

---

### Post by TheFu on 2020-02-13
> **The Cog said:**
> I know chromium-browser is only available in a snap package from 10.10 onwards. I gather most other packages are not forcing you to use snap yet. I think the distro's plan is for more snap packages but haven't seen any official statements to that effect. I don't know if they plan to force users to use snap in general, or to offer both packages ongoing.

I suspect you mean 17.10 for the chromium-browser snap, not 10.10?

Hope this is useful for someone.  No non-LTS stuff, like 19.10 here. Sorry.

On an 18.04 machine:
```
snap list
```
should show any installed snap packages.  If that command isn't found, then none are installed.
```
$ snap list
Name               Version          Rev   Tracking  Publisher   Notes
chromium           80.0.3987.100    1026  stable    canonicalâ  -
chromium-ffmpeg    0.1              15    stable    canonicalâ  -
core               16-2.43.2        8592  stable    canonicalâ  core
core18             20200124         1668  stable    canonicalâ  base
gtk-common-themes  0.1-28-g1503258  1440  stable    canonicalâ  -
snapd              2.43.2           6240  stable    canonicalâ  snapd

$ sudo snap remove chromium chromium-ffmpeg core core18 gtk-common-themes snapd
error: cannot remove "chromium", "chromium-ffmpeg", "core", "core18",
       "gtk-common-themes", "snapd": snap "core" is not removable: snap is used
       by the model

```
Removing the DEB package for snapd looks possible.  Doing that removes all the snaps too!
```
$ sudo apt purge snapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  snapd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 65.3 MB disk space will be freed.
Do you want to continue? [Y/n] Y
```
I answered yes! seemed to work **and removed all snaps**.

```
$ sudo apt install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  adwaita-icon-theme at-spi2-core chromium-browser-l10n
_....   ABOUT 3 PAGES OF PACKAGE LISTS ... _
0 upgraded, 149 newly installed, 0 to remove and 0 not upgraded.
Need to get 103 MB of archives.
After this operation, **616 MB** of additional disk space will be used.
Do you want to continue? [Y/n] N   HELL NO!!!!

$ sudo apt install **--no-install-recommends** chromium-browser
.....
0 upgraded, 74 newly installed, 0 to remove and 0 not upgraded.
Need to get 66.4 MB of archives.
After this operation, **255 MB** of additional disk space will be used.
Do you want to continue? [Y/n] Y
....
74% [74 chromium-browser 31.1 MB/**52.1 MB** 60%]                    1,626 kB/s 12s
....

```

After all that, 
```
$ snap info

Command 'snap' not found, but can be installed with:

sudo apt install snapd

$ dpkg -l |grep chromium
ii  chromium-browser   **65.0.3325.181-0ubuntu1**    amd64  Chromium web browser, open-source version of Chrome

```
But **79.0.3945.130-0ubuntu0.16.04.1** is the current version on my 16.04 desktop systems.  Seems Chromium has been abandoned as a deb package on 18.04.  

Firefox it will be.  Good news, Firefox in the 18.04 .deb repos looks to be current.  **73.0+build3-0ubuntu0.18.04.1**

---

### Post by CatKiller on 2020-02-13
> **TheFu said:**
> Seems Chromium has been abandoned as a deb package on 18.04.

Chromium from [a PPA](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta) is preferable anyway, because of the VA-API support.

---

