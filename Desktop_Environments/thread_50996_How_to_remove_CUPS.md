---
title: "How to remove CUPS?"
date: 2005-07-22
forum: Desktop Environments
---

### Post by tom-ubuntu on 2005-07-22
Hi guys

I am not having any printer at home. I always mail it to my office to print something. So I like to remove everything cups related. But if I like to uninstall it, apt will remove also packages "ubuntu-desktop" (or similar, can't remember). Is this safe to do? Or how can I remove cups?

There are also other packages I like to remove with the same dependency.

Thanks for any tips!
Joe

---

### Post by Xian on 2005-07-22
It's giving you the 'ubuntu-desktop' up for removal because cupsys is a package that was included in that meta-pkg format. It can be removed without any problems.

---

### Post by heimo on 2005-07-22
At least ubuntu-desktop is safe to remove. For other packages, if you're uncertain, copy list of packages  to text file and reinstall if neccessary.

---

### Post by tom-ubuntu on 2005-07-22
Ok, thanks for your replys.

btw. just recognized now that I posted in the wrong forum, I've got 5.04   ;-)

---

