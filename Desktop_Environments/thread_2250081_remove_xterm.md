---
title: "remove xterm"
date: 2014-10-26
forum: Desktop Environments
---

### Post by mayagrafix on 2014-10-26
I installed gnome-terminal and now UXTerm and XTerm are redundant. Can I remove them? how? or are they integral to Lubuntu DE? At least how do I remove from Start Menu, as only option available is to change icon which appears under right click contextual menu "Menu" Settings option.

Thanks for your help.

---

### Post by papibe on 2014-10-26
EDIT:

**YOU CAN'T REMOVE xterm in Lubuntu because it is part DE**
```
$ apt-cache depends lubuntu-desktop | grep xterm
  Depends: lxterminal
  **[COLOR="#FF0000"]Depends: xterm[/COLOR]**
    xterm:i386

```
My mistake. I got confused because later vanilla Ubuntu releases don't depend on xterm. It is only a recommended package:
```
$ apt-cache depends ubuntu-desktop |  grep xterm
  Recommends: xterm
    xterm:i386

```


Original post valid only to Ubuntu 14.04
-----------------------------------------------------------------------------------------------------------------------------------------

Hi mayagrafix.

This is the process I would follow:

Get the path of the executables:
```
$ which xterm 
/usr/bin/xterm

$ which uxterm 
/usr/bin/uxterm

```
Now you can get the name of the package the file belongs:
```
$ dpkg -S /usr/bin/xterm
**[COLOR="#FF0000"]xterm[/COLOR]**: /usr/bin/xterm

$ dpkg -S /usr/bin/uxterm
[COLOR="#FF0000"]**xterm**[/COLOR]: /usr/bin/uxterm

```
Since both belong to the same package, called xterm, now you can remove the package. I usually run a simulation before actually doing it:
```
$ sudo apt-get [COLOR="#FF0000"]**-s**[/COLOR] purge xterm
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  xterm*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Purg xterm [297-1ubuntu1]

```
Since it seems just the package and no other library would be removed, I would proceed to remove it:
```
sudo apt-get purge xterm
```
Hope it helps. Let us know how it goes.
Regards.

P.S.: you can combine the 2 first steps with:
```
dpkg -S $(which uxterm) $(which xterm)
```

---

### Post by vasa1 on 2014-10-26
> **mayagrafix said:**
> I installed gnome-terminal ...
Why did you install gnome-terminal? Is there some feature it provides that the default lxterminal doesn't?

By the way, if you don't want to uninstall software but just keep it from appearing in typical menus, you could add a line with **NoDisplay=true** to the end of that particular .desktop file. See [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html) for more on .desktop files.

---

