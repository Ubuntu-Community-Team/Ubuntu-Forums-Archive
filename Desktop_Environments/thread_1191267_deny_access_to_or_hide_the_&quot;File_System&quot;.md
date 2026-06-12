---
title: "deny access to or hide the &quot;File System&quot; from &quot;Open Files&quot;"
date: 2009-06-18
forum: Desktop Environments
---

### Post by chang5562 on 2009-06-18
When user opens a program, ex Gedit, which can access the files, from File --> Open, the open dialogue includes not only the user's home directory, but also all the storage sources (DVD, CD, or floppy drive) and the "File System".  How can I deny the user to open or even to view the "File System"?

Where is the script control the dialogue?

I unchecked the show_desktop value under the /app/nautilus/preferences, it would forbid me to drag the executable file from File System to desktop (then I can run it).  However, this change disallowed the external USB device pupped up the media label on the desktop, even it still mounts it, and I could not discharge the CD from USB CD drive.

Is there another way to hide the "File System"?

try the .hidden method, only worked for nautilus.

---

