---
title: "Debian menu item not showing under Applications"
date: 2006-10-24
forum: Desktop Environments
---

### Post by johnusa on 2006-10-24
In an effort to find out where my installed application were, I installed the package "menu-xdg" via synaptic.  I rebooted and the menu item "Debian" did not show up under the Applications menu.  I then issued the following command as a root user:
```
dpkg-reconfigure menu-xdg
```
I rebooted and still no "Debian" menu item under Applications.  Can anyone provide help in resolving this problem.  I am relatively new to Ubuntu.  Thank you in advance for any assistance.

---

### Post by johnusa on 2006-10-24
I later started **synaptic** from the shell prompt, right-clicked **menu-xdg** in the list and selected **properties.**  I then selected the **Dependencies** tab.  Under the dependencies tab there was a drop-down list.  Under both the **Dependencies** item in the list and the **Dependencies of the Latest Version** items in the drop-down list was the following text:
```
Recommends: *menu*
Conflicts: *menu*
```
I am including this as it may provides someone with a clue as to what the problem is in getting the **Debian** menu item to appear under the **Applications** menu item.

---

### Post by tturrisi on 2006-10-24
The Debian menu package is called "menu", so do:
$apt-get install menu

menu-xdg:
[http://packages.debian.org/unstable/admin/menu-xdg](http://packages.debian.org/unstable/admin/menu-xdg)
-freedesktop.org menu compliant window manager scripts-
menu-xdg contains menu-methods to convert the Debian menu structure to the freedesktop.org xdg menu structure.

---

### Post by johnusa on 2006-10-24
Thank you for your input.

I issued the following command:
```
apt-get install menu
```
and received the following output:
```
127:/usr/local/apache2/bin# apt-get install menu
Reading package lists... Done
Building dependency tree... Done
Package menu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package menu has no installation candidate
root@johni-desktop
127:/usr/local/apache2/bin#

```
Any suggestions?

---

### Post by kerry_s on 2006-10-24
Did you turn all the repos on?

---

### Post by johnusa on 2006-10-24
Thank you kerry_s for your reply.  I turned on all the repositories and was able to issue the "apt-get install menu" command successfully.  I now have the Debian menu item under the Applications menu.  Unfortunately, none of the applications that I was looking for could be found under the Debian menu.

[LIST=1]
[*]I was supprised at the number of downloads that occurred when I enable all repositories.  If I want to disable all of the additional repositories that I enabled, will all of the additional packages that were downloaded be automatically removed from the synaptic package manager list as well as my machine?  If not, then how do I get rid of them and revert back to the state in which I had only the main repository enabled?

[*]Is there a way to issue the apt-get install command to retrieve a package that is not in the main repository without have to enable all repositories.  I was wondering if I could specify a list of repositories to search on the command line without having to enable them in Ubuntu so I would only get the package I wanted to install and nothing else.
[/LIST]
Thanks again for any comments.

---

### Post by Zorlin on 2006-10-27
Thank you to all.
This saved me from posting a new thread.
:D
Go ubuntu!
Go the ubuntu forums! :P

---

