---
title: "KDesktop Lost Type"
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by jlr4u on 2008-02-12
I had a link on my desktop that opened an odt Open Office Document. I opened the properties of this link did  a right clicked on edit file type. This corrupted all open office documents in that I can no longer left click to open any of them.   I must right click and select "Open With"  I can't seem to figure out how to restore the file type.

I'm running Ubuntu 7.10 gusty on Kubuntu 2.6.22-14-generic #1

---

### Post by jlr4u on 2008-02-16
Problem fixed.

After doing a lot of researching,  I found the problem with the file association in a file called 
x-desktop.desktop

I just renamed the file and all of the associations to Open Office Document worked again.
Commands were:
```
cd ~/.kde/share/mimelnk/application
mv x-desktop.desktop x-desktopbkup.desktop 
```

---

