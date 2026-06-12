---
title: "package &quot;ubuntu-wallpapers-extra&quot;"
date: 2010-11-20
forum: Desktop Environments
---

### Post by Skaperen on 2010-11-20
I have found that the package "ubuntu-wallpapers-extra" appears to be the culprit in imposing a system-wide new default of a particular wallpaper background image on all users (both those already added and those yet to be added) as well as the login screen.  It can be overridden.  The problem is, it has to be overridden.

Anyone know of a way I can block any such changes from happening?  If not that, what about a tool that will automatically revert such changes.  The goal is so that users (and the login context) won't need an explicit background image to be set and when so, will get the image that was the default at install time.

---

### Post by Frogs Hair on 2010-11-20
This bug may be related . [https://bugs.launchpad.net/ubuntu/+source/ubuntu-wallpapers-extra/+bug/569202](https://bugs.launchpad.net/ubuntu/+source/ubuntu-wallpapers-extra/+bug/569202)

---

### Post by Skaperen on 2010-12-10
I've been building a set of scripts to "mod" my system after I install a distribution.  I figured out where the problem was and made the following script to fix it, invoked after the script that installs "ubuntu-wallpapers-extra":

```
#!/bin/bash
fix_bg_image() {
    file="/var/lib/gconf/debian.defaults/%gconf-tree.xml"
    ln -fv "${file}" "${file}".old || return 1
    sed 's/WhiteOrchid\.jpg/warty-final-ubuntu.png/' < "${file}".old > "${file}".new || return 1
    if cmp "${file}".old "${file}".new ; then
        rm -fv "${file}".new
    else
        mv -fv "${file}".new "${file}" || return 1
    fi
    rm -fv "${file}".old || return 1
    return 0
}
fix_bg_image || echo "Failed to fix default background image configuration" 1>&2
```If uninstalling "ubuntu-wallpapers-extra" fixes it, too, then it must have some uninstall script that takes reverts "/var/lib/gconf/debian.defaults/%gconf-tree.xml" back to its previous contents, at least for that item.  That would suggest the package builder knows this is happening.

---

