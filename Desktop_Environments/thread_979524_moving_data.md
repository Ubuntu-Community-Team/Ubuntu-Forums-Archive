---
title: "moving data"
date: 2008-11-12
forum: Desktop Environments
---

### Post by JoelClement on 2008-11-12
I have to move data from a clients hard drive from their RedHat server onto another drive because the server died. I can see the folders, but when I try to copy some of the files, I get a message that says in effect that I don't have permission to read the files. When I try to share the folder, I get a message that says I can't share folders I don't own. when I try to edit the smb.conf to allow the sharing, I am told I don't hame permission for that either. I tried a command like chown but I get an error about resolving the computer name.

---

### Post by taurus on 2008-11-12
Try putting _sudo_ in front of the command when you move files/directories from one drive to another drive.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by JoelClement on 2008-11-12
I was using the gui because there are 60,000 + files in dozens of folders. How would I do a wholesale move with the command line?

---

### Post by taurus on 2008-11-12
If you prefer GUI, nautilus, then run it from a terminal as

```
gksudo nautilus
```

---

### Post by psusi on 2008-11-12
cp -a src dest will recursively copy all files while preserving their permissions and ownership ( if run as root, use sudo ).

---

