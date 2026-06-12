---
title: "Messed up language on Gnome - 2 languages at the same time"
date: 2008-07-20
forum: Desktop Environments
---

### Post by BEaSTFX on 2008-07-20
I have 2 lang for example my start panel is english but the submenus are in bulgarian.Right click is english control panel is bulgarian.....
Notice that Priority is **not obligatory**

Result of  **locale**```
beastfx@16431879199042:~$ locale
LANG=bg_BG.UTF-8
LC_CTYPE="bg_BG.UTF-8"
LC_NUMERIC="bg_BG.UTF-8"
LC_TIME="bg_BG.UTF-8"
LC_COLLATE="bg_BG.UTF-8"
LC_MONETARY="bg_BG.UTF-8"
LC_MESSAGES="bg_BG.UTF-8"
LC_PAPER="bg_BG.UTF-8"
LC_NAME="bg_BG.UTF-8"
LC_ADDRESS="bg_BG.UTF-8"
LC_TELEPHONE="bg_BG.UTF-8"
LC_MEASUREMENT="bg_BG.UTF-8"
LC_IDENTIFICATION="bg_BG.UTF-8"
LC_ALL=
```
 
 
Result **sudo aptitude show language-support-bg**
```
beastfx@16431879199042:~$ sudo aptitude show language-support-bg
Package: language-support-bg
State: installed
Automatically installed: yes
Version: 1:8.04+20080214
Priority: not obligatory
Section: translations
Maintainer: Language pack maintainers <language-packs@ubuntu.com>
Uncompressed Size: 32,8k
Depends: language-support-translations-bg, language-support-writing-bg
Recommends: language-pack-bg
Description: metapackage for Bulgarian language support
 This metapackage depends on all packages that provide native language support
 for applications. (like spell checkers, dictionaries, OpenOffice and Mozilla
 locale packages, etc.). 
 
 If you also want your applications and the desktop to be translated, please
 additionally install language-pack-bg. 
 
 Language: Bulgarian
```

**/etc/environment**

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="bg_BG:bg"
LANG="bg_BG.UTF-8"
```

**/etc/default/locale**
```
LANG="bg_BG.UTF-8"
LANGUAGE="bg_BG:bg"
```


All seems right to me so tell me what's wrong.

---

