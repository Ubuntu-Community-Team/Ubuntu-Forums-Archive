---
title: "Refreshing folder contents in Dolphin"
date: 2009-10-26
forum: Desktop Environments
---

### Post by ascent1729 on 2009-10-26
Something that has annoyed me about Dolphin and the folder dialogs used by KDE4 applications is that they don't seem to automatically refresh when new files have been placed in a directory. For example, if I download some new music and then extract it to my Downloads directory, then KDE4 applications keep on remembering the old contents of the folder until I manually refresh. I'm pretty sure other applications (GNOME applications, for example) show you what is in the folder at the time that it is accessed. Is there some setting that I can use to change this? I'm using Ubuntu 9.10 (Jaunty).

---

### Post by lovinglinux on 2009-10-26
+1

I'm loving KDE, but that behavior is really annoying. I don't know why, but sometimes it does refresh automatically.

---

### Post by GeneralZod on 2009-10-26
Weird - works perfectly, here, with Dolphin and the file dialogs.  I compile from source, though.

---

### Post by smsmith on 2010-01-19
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/479527](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/479527)
[https://bugs.kde.org/show_bug.cgi?id=207361](https://bugs.kde.org/show_bug.cgi?id=207361)

The KDE bug is marked resolved-fixed (for KDE 4.4).  There's also a SUSE bug marked resolved-fixed:
[https://bugzilla.novell.com/show_bug.cgi?id=546491](https://bugzilla.novell.com/show_bug.cgi?id=546491)

According to [comment 15 of the Ubuntu bug]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/479527/comments/15"), this should be fixed in the "next kernel update".  But I can't figure out which kernel is supposed to have the fix.  I've currently got 2.6.31-17 (recalling from memory).

---

### Post by freedomnotequality on 2011-09-18
This bug is NOT fixed.

I have the same issue.  It is not a mere annoyance: potentially one could make a system decision, perhaps to delete some files, based upon the erroneous folder contents display.

I am running Kubuntu Natty with Kernel 2.6.38-11.48.

---

