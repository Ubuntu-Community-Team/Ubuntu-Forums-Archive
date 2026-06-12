---
title: "Drag and Drop Problems"
date: 2013-09-06
forum: Desktop Environments
---

### Post by Gannin on 2013-09-06
I'm using Lubuntu 13.04, which uses PCManFM 1.1.0.  Dragging and dropping files into some programs isn't working for me.  I can move files around in PCManFM, drag and drop then into other folders etc., but dragging and dropping them into other programs doesn't always seem to be working.

If I try to drag and drop a file into Audacity, regardless of the file Audacity says it can't tell the file type of the file, even though importing files through the file > import dialog works.  If I try to drag an image file into EasyTAG, it gives me the error of "no such file or directory".  Dragging to both of these programs worked in 12.10.

However, strangely enough, dragging to Gimp works fine, and if I drag a file into Leafpad, it gives "file:///path/to/file" with the actual file path of course.

But it's still troubling that some programs no longer accept drag and drop from PCManFM, when they worked perfectly fine in 12.10.  Any ideas?

---

### Post by vasa1 on 2013-09-06
There are other reports relating to drag-n-drop: [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1179167](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1179167)

---

### Post by Gannin on 2013-09-06
Thank you for the information.  That's interesting, but it looks like the link is only about dragging files back and forth to and from the desktop, instead of dragging them to other applications.

---

### Post by garethfoxwilliams on 2013-09-09
I'm using Lubuntu 13.04 with PCManFM 1.1.0

I there a simple way of perhaps updating to the latest version, without compiling ?


(that's assuming the bug has been fixed...... )

---

### Post by vasa1 on 2013-09-09
@gareth, please don't ask the same question more than once.

---

### Post by Gannin on 2013-09-09
I can confirm that this bug is fixed in PCManFM 1.1.2.  However, there's no simple way of updating, especially considering Ubuntu uses multiple packages for libfm, instead of having just one libfm package.

---

### Post by garethfoxwilliams on 2013-09-10
Could anyone advise on the "complicated" way, then, as I'm willing to give it a go!!

Thanks in advance

---

### Post by kalehrl on 2013-09-10
Have you rad this post:
[http://ubuntuforums.org/showthread.php?t=2157490&p=12783915#post12783915](http://ubuntuforums.org/showthread.php?t=2157490&p=12783915#post12783915)

---

### Post by Gannin on 2013-09-10
> **kalehrl said:**
> Have you rad this post:
[http://ubuntuforums.org/showthread.php?t=2157490&p=12783915#post12783915](http://ubuntuforums.org/showthread.php?t=2157490&p=12783915#post12783915)

I would recommend against using the Lubuntu dev PPA.  It doesn't just upgrade PCManFM and libfm, it also upgrades the panel and a few other items and at least on my machine, causes the logout menu to no longer appear.

To upgrade PCManFM, here's what I did.  When I install from source, I like to use checkinstall to automatically create a .deb from the source so the package manager knows about the software I just installed.  I think there are other programs that will also automatically create .deb packages, so feel free to use whatever works for you.

First, it's good to understand that a bunch of system packages depend on PCManFM, which then depends on all the libfm packages.  So it's like this:

System > PCManFM > libfm

In Ubuntu, libfm is spread across multiple packages, for no real reason that I can discern.  However, the libfm source creates just one package, which then conflicts with all the other libfm packages.

So, download the latest stable PCManFM and libfm source packages [http://sourceforge.net/projects/pcmanfm/files/](http://sourceforge.net/projects/pcmanfm/files/).

Extract and compile PCManFM using the normal methods.  Create a .deb from the source, making sure to give it the appropriate version number of 1.1.2 or whatever the version is when you do this, and then install the .deb package.  This should upgrade and replace the existing PCManFM package.  To make things easy, make sure you don't set any dependencies on the package.

If you don't set any dependencies on the package, that means the system will no longer require the default libfm packages.  This is important for later.  Next, extract and compile libfm.  Now remove the existing libfm packages from the system.  Because the PCManFM package no longer depends on libfm, the system will let you do this.  After removing the default libfm packages, create a new package from your new libfm source and install it.  Finally restart your system and it should work.

Technically the new libfm package can coexist with the default libfm packages if you use force install it with dpkg, but then if there are any updates to the default libfm packages the updates will overwrite your new package and you'll have to go back and install it again.  If you remove the default libfm packages and then install the new one, you won't have to worry about this.  And if at some time you want to go back to using the default packages, you can just go into Synaptic and do a rollback of the PCManFM package, which will then install the default libfm packages too.

---

