---
title: "Editors write empty files over gvfs mounts"
date: 2010-10-11
forum: Desktop Environments
---

### Post by vordan on 2010-10-11
I just updated to version 10.10 and a serious issue appeared.
As a developer, I access my company's server shared folders via Nautilus and ssh (sftp) mounts (using gvfs).
Everything was working fine before the upgrade, but suddenly, when I open a file from the server, **make some changes to it and write it back, the file size is 0 bytes**! Luckily, we have backups, otherwise it would have been a real disaster!.

My main editor is Geany, but same happens with any other I've tried (Gedit, Leafpad, Komodo Edit ...)
I found a similar problem being reported on Launchpad (
[Eclipse writes empty files over gvfs]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs/+bug/658069")), but no answers there yet.

If a solution is not being found soon, I'll have to regress and install 10.04, or even 9.10.

This happened on my Dell Inspiron 1764 laptop. Luckily, my desktop computers at work and home and my other laptop are still with the old version...

---

### Post by habl on 2010-10-12
I got the exact same problem, didn't find a way to get around it yet :s

---

### Post by habl on 2010-10-12
Solution:
~/.config/geany/geany.conf and changed use_safe_file_saving from FALSE to TRUE, after that the remote saving worked.

Found in:
[https://bugs.launchpad.net/ubuntu/+source/geany/+bug/643253](https://bugs.launchpad.net/ubuntu/+source/geany/+bug/643253)

---

### Post by dawez on 2010-10-12
Same thing happens with IntelliJ Idea and other few editors. It seems to me that also the permission got screwed, am I right ?

---

### Post by habl on 2010-10-12
Not sure, sounds more like a bug in gvfs. No idea how to work around it in other ide's. Try following this bug report aswell: [https://bugs.launchpad.net/ubuntu/+source/gnome-vfs/+bug/658069](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs/+bug/658069)

---

### Post by qbxk on 2010-10-12
has to be something related to gvfs itself for all these editors to be involved.  i'm using SciTE and it's also saving empty files :mad:  very surprising

just for fun, i cd'd my way into the gvs path and edited a file using vi, lo and behold it worked!  (what can't vi do?), however nano also saved an empty file.  amazing.

anybody find a bug report that is not editor-specific?

edit: posted too soon, the workaround to fix SciTE (if i'm not the only one as it seems i may be...), is to in your Global Options file (SciTEGlobal.properties) set

```
save.deletes.first=1
```

edit 2: this has the unfortunate side effect of resetting permissions on the file you're saving. :mad:
also, FTR i had added myself to the fuse group, and that may be necessary

---

### Post by vordan on 2010-10-13
> **habl said:**
> Solution:
~/.config/geany/geany.conf and changed use_safe_file_saving from FALSE to TRUE, after that the remote saving worked.

Found in:
[https://bugs.launchpad.net/ubuntu/+source/geany/+bug/643253](https://bugs.launchpad.net/ubuntu/+source/geany/+bug/643253)

Thanks, this works for me. 
As I understand, it's a workaround, not a solution to the problem (which is, by all accounts, in gvfs).
But, it'll do for now.


BTW, a tip: 
I keep my Geany, Nautilus, SSHmenu, OpenOffice and some other configs into my Dropbox folder.
I just make a symlink from there to the places where the programs expect their config files.

That way, on all my computers I have exact same configurations for the key programs I use every day. When I make some adjustment, I can be sure that it will be available immediately everywhere!

---

### Post by vordan on 2010-10-18
This issue appears to be solved with today's (18 Oct 2010) update of Nautilus.
I tested with multiple editors and everything worked fine.

Oddly, the Geany setting [use_safe_file_saving=true] must remain in place, otherwise it still doesn't work.

EDIT: It doesn't work with UEX.

---

