---
title: "Files or Folders copied to the hard disk from an CD DVD sets as read only"
date: 2014-09-18
forum: Desktop Environments
---

### Post by ivantutavac on 2014-09-18
That, this problem only happens under xubuntu, in a fresh 14.04 install. (Didn't tested in earlier versions). No problem at all with any ubuntu version or fedora xfce spin. When I set manually the permision in the propierties panel in Thunar I can make it readable. But its weird to make it with ALL my CD or DVD backups, and ALL subfolders. Any idea?

Cheers

---

### Post by TheFu on 2014-09-18
Welcome to the forums.
[B]
chmod -R u+w[/B]  Please do not run this command without understanding what it does AND do not do it anywhere that isn't owned by your userid.  It can break a system if run on the wrong files. **You've been warned.**

**man chmod** to learn more.

When running a multi-user OS, it is important to understand some of the basics of users, groups and permissions.
There is a free PDF book (or you can purchase the book at a bookseller, if you like) that will explain the why and how ... [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - get the PDF file and skim the first 100 pgs.  This will save you hundreds of hours wasted wondering why userid X can't do Y with a file/directory.

As long as I can recall, copying read-only files results in new files with read-only permissions.** Any other behavior would be a massive, huge, unacceptable, bug!**

---

### Post by ivantutavac on 2014-09-18
> **TheFu said:**
> Welcome to the forums.
As long as I can recall, copying read-only files results in new files with read-only permissions.** Any other behavior would be a massive, huge, unacceptable, bug!**

Thanks for your reply. There is no doubt about in a CD the files and or folder are read-only, but when I copy to for example the Desktop, it must become read-write, always happen this as far as I know. This "logic" is in ubuntu, or fedora-xfce, to mention a few. And in Windows too. That's why I want to find out why it happens in my Xubuntu.

---

### Post by TheFu on 2014-09-18
I'm absolutely positive that the **cp** command has this behavior and has since UNIX was created.  So ... regardless of how it SHOULD work, that isn't what you want, which is fine. How do we get something working the way you prefer?

Exactly what command are you using to copy the files over?  Is it **cp**?  Or something else? Is there a settings file for it?

To change the permissions on any files - use the **chmod** command, as mentioned above. I suspect that isn't what you want - probably using some GUI-thingy.

---

### Post by ivantutavac on 2014-09-18
I copy through drag and drop. Tried from Thunar that comes by default in Xubuntu and trough Nautilus and have the same problem.

---

### Post by TheFu on 2014-09-18
Looks like a bug in Thunar: [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/242842](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/242842)
and for Nautilus: [http://ubuntuforums.org/showthread.php?t=895403](http://ubuntuforums.org/showthread.php?t=895403)

There was a bug of this in 10.04 that was listed as fixed.

Where are the files being copied to?  NTFS or Linux file system? NTFS seems to be important in some of the bug reports I've seen.

---

### Post by ivantutavac on 2014-09-19
> **TheFu said:**
> Where are the files being copied to?  NTFS or Linux file system? NTFS seems to be important in some of the bug reports I've seen.

To linux file system

---

### Post by TheFu on 2014-09-19
So - from the reading I've done on this, seems you are hitting a bug in the file managers that was previously fixed, multiple times.

I know this doesn't help, but I use a script to pull files form optical media. You'll need to modify it for your system (the /raid/media/tmp part), but here it is:
```
#!/bin/bash
sudo mount /cdrom
cd /raid/media/tmp
nice cp -r /cdrom/* . 
chmod -R u+w *

```
Hope you find it useful.  Do not run it without making certain the TMP directory exists and you can create files there. Otherwise, it will be bad.

---

### Post by ivantutavac on 2014-09-19
> **TheFu said:**
> So - from the reading I've done on this, seems you are hitting a bug in the file managers that was previously fixed, multiple times..

Hi, thanks for the reply. I'll try it and will let you know. If it was fixed several times, why I'm getting that bug in a fresh and up to date installation?

---

### Post by TheFu on 2014-09-19
It must be easy to cause by mistake - especially since the program is overriding the default behavior of the cp command which honors the umask.

The storage location was changed in 14.04 for autoconnected paths by gvfs - security reasons.  I don't know for sure, but that could be part of it. It is really impossible without looking at the code changes over time.  If you really want to know, grab the source code and find the bug. Looking through the check-in log messages should help to locate the specific changes.  I haven't done that in years, but it can be very enlightening. I don't know where the developers keep the version control for these tools - github? Google found it here: [https://github.com/GNOME/nautilus](https://github.com/GNOME/nautilus) - be certain to clone the correct branch for your version of nautilus - so you get the entire change history.

---

### Post by ivantutavac on 2014-09-19
I'm noob, don't know the procedure for doing this, reporting bugs, find them, etc. Can you please tell me how can I help with this "bug", where can I report or post. Cheers.

---

### Post by TheFu on 2014-09-19
Google found this: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) - the ubuntu bug reporting doc.
There is a nice "Getting Advice" section near the bottom for more help.

---

