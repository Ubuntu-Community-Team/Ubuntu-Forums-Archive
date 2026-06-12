---
title: "Question about File Permissions"
date: 2009-06-08
forum: General Help
---

### Post by lachild on 2009-06-08
Hey guys,

Quick question about file permissions.

If I have folder owned by a user that has been set to permissions 755 and a file located inside this folder owned by root and the file permissions set to 600, is it normal to allow the folder owner the ability to remove this file even though the file itself is owned by root and the file permissions are set to only allow root access to this file?

Before the flames, I understand that this situation should never come up.  I was testing a script to make sure the correct error message was thrown when it couldn't write to the file not knowing the folder owner could remove said file.  In reality I would put this protected in it's own protected folder outside any user owned folders.  It just struck me as odd and I wanted to see if this was expected behavior for curiosities sake.

Thanks in advance,
LaChild

---

### Post by upbeat.linux on 2009-06-09
Yes. If you give the directory owner write access they will be able to delete files owned by other users including root.  That being said, how are you doing remove.  Forcing a recursive remove would not throw an error message:

```
rm -rf myfile.txt
```

However, a simple remove:

```
rm myfile.txt
```

would prompt:

```
rm: remove write-protected regular file `myfile.txt'?
```

For questions on file permissions see:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

