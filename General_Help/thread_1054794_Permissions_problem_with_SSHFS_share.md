---
title: "Permissions problem with SSHFS share"
date: 2009-01-30
forum: General Help
---

### Post by lightnb on 2009-01-30
I have my web hosting account mounted to my local machine using SSHFS.

Using Nautilus, I can delete files off of the remote server as if they were local files. I can also create new files without problems.

However, if I open a file in an editor, make changes, and try to save over the existing file, I get a permission denied error. This happens in every editor I've tried. I can get around the problem by opening the file in an editor, deleting it off the server, making the change and then saving it to the server again (which basically creates a new file with the same name in the same place), but this is very annoying.

My local permissions tab say the remote files are owned by "32451" and group "17362", and I am "not the owner so I can't change these permissions".

Trying to chown or chgrp them fails as well, even as root.

Anyone know a workaround?

Thanks,

Nick

---

