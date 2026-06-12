---
title: "&quot;VFS: Can't find ext3 filesystem on dev&quot; message"
date: 2005-05-18
forum: Desktop Environments
---

### Post by dninja on 2005-05-18
Everytime I boot I get the following message just before the init scripts are ran:

VFS: Can't find ext3 filesystem on dev hda9.

The message is correct as hda9 is reiser fs and appears as the following in my fstab:

/dev/hda9       /               reiserfs defaults       0       1

It gets mounted correctly anyway so there doesn't seem to be an actual problem anywhere.

I also get this message laptop which is setup the same.

Can anyone suggest what is causing this?

---

### Post by jeremy on 2005-05-18
I have no idea why it gives this message, but wanted to let you know that I have seen the same, as in your case everything seems to work well and unaffected by this.

---

