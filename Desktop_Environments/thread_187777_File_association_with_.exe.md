---
title: "File association with .exe"
date: 2006-06-03
forum: Desktop Environments
---

### Post by meng on 2006-06-03
Strange problem I came across shortly after the Dapper upgrade:

My .exe (lower case) files would not open with wine on double-click, neither would wine appear on the menu if I right-clicked, instead the options would be cedega and text editor. But when I went to properties > open with, wine would be selected as the default.

Conversely, if I chose cedega as the default app, then cedega would no longer appear on the right-click menu, but wine would!!

Uninstalling and reinstalling wine did not help.

However, the problem was solved by renaming the extension to .EXE and then back to .exe, now the associations are recognized correctly, and I can open with wine by double-clicking.

Weird, huh? Anyone else had this problem and come up with the same or different solution?

---

### Post by slaging on 2006-06-07
I've been having the same problem with .exe files, and with any text document. It seems that nautilus want to open/run everything in gnome terminal as default. If you have any luck, please post.

---

### Post by meng on 2006-06-08
I had exactly the same problem. It was solved after deleting ~/.local directory (some menu information and application/mime associations are kept in there, so afterwards I had to reconfigure my menus and preferred apps all over again). It seems to have solved the wine/.exe problem, but since then I've noticed that certain (not all) .htm files will not automatically open with my browser.

May I ask, did both of you upgrade rather than clean install? I was wondering if this was responsible.

---

### Post by jobezone on 2006-06-08
There's was a bug reported in launchpad (EDIT: against wine) in that firefox allowed you to open .EXE files with wine from a link (in windows it doesn't allow you to do that, for security sake). I think the fix they made was a change in the mimetypes, so it could be related to this problem.

EDIT:[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/24829](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/24829)
But I'm not sure if the fix prevents or not from opening .EXE files in Nautilus with wine:
> wine (0.9.9-0ubuntu2) dapper; urgency=low
 .
   * Remove insecure mailcap entries; MS Windows '.exe' files should be run
     using 'binfmt-misc' support instead. (Closes: Ubuntu #24829)
[This]("http://en.wikipedia.org/wiki/Binfmt_misc") explains what binfmt-misc is, and how it works.

---

