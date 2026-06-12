---
title: "Ubuntu 7.10 - GB18030 locale"
date: 2008-04-10
forum: Desktop Environments
---

### Post by boson84 on 2008-04-10
I have an application that needs to support GB18030 locale on Ubuntu.  I'm currently using 7.10 Gutsy.  As is, Ubuntu does not come with this locale, so I found some steps online on how to configure this locale.  I did following steps (I'm not sure if these steps are enough setup new locale):
1. modified /var/lib/locales/supported.d/zh to include zh_CN.GB18030
2. ran ' Sudo dpkg-reconfigure locales' to configure new locale.

After performing above steps, I can now get the zh_CN.GB18030 locale to show up when I run 'locale -a' command.  I can also change to this locale during log-in process, but Chinese input does not seem to work.  Whenever I try to enter a Chinese text using SCIM, it shows number and English character.  After investigation this issue, I suspect that this problem is occurring because the locale is not setup properly.  More specifically, I noticed that the file /usr/share/X11/locale/zh_CN.gb18030/XI18N_OBJS expects certain shared library files to be on the system at /usr/X11R6/lib/X11/common folder.  However, this folder does not exist in 7.10 or in 8.04.  In fact, since the Ubuntu edgy release, these files have been removed from the distribution.  Does anyone know why these files were removed?  Is this the reason why the Chinese input is not working correctly?  Does anyone have Ubuntu working in GB18030 locale?  I would really appreciate answer to these questions from anyone who is knowledgeable with this area.

---

### Post by boson84 on 2008-04-11
bump.  

Does anyone know anything about this issue? or Does anyone know any other place that would be better suited for asking this question?

---

### Post by boson84 on 2008-04-17
I just wanted give an update on this problem to anyone who runs into this.  After contacting several people, I found out that this problem exists because the patch for the problem has not been checked-in to the Xorg code base ([https://bugs.freedesktop.org/show_bug.cgi?id=1573](https://bugs.freedesktop.org/show_bug.cgi?id=1573)).  Some versions of Linux such as Suse and Redhat have already included in the patch in their distribution, but Ubuntu, Fedora and may be others do not have this patch included as of now.

---

