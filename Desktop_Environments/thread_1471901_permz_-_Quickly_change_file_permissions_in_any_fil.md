---
title: "permz - Quickly change file permissions in any file manager"
date: 2010-05-03
forum: Desktop Environments
---

### Post by IgnorantGuru on 2010-05-03
Designed to be integrated into any file manager, permz is a bash script which presents a GUI menu.  You can use it to quickly change file permissions and ownership as a normal user or as root, and delete files as root.  I wrote this because I have yet to see a file manager that isn't cumbersome for this - the mechanism is usually buried on a second tab of the Properties window, and changing permissions often involves multiple clicks in a grid. To change the owner of a file, you need to type the username. And if the file is owned by root, you can’t do anything.

[[img]http://ignorantguru.users.sourceforge.net/downloads/screenshot-permz.png[/img]](http://igurublog.wordpress.com/downloads/script-permz/)

```
permz --help

Presents a menu for changing file permissions/ownership.  May be run as
normal user or root.
Requires: zenity gksu
Optional: sudo (recommended to prevent multiple root password prompts)
Usage: permz FILE [...]

MENU FUNCTIONS:
rwxrwxrwx            Sets file(s) to given permissions
Sticky Clear/Set     Performs "chmod -t" or +t to clear or set the sticky
                     bit.  You may select to clear/set sticky in addition
                     to changing other permissions.
Recursive go-rxw     "chmod -R go-rxw" on file(s) recursively, denying
                     access to non-owners
Recursive go-w       "chmod -R go-w" on file(s) recursively, denying write
                     to non-owners
Recursive ugo+r (dirs +x)
                     "chmod -R ugo+r" giving read access to all.  Also
                     sets +x for directories (allow directory entry).
Recursive ugo+w      "chmod -R ugo+w" on file(s), giving write to all
(You may select several compatible recursive functions above at once)
Owner USER As ROOT   Sets ownership to USER:USER as root
DELETE As ROOT       Deletes file(s) as root.  Must be used alone or with
                     "Perform Recursively" (to delete directories - USE
                     WITH CAUTION). Not available if permz is run as root.
Perform As ROOT      Run as root to change selected permissions.
                     (Use of root is automatic when changing ownership)
Perform Recursively  Adds -R to all chmod, chown, and delete commands to
                     descend into subdirectories.  Use in conjunction with
                     any other functions.  (Recursion is automatic for
                     "Recursive" functions above)

Current su command is set to: gksu -gS
```

If you're somewhat familiar with bash, adding additional options or changing the existing ones is straightforward.

I have tested it pretty thoroughly but if you do encounter anything amiss please let me know.

More details and instructions at [http://igurublog.wordpress.com/downloads/script-permz/](http://igurublog.wordpress.com/downloads/script-permz/)

Instructions for integrating permz into PCManFM-Mod are [_here_](http://igurublog.wordpress.com/downloads/mod-pcmanfm/#examplepermz).

---

