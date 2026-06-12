---
title: "Issues when creating a DEB package the easy way"
date: 2009-04-25
forum: General Help
---

### Post by abelthorne on 2009-04-25
Hello,
I want to package a personal icon theme for easy distribution. As it is only a bunch of files/directories to install to /usr/share/icons, I found a method for simple DEB packages creation :
- I create a directory (let's call it "mytheme") with a "DEBIAN" subdir and the hierarchy of directories that match the installation (i.e. usr/share/icons/myicontheme/scalable etc.)
- in the DEBIAN dir, I create a "control" file that describes the package (maintainer, category, version...)
- I use **dpkg-deb -b mytheme** to get mytheme.deb

It works fine except for a specific and problematic point : when working on the files I want to package, they are of course somewhere in my home dir, with me as an owner. The problem is that after packaging and installation, the installed files keep myself as an owner and I end up with a directory owned by me rather than root in /usr/share/icons. Even if using **sudo dpkg-deb...**, the installed files keep the original owner.

I find it odd that the packaging process doesn't "convert" the files owner and allow to end up with a standard user owning files in the system dirs. Is it a normal behaviour or a bug in dpkg-deb ?

If it is normal, how am I supposed to handle my work : do I have to set root owner on the files I work on prior to packaging and set them back to myself after it so that I can continue to work on them ?
How do you developers work or organize your files when you have to package them ?

---

