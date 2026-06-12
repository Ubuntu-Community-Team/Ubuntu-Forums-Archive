---
title: "choose default font for non-english character"
date: 2010-04-22
forum: Desktop Environments
---

### Post by elegant55 on 2010-04-22
Hi

I am using a English font family (Lucida) as my desktop font. When there are Chinese characters (such as in title bar and bookmarks toolbar of firefox) the system automatically choose a default chinese font family for them. 
I want to use a specific chinese font just for the chinese characters but not system-wide. Is it possible?

---

### Post by elegant55 on 2010-04-22
Ok, I solved it.

cd /etc/fonts/conf.d
sudo ln -s ../conf.avail/69-language-selector-zh-cn.conf .

---

