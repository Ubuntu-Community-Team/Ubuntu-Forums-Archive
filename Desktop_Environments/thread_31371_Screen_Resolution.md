---
title: "Screen Resolution"
date: 2005-05-02
forum: Desktop Environments
---

### Post by Fenix on 2005-05-02
Yesterday, I had my computer on its usual setting of 1024 X 768 and turned it off before I went to bed last night. Now it’s stuck at 640 X 480 and will not let me change it. Any and all help would be appreciated.

---

### Post by heimo on 2005-05-02
Almost everything that I know about these problems:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

However, it's odd that it was working and is no longer. Did something change? Major updates? Logfile mentioned in post abowe is useful source of debugging information for these kind of problems. Check that.

Also run:
ls -al /etc/X11/xorg.conf*
and see if there are other versions of Xorg configuration file. If update changed the configuration, there may be backup file with date  in its name. See if it's a recent file and check what the differences are.

---

### Post by timbtwisted on 2005-05-03
I actually just encountered the exact same problem.  If anyone knows of any recent issues the information would be great thanks.

---

