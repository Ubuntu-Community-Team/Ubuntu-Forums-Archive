---
title: "Problems installing dwarf fortress , lubuntu 64bit ( ubuntu )"
date: 2012-12-09
forum: Gaming &amp; Leisure
---

### Post by gogic on 2012-12-09
Am trying to install DW and am following two guides :
1. [http://dwarffortresswiki.org/index.php/DF2012:Installation](http://dwarffortresswiki.org/index.php/DF2012:Installation)
2. [http://blog.isja.org/index.php?/archives/81-Setting-up-Dwarf-Fortress-in-64bit-Debian.html](http://blog.isja.org/index.php?/archives/81-Setting-up-Dwarf-Fortress-in-64bit-Debian.html)
3. [https://github.com/haesken/dwarf_fortress_auto](https://github.com/haesken/dwarf_fortress_auto)

Tried 3. and looks like it's broken 

```

....
Traceback (most recent call last):
  File "<string>", line 176, in <module>
  File "<string>", line 151, in main
  File "develop/build/pyi.linux2/df_install/out00-PYZ.pyz/dfa_df", line 99, in install_dwarf_fortress
  File "develop/build/pyi.linux2/df_install/out00-PYZ.pyz/dfa_df", line 58, in copy_libgl
IndexError: list index out of range
```

Tried 1. and 2. and i get problem when i need to install 32bit libs on 64bit ubuntu .

```
sudo apt-get install ia32-libs ia32-libs-gtk
```

```
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.

```

Am stuck, can somone help ?

---

### Post by mzrk7 on 2012-12-10
what version of lubuntu are you using?

---

### Post by mzrk7 on 2012-12-10
this old post is about your same issue. And offers some solution. 

[http://ubuntuforums.org/showthread.php?t=1880965](http://ubuntuforums.org/showthread.php?t=1880965)

---

