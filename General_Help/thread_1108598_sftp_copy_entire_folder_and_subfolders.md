---
title: "sftp copy entire folder and subfolders"
date: 2009-03-27
forum: General Help
---

### Post by swraman on 2009-03-27
Hi,

Im trying to copy an entire folder along with its subfolders through sftp from a server to my pc.

I tried:

get /path/folder_to_copy/* /path_on_computer/

it coppies all the files in folder_to_copy to path_on_computer, but it gives an error for all of the subfolders in folder_to_copy.

Thanks,

Raman

---

### Post by doas777 on 2009-03-27
usually to get recursion on any app, you add -R (or -r).

I just learned that if you have ssh installed on the server,
you can just paste an ssh command into nautilus```
ssh://user@server
```
to get a gui for sftp, if that is acceptable.

---

### Post by swraman on 2009-03-27
THanks, the -r worked.

For anyone else reading, I used:

scp -r user@host:path_on_server path_to_copy_to

Thanks again

---

