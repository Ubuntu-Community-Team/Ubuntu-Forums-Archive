---
title: "I shared a folder from Gnome, then deleted that user."
date: 2010-12-10
forum: Desktop Environments
---

### Post by alfadog67 on 2010-12-10
Hi - this is my first post.

I logged in as user1 with administrative privileges.
I right-clicked on a folder on my desktop, then "Sharing Options", then shared the folder as "docs".
Then I created a new user with administrative privileges, user2, and logged in as that user.
Then, I deleted user1 - account settings, and files.
Then I created a folder on my desktop and tried to share it as "docs", but I get the following error:

'net usershare' returned error 255: net usershare add: failed to add share docs. Error was Operation not permitted

I can share the folder as any other name, just not "docs".

My smb.conf file doesn't contain the entry.

I'd love to know where the configuration file is that's hi-jacked the name "docs".

Thanks for your input!

---

### Post by alfadog67 on 2010-12-11
I found the answer...
I tried grepping for files containing the share name, but the share name is actually the name of the file rather than in thi contents of a file.

Here's where the share is stored:
/var/lib/samba/usershares

Thanks for looking!

---

