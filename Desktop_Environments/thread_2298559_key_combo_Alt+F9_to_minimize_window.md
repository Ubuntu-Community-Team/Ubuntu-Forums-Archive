---
title: "key combo Alt+F9 to minimize window"
date: 2015-10-12
forum: Desktop Environments
---

### Post by joe.koenig on 2015-10-12
Hi,

I'm new to LXDE (Lubuntu).  I'm trying to figure out how to apply some of the
key-combos I've grown accustumed to from beloved Windowmanager IceWM.

Closest I've gotten so far is:


```
$ tail -n +372 ~/.config/openbox/lubuntu-rc.xml | head -n 6
    <keybind key="W-r">
      <action name="Execute">
        <command>lxpanelctl run</command>
        <comment> NOT lxsession-default launcher_manager</comment>
      </action>
    </keybind>
```

Leaving aside that "W-r"  is not the same a "W-<space>", I'm taking confidence
in that I'm editing the correct config file and that the so called <Super> key
seems to be configurable.

However, I'm still grinding over some other key-combos:
<Alt>-F9         # supposed to minimize a window
<Win>-<arrow>    # supposed to switch to the next desktop

Can you please tell me how to make these work with LXDE?

Regards
Joe


```
$ cat /etc/*-release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

$ uname -a
Linux Jessi 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:12:08 UTC 2015 i686 athlon i686 GNU/Linux

$ dpkg-query -W lubuntu-core
lubuntu-core    0.55
```

---

