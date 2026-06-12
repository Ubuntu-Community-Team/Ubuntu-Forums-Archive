---
title: "Tagging filesystem support"
date: 2011-03-01
forum: Desktop Environments
---

### Post by _nikolaos on 2011-03-01
My question is about tagged filesystem support. 

That is, adding several tags into my folders and files, and browse rearranging them by the tag names.

The ideal would be that by right-click on a file explorer window, an option "Arrange by Tags" appears to select, and the window reappears with a list of the tagnames in a folder-like fashion.

As far as I know, there is no such support integrated in GNOME, nautilus or other.

Is there anything helpful towards tag support as I described?

---

### Post by lykeion on 2011-03-01
Maybe you can use extended attributes for this, see this: [http://en.wikipedia.org/wiki/Extended_file_attributes](http://en.wikipedia.org/wiki/Extended_file_attributes)
Install package *python-xattr* and use command *xattr* to set values. If you know a little python it's easy to write an app or script that reads extended attributes using the xattr module, see [http://pyxattr.sourceforge.net/html/](http://pyxattr.sourceforge.net/html/)

Supposedly the search utility Beagle (it's in the repos) also reads extended attributes. Might be easier if you've no programming skills.

---

