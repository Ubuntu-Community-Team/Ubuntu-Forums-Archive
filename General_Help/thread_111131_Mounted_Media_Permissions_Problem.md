---
title: "Mounted Media Permissions Problem"
date: 2006-01-01
forum: General Help
---

### Post by RoninGurl on 2006-01-01
I am having trouble opening the auto-detected drives on the Gnome desktop. But when I go to "System --> Administration --> Disks --> <any_drive_here> --> Browse" it works. Why the difference in working and not working? I just get the error "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of hda1." Same with hdc1 and hdd1. Can anyone help me so I can open these drives from the icons placed on my Gnome Desktop? I'm using Ubuntu 5.10. 

I assume this is because I am not root, and Ubuntu doesn't have a root account from what I understand, but then how am I supposed to open these drives? I dont see an "open as user" option. Any help?

---

### Post by yekibud on 2006-01-01
I'm having the same problem.  I'll let you know when I find a solution...  Did you try chown-ing the disk?  I tried that without success, but thab may be because it's read-only NTFS, I don't know...

---

### Post by RoninGurl on 2006-01-01
CHOWN won't work. It just says "read-only file system." Hmm. Well, any other ideas here? All I can think of is maybe adding myself to the root user group, and Im not sure how Ubuntu handles that because everything runs through "sudo" instead of an actual root user, I thought. If I'm wrong tell me. I'm new to Ubuntu.

---

### Post by yekibud on 2006-01-01
Solved...

Got this from another thread, works for me...

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by RoninGurl on 2006-01-01
[QUOTE=yekibud]Solved...

Got this from another thread, works for me...

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)[/QUOTE]
Oh my gosh. Thank you. That worked.
I just hope the folks at Ubuntu fix that little bug so it works by default.

---

