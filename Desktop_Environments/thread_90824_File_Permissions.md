---
title: "File Permissions"
date: 2005-11-15
forum: Desktop Environments
---

### Post by pja on 2005-11-15
I have just installed "Breezy Badger" and it is great; Ubuntu is just getting better ad better.

I have a large number of files to copyover from a WinXP volume (hda1) and am looking for a tool that will allow me to set the permissions on all the files in a directory tree - ie. the tool wil ripple through the directory changing permissions on all underlying filesand directories.

Another query while I'm here; the 'Applications' menu no longer has a 'run' option, can anyone advise on how to add this.

Thanks in advance,

Peter :confused:

---

### Post by Remmelas on 2005-11-15
not sure about the applications menu, and don't know of a gui that will do recursive permissions like you are talking about, but at the command line, you can use chmod -R to do recursive permissions modifications, for example to drop the cursed executable permission that all windows files have, you can do chmod -R a-x /path/to/directory
and that will remove exec (x) from all (a) permissions groups(user, group, and other)

---

