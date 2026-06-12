---
title: "/etc/sudoers"
date: 2005-01-12
forum: Desktop Environments
---

### Post by endtime on 2005-01-12
I screwed up my /etc/sudoers file by adding a bad line at the end (trying to give myself permission to run xmms as root without authentication so that it can read mp3s from my windows ntfs hdd), so now there's a syntax error in it and I can't sudo or use the root terminal or anything.  Is there a way to fix this?  Any guidance greatly appreciated.

---

### Post by mrosenlof on 2005-01-12
boot in single user mode

when grub says 'hit escape for the boot menu' or something like that, hit escape, follow the directions to add a '1' to the boot command line

you'll get a command line, and you'll be root.  you can edit the sudoers file with 'visudo' and fix it

---

### Post by endtime on 2005-01-13
Thanks dude...I know how to edit the boot command, but what exactly do I change?  I changed the last line from "boot" to "boot 1" and it just booted me back into Ubuntu normally...

---

### Post by Danilo on 2005-01-13
Append 1 to the "kernel" line instead.

---

### Post by wulf on 2005-01-13
Were you trying to edit the file using the visudo command or working on it directly? You should do the former - it checks the file is valid, which should avoid the problem you describe.

Also, when you get the issue sorted out, I wonder if a better approach to your problem might be to edit /etc/fstab so your user account has rights to mount and read the drive in question rather than trying to access it with root privileges.

Wulf

---

### Post by endtime on 2005-01-13
Thanks guys...I did try chmodding and chowning the drive but every file tells me it's read-only, I think it has something to do with it being NTFS but I'm not sure.  I know it's generally bad practice to run programs as root but I figured it would be okay just this once, since I can't find another solution.  I did add the drive to fstab, even with the "rw" variable I think, and still no luck.  Thanks again for the quick help guys.

Edit:  Oh and I edited it directly, didn't know about visudo, thanks for that tip.  If you can't tell, I'm pretty new to Linux.

---

### Post by endtime on 2005-01-13
Beautiful, that worked very nicely thank you.  Now I need to work out how to edit it properly...

---

