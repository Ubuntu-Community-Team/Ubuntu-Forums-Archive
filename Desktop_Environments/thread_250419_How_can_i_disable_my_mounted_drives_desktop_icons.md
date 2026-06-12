---
title: "How can i disable my mounted drives desktop icons?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Benllie on 2006-09-04
i have 3 mounted drives and its not good looking to have them all the time in my desktop :cool: tnx

---

### Post by ciscosurfer on 2006-09-04
Issue the following in a terminal to 'remove' them```
gconftool -t bool -s /apps/nautilus/desktop/volumes_visible false
```To bring them back, use this```
gconftool -t bool -s /apps/nautilus/desktop/volumes_visible true
```I'm using the gconftool which is basically a command-line scripting tool that interfaces with your Configuration Editor.  You can enable your Configuration Editor by going to Applications > Accessories > Alacarte Menu Editor, clicking on System Tools, then placing a checkbox next to Configuration Editor.  To use it, go to Applications > System Tools > Configuration Editor.

---

### Post by Benllie on 2006-09-04
ty so much im really liking this linux/ubuntu OS thanks for your time

---

### Post by ciscosurfer on 2006-09-04
I'm glad that took care of your issue.  The UbuntuForums are "chock-full" of useful information and users who care about helping others out.  If you ever have any questions or concerns (or complaints), the Forums are a great place to vent.  Have fun with your Ubuntu system! :D

---

