---
title: "Problem with keyboard shortcuts on Ubuntu 14.04 + Gnome Session Fallback (Metacity)"
date: 2014-04-18
forum: Desktop Environments
---

### Post by Leandro_Ishi on 2014-04-18
Hello,

I've been searching for this problem through Web, but could not find any solution. It is kinda weird. I have Ubuntu 14.04 and installed Gnome Session Fallback because I like Gnome classic more than unity. I use Gnome Metacity as manager and everything works fine, except that I can't use shortcut to show desktop (super + d does not work, nor ctrl + alt + d, or alt + d, etc...). However, alt+tab works to switch apps, ctrl+alt+arrows works to switch workspace, etc... Everything seems fine, except show desktop shortcut. When I go to system preferences > keyboard > keyboard shortcuts, there is no "Navigation" menu so that I can configure a shortcut to "show desktop". 

Anyone can help me out?

Thanks in advance.

---

### Post by kansasnoob on 2014-04-19
I encountered a similar problem:

[http://ubuntuforums.org/showthread.php?t=2217817](http://ubuntuforums.org/showthread.php?t=2217817)

For me it was "run-panel-dialog", but some of the flashback w/metacity default keybindings aren't set properly.

Anyway, if you install 'dconf-tools' you'll then find dconf Editor in System Tools. Then navigate to org > gnome > desktop > wm > keybindings and you'll find show desktop:

[ATTACH=CONFIG]252213[/ATTACH]

You should just be able to click on Set to Default.

But I think that's a bug :confused:

I need to check that behavior in Edubuntu, if it's messed up there I'll probably file a bug report.

---

### Post by Leandro_Ishi on 2014-04-19
Hello Kansasnoob,

Thank you. Thank you very much. It worked right away and I really appreciated it.

Thanks a lot!

---

### Post by jan123 on 2014-08-03
The bug has been filed:
[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/1073393](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/1073393)

I added a reference to this thread

---

