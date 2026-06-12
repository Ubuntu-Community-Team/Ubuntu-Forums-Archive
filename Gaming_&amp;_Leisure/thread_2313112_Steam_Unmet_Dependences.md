---
title: "Steam Unmet Dependences"
date: 2016-02-09
forum: Gaming &amp; Leisure
---

### Post by justinvermeer8 on 2016-02-09
I keep getting a terminal pop-up when opening steam saying

```
Steam needs to install these additional packages:     libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386

```

When i put in my P/W i get this message, any attempt to apt-get install any of these dependencies results in more dependency issues

```
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.6)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



```



Ubuntu 14.04 x64

---

### Post by justinvermeer8 on 2016-02-09
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install steam[/FONT][/COLOR]
```

This command fixed it all.

For those who used the .deb file from the steam website, be sure to run this command afterwords and accept the uela :)

Sorry for taking up space
:D :P

---

### Post by Vladlenin5000 on 2016-02-10
> **justinvermeer8 said:**
> ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install steam[/FONT][/COLOR]
```

This command fixed it all.

For those who used the .deb file from the steam website, be sure to run this command afterwords and accept the uela :)

Sorry for taking up space
:D :P

Actually no... Just run the command and it'll install Steam. No need to download from Steam directly. Once installed just run it and it'll download and install all the required updates.

---

