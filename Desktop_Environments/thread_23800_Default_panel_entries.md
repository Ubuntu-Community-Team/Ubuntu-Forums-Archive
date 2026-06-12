---
title: "Default panel entries"
date: 2005-04-04
forum: Desktop Environments
---

### Post by Gavrila on 2005-04-04
Greetings,
I've just installed this wonderful distro, which is kbuntu. However defaullt installation kde panel is wrong IMHO.

It provides as default, the system view submenu to access the "file management" functions in kde.

Looking deeper in system view .desktop files, we can see that they are treated as URL passed to kde (e.g. URL=$HOME in home.desktop).

This behavior is, IMHO, plain wrong: I've chosen to use tab browsing in _ Web browsing_ section in konqueror settings. This mean that when I'm _Browsing_ I want _web links_ to be opened in tabs. The way kubuntu deals with the  deault panel implies that, stated the facts I wrote above, if I'm currently surfing the web, clicking on home icon to browse my files, will result in a new tab opened in my we browser window,  while I'm expecting a new file manager browser window to open.

This behavior is also wrong because it doesn't keep track of the differences the user sets between the web profile and file mangaer profile in konqueror. In fact, I won't be able to have my sidebar opened as well, if the file manager window pops int the the browser's one as a tab, while, as default, file management profile wants the sidebar.

Bottom line I'm asking to change the way kubuntu shows the default panel, adding some new .desktop files which execute commands to open system view things, rather than passing the URL. That would be more intuitive and handly for everyone, expecially for new linux users, who won't be able to figure it out by theirselves.

Best regards

---

### Post by aramazan on 2005-04-04
[QUOTE=Gavrila]The way kubuntu deals with the  deault panel implies that, stated the facts I wrote above, if I'm currently surfing the web, clicking on home icon to browse my files, will result in a new tab opened in my we browser window,  while I'm expecting a new file manager browser window to open.
[/QUOTE]I agree and I've also reported this in [http://lists.ubuntu.com/archives/kubuntu-users/2005-April/000188.html](http://lists.ubuntu.com/archives/kubuntu-users/2005-April/000188.html) (at the bottom of the page), though not as detailed and complete as your post.

Best regards

---

### Post by Gavrila on 2005-04-04
I've submittedi it to bugzilla, [https://bugzilla.ubuntu.com/show_bug.cgi?id=8640](https://bugzilla.ubuntu.com/show_bug.cgi?id=8640)


Regards


Stefano

---

