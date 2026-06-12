---
title: "Do you know about this problem?"
date: 2008-06-01
forum: Desktop Environments
---

### Post by aurora_consurgens on 2008-06-01
My menu bar doesn't show normal. It separate from window so I want to give normally. How can I solve this problem.
Thank you... 

This is picture:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72409&stc=1&d=1212295785[/IMG]

---

### Post by prshah on 2008-06-01
> **aurora_consurgens said:**
> My menu bar doesn't show normal. It separate from window so I want to give normally. How can I solve this problem.


You have installed the "mac pack" and hence the Mac Menu Bar (The folder shows on your desktop!) To disable this behaviour:

Press Alt+F2, then give the command ```
gedit ~/.gnomerc
``` A (blank) gedit window will open up. Add the below line```
export GTK_MENUBAR_NO_MAC=1
```

Save, and close. Now logout and login. Your menus should be back to normal.

---

