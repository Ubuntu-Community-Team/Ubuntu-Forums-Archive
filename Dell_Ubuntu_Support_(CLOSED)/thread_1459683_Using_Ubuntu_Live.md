---
title: "Using Ubuntu Live"
date: 2010-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kid Charlemagne on 2010-04-21
I'm trying to access my installed version of Ubuntu 8.04 with a Ubuntu 9.1 live CD. I booted up from the live CD without installing, but I can't seem to access any files from the installed version.

I am being denied permission. I can access files on the live CD, but not the installed operating system. I used the command code sudo nautilus and the root file browser window opened, but when I try to save the file I want to change on the installed operating system; it denies permission because I don't have administrative privileges. Is there a way I can enter my password at some point to get access to my files? Without the live CD I can't boot up at all. Any help you could offer would be greatly appreciated.

---

### Post by Kai Summers on 2010-04-23
try gksudo gedit /the/file/you/want/to/edit

---

### Post by ugm6hr on 2010-04-24
Maybe tell us exactly what the problem is, so we can get a flavour of what you are trying to achieve.

And what file are you trying to edit?  If a text file then the suggestion above should work.  From memory, there is no password for sudo on the LiveCD.

---

### Post by Kid Charlemagne on 2010-04-24
Thanks for the reply. I had to open the filesystem for the installed operating system. It was under places on the Live CD desktop. This was after the nautilus command opened the root file browser. Problem solved. I can get any file I want to now on the installed operating system. Thanks again.

---

