---
title: "X won't start after apt-get upgrade"
date: 2005-07-14
forum: Desktop Environments
---

### Post by jvantslot on 2005-07-14
Hi all,

Yesterday I ran an apt-get upgrade and today X fails to start... the log file says it can't find the following drivers: nv, keyboard and mouse.

Anyone else experiencing this issue and if so what's the fix?

james

---

### Post by Curlydave on 2005-07-14
[QUOTE=jvantslot]Hi all,

Yesterday I ran an apt-get upgrade and today X fails to start... the log file says it can't find the following drivers: nv, keyboard and mouse.

Anyone else experiencing this issue and if so what's the fix?

james[/QUOTE]

Welcome to Linux! Been there, done that, reformatted. Your issue sounds fixable though, if you can use VI to fix the file.

---

### Post by varunus on 2005-07-14
Can you post your xorg.conf?  i don't think there was an X update yesterday...Did you install a new kernel?  If you did, what happens if you boot the old kernel?  Were you using the proprietary nvidia drivers before upgrading yesterday?

---

### Post by jvantslot on 2005-07-15
I'm just using the nv driver.  I ran apt-get dist-upgrade again today and it installed a BUNCH of xorg stuff.  So today the error is different.  Now it just says it can't find the keyboard driver.  So it looks like it's getting there but still mising stuff.  Could it have un-installed a file to meet some dependency?  If so what file might contain such files as the keyboard driver?

One question about Ubuntu... when a new version of a file like xorg.conf wants to be installed, it doesn't do it because it says mines been modified (I've switched back and forth with the nv and nvidia drivers).  Where does it put the new file if it doesn't over write my old?  I'd like to do a diff on the files and see what's changed.  In RPM based distros the file usually ends up named something like xorg.conf.rpm-new or something similar.

james

---

### Post by maruchan on 2005-07-15
Heh, it looks like you should be posting your messages in the breezy badger forum now, since you did a dist-upgrade  :)

---

