---
title: "nautilus isn't happy with smbmount-ed shares"
date: 2006-06-02
forum: Desktop Environments
---

### Post by lapsey on 2006-06-02
I rely upon local samba shares quite heavily and nautilus isn't very happy when reading them, and often crashes. This includes the gThumb image viewer.

I am sure there is some problem with synchronisation between smbfs and nautilus.

I tried turning off the preview but this this did not solve the problem, as nautilus likes to check out the actual filetypes of, and number of, files in a directory. My home network is fairly fast for that matter

I had hoped it would have been fixed with dapper, but maybe this is a rare behaviour.. either way, I hope someone has some idea!

---

### Post by smack on 2006-06-02
[http://bugzilla.gnome.org/show_bug.cgi?id=335114](http://bugzilla.gnome.org/show_bug.cgi?id=335114)

I went to submit a bug report for the same thing and found that it had already been reported. I'm hoping a fix is made for this because it's very very annoying.

---

