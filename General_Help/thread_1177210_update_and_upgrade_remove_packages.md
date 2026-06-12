---
title: "update and upgrade remove packages?"
date: 2009-06-03
forum: General Help
---

### Post by Wangberg on 2009-06-03
i execute command 

```

sudo apt-get update && sudo apt-get upgrade

```

and it looks like nothing is being update and packages are actually being removed:

```

W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  exiv2{u} kde-icons-oxygen{u} kdebase-runtime{u} 
  kdebase-runtime-bin-kde4{u} kdebase-runtime-data{u} 
  kdebase-runtime-data-common{u} kdelibs-bin{u} kdelibs5{u} 
  kdelibs5-data{u} kdemultimedia-kio-plugins{u} khelpcenter4{u} 
  language-support-fonts-zh{u} language-support-translations-zh{u} 
  libatk1.0-dev{u} libavahi1.0-cil{u} libboo2.0-cil{u} libcairo2-dev{u} 
  libclucene0ldbl{u} libdirectfb-dev{u} libdirectfb-extra{u} libexiv2-5{u} 
  libgda3-3{u} libgda3-bin{u} libgda3-common{u} libgdl-1-0{u} 
  libgdl-1-common{u} libgtk2.0-dev{u} libkcddb4{u} libloudmouth1-0{u} 
  libmono-zeroconf1.0-cil{u} libnotify0.4-cil{u} libpango1.0-dev{u} 
  libpixman-1-dev{u} libsoprano4{u} libstreamanalyzer0{u} libstreams0{u} 
  libsysfs-dev{u} libtaglib2.0-cil{u} libtre4{u} libxcb-render-util0-dev{u} 
  libxcb-render0-dev{u} libxcomposite-dev{u} libxdamage-dev{u} 
  openoffice.org-help-zh-cn{u} openoffice.org-help-zh-tw{u} 
  openoffice.org-l10n-zh-cn{u} openoffice.org-l10n-zh-tw{u} podsleuth{u} 
  python-cddb{u} python-gamin{u} python-gnome2-extras{u} python-gpod{u} 
  python-mutagen{u} scim-dev-doc{u} soprano-daemon{u} streamripper{u} 
  thunderbird-locale-zh-cn{u} thunderbird-locale-zh-tw{u} ttf-wqy-zenhei{u} 
  x11proto-composite-dev{u} x11proto-damage-dev{u} xfonts-wqy{u} 
0 packages upgraded, 0 newly installed, 62 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 260MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
wangberg@dino:~$ aptitude

```

am i missing something?

---

### Post by colau on 2009-06-03
> **Wangberg said:**
> i execute command 

```

sudo apt-get update && sudo apt-get upgrade

```

and it looks like nothing is being update and packages are actually being removed:

```

W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  exiv2{u} kde-icons-oxygen{u} kdebase-runtime{u} 
  kdebase-runtime-bin-kde4{u} kdebase-runtime-data{u} 
  kdebase-runtime-data-common{u} kdelibs-bin{u} kdelibs5{u} 
  kdelibs5-data{u} kdemultimedia-kio-plugins{u} khelpcenter4{u} 
  language-support-fonts-zh{u} language-support-translations-zh{u} 
  libatk1.0-dev{u} libavahi1.0-cil{u} libboo2.0-cil{u} libcairo2-dev{u} 
  libclucene0ldbl{u} libdirectfb-dev{u} libdirectfb-extra{u} libexiv2-5{u} 
  libgda3-3{u} libgda3-bin{u} libgda3-common{u} libgdl-1-0{u} 
  libgdl-1-common{u} libgtk2.0-dev{u} libkcddb4{u} libloudmouth1-0{u} 
  libmono-zeroconf1.0-cil{u} libnotify0.4-cil{u} libpango1.0-dev{u} 
  libpixman-1-dev{u} libsoprano4{u} libstreamanalyzer0{u} libstreams0{u} 
  libsysfs-dev{u} libtaglib2.0-cil{u} libtre4{u} libxcb-render-util0-dev{u} 
  libxcb-render0-dev{u} libxcomposite-dev{u} libxdamage-dev{u} 
  openoffice.org-help-zh-cn{u} openoffice.org-help-zh-tw{u} 
  openoffice.org-l10n-zh-cn{u} openoffice.org-l10n-zh-tw{u} podsleuth{u} 
  python-cddb{u} python-gamin{u} python-gnome2-extras{u} python-gpod{u} 
  python-mutagen{u} scim-dev-doc{u} soprano-daemon{u} streamripper{u} 
  thunderbird-locale-zh-cn{u} thunderbird-locale-zh-tw{u} ttf-wqy-zenhei{u} 
  x11proto-composite-dev{u} x11proto-damage-dev{u} xfonts-wqy{u} 
0 packages upgraded, 0 newly installed, 62 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 260MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
wangberg@dino:~$ aptitude

```

am i missing something?
What happens after this
```

sudo apt-get dist-upgrade

```

---

### Post by mhgsys on 2009-06-03
check out these pages, looks like a bug.

```
https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/147780
```

```
https://bugs.launchpad.net/ubuntu/+source/bash/+bug/128575
```

edit: also colau properly ment sudo apt-get dist-upgrade

---

### Post by Wangberg on 2009-06-03
```

wangberg@dino:~$ sudo apt-get dis-upgrade
E: Invalid operation dis-upgrade

```

---

### Post by colau on 2009-06-03
> **Wangberg said:**
> ```

wangberg@dino:~$ sudo apt-get dis-upgrade
E: Invalid operation dis-upgrade

```
It is 
```

sudo apt-get dist-upgrade

```

---

### Post by Wangberg on 2009-06-03
> **mhgsys said:**
> check out these pages, looks like a bug.

```
https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/147780
```

```
https://bugs.launchpad.net/ubuntu/+source/bash/+bug/128575
```

edit: also colau properly ment sudo apt-get dist-upgrade

these bugs are from 2007 and mid-2008, with the patch attached...surely this bug would have been fixed for 9.04, right?  additionally when i tab twice after i type aptitude, "full-upgrade" and "safe-upgrade" appear.  i don't think this bug refers to my problem of apt-get trying to remove packages when i execute update and upgrade commands.  

thanks

---

### Post by Wangberg on 2009-06-03
> **colau said:**
> It is 
```

sudo apt-get dist-upgrade

```

my bad....carelessly overlooked my typo

```

wangberg@dino:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wangberg@dino:~$ 

```

---

### Post by mhgsys on 2009-06-03
I overlooked which  version of ubuntu your using,. 
Making my post entirely useless. 
lol. Sorry to waste your time.

Need to wake up a little, 
Coffee, that's what beans are for.

---

