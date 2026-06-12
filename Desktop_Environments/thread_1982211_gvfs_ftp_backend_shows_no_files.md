---
title: "gvfs ftp backend shows no files"
date: 2012-05-18
forum: Desktop Environments
---

### Post by Newbunto on 2012-05-18
The gvfs ftp backend shows no files for me even though I know that there are files. It will however correctly create a new file (which then promptly is also invisible).

I believe that the problem here is that the gvfs ftp backend assumes that sending an FTP "LIST -a" command is goodness (to list *all* the files in a directory). It is a fairly dubious interpretation of the FTP spec. I can see why it was done this way however. There needs to be a way of turning this off (for those FTP servers that do not interpret "-a" in the assumed way NB: The FTP server is not Linux/Unix.). Does such a mechanism exist? Is there any other workaround?

---

### Post by Newbunto on 2012-06-17
Upgraded to Ubuntu 12.04 (for unrelated reasons). Confirming no change in behaviour i.e. still doesn't work.

---

