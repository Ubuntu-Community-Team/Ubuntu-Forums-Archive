---
title: "thunar actions only on local drive"
date: 2011-12-02
forum: Desktop Environments
---

### Post by breek on 2011-12-02
is this a bug or a feature?
if i right-click files or folders on local drives i see default (open terminal) and custom thunar actions but when doing the same on samba shares (something like smb://192.168.1.111/mysambafolder) i see none of them.
the other stuff works as i can read and delete all my files on that network drive.
a workaround could be open "/home/user/.gvfs/mysambafolder on 192.168.1.111" to fool thunar but i don't like it so much...

tested on ubuntu studio 11.10 with custom actions and on xubuntu 11.04 with no custom action added

---

### Post by LewisTM on 2011-12-02
Any custom SendTo items are also ignored, including the ones packaged with Xubuntu (Printer, Mail recipient, etc).
Should be a bug because it's all there in the .gvfs directories.
Personally I bookmarked .gvfs, calling it 'File Shares'. It's useful for those applications that are not aware of gvfs mounts, like Firefox or Thunderbird. 
In Thunar, it also adds the benefit of tree navigation, which is not offered for smb://, [ftp://,](ftp://,) etc. locations.
Hopefully the next version will show mounted shares on the tree pane like Nautilus and treat everything the same.

---

### Post by breek on 2011-12-03
i wrote about it [here]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/899624").
if you have a launchpad account please click on "This bug affects 1 person. Does this bug affect you?" ;)

---

### Post by LewisTM on 2011-12-03
Done.
Thanks for submitting the bug! Please post back if a solution is found.

---

### Post by breek on 2011-12-03
of course! thanx ;)

---

