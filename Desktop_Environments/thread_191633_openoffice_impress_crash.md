---
title: "openoffice impress crash"
date: 2006-06-07
forum: Desktop Environments
---

### Post by NiN on 2006-06-07
Hi!

Tried to build a little presentation in impress with some high resolution pictures, but it looks like the version supplied with dapper is quite buggy.

I got more than one crash and it is awfully slow...

Someone with some tips on how to change this?

[edit]
submitted a bug report:
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/49432](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/49432)
[\edit]

---

### Post by gesus on 2006-06-10
I've got exactly the same problem. 

Impress crashes. When you restart the program it tries to recover the document. You can see that the program is building the thumbnails of the slides on the left hand side. The slide with the pictures seems to cause the crash. :-k

---

### Post by gesus on 2006-06-10
Hower, I removed the packages openoffice.org2-gnome and openoffice.org-gtk and it did work. The application now looks a bit strange but doesn't crash any more :-)

Seems to be a bug in one of those packages....

---

### Post by Barney on 2006-11-29
I experienced the same crashes when attempting to insert a picture into a slide in impress.

After several crashes and failures to recover as described above, I found that by unchecking the box next to "Link" in the lower left corner of the "Insert picture" window that the crashes no longer occurred, and that I was able to create a presentation of pictures selected from files and save the presentation as a .ppt.

I emailed the .ppt, and it worked fine for the recipient, so the "Link" box seemed to have no function for what I was trying to do.

---

