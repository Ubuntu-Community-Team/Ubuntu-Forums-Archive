---
title: "fspot export to folder problem - thumbnails missing"
date: 2006-06-26
forum: Desktop Environments
---

### Post by jaypeasy on 2006-06-26
Hi,

Whenever I try to export a photo gallery to a folder using fspot, everything proceeds correctly except that the thumbnails created are all empty files. The gallery therefore does not display anything except empty blocks in my web browser. Clicking on one of these blocks of course takes me to the original image. Any idea why the thumbnail generation fails?

---

### Post by Ribs on 2006-09-01
I have the exact same problem. I fear the problem may be due to f-spot's coding more than anything else. On the terminal I see the following when trying to export:

(f-spot:11323): GdkPixbuf-WARNING **: Bad option name '' passed to JPEG saver

(f-spot:11323): GdkPixbuf-CRITICAL **: gdk_pixbuf_savev: assertion `error == NUL L || *error != NULL' failed

for each picture. Not too sure how to fix.

---

### Post by gerbman on 2008-06-02
Did either of you find a solution to your problems? I seem to be having the same issue in the current version of F-Spot.

---

### Post by orsonj on 2008-06-02
I posted a workaround at the [bug report]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/235071/comments/4")

---

### Post by gerbman on 2008-06-02
> **orsonj said:**
> I posted a workaround at the [bug report]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/235071/comments/4")

Thanks for the reply, Orson; however, the error mentioned by tiefflieger (at the bug report) comes up for every picture being exported. I am trying to export around 800 pictures, and clicking the "Skip" button for each one is not very doable. How do we get this bug confirmed and assigned to someone?

---

### Post by orsonj on 2008-06-03
> Thanks for the reply, Orson; however, the error mentioned by tiefflieger (at the bug report) comes up for every picture being exported. I am trying to export around 800 pictures, and clicking the "Skip" button for each one is not very doable.
Tell me about it. It is really annoying.
> How do we get this bug confirmed and assigned to someone?
I'm not sure. Sorry.

---

### Post by gerbman on 2008-06-05
They have fixed the problem and backported it to 4.3.1. To get the fix, go to Edit->Manage Extensions. Disable the current Folder Export extension and go to Install Add-ins. Refresh the list and install the new Folder Export extension. Should do the trick.

---

### Post by SlaughterDog on 2008-07-21
> **gerbman said:**
> They have fixed the problem and backported it to 4.3.1. To get the fix, go to Edit->Manage Extensions. Disable the current Folder Export extension and go to Install Add-ins. Refresh the list and install the new Folder Export extension. Should do the trick.

Doesn't work for me, but I am having a slightly different problem too. I try to export and get an error "Object reference not set to any instance object". It exports only one HQ pic, along with the web pages.

---

