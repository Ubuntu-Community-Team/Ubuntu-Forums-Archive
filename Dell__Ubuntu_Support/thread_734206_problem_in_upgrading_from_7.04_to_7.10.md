---
title: "problem in upgrading from 7.04 to 7.10"
date: 2008-03-24
forum: Dell  Ubuntu Support
---

### Post by dhap on 2008-03-24
The system stops with this comment:

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release) Unable to find expected entry  screenlets/binary-i386/Packages in Meta-index file (malformed Release file?)

I usually do not have any problems while updating packages.

---

### Post by Sam Lars on 2008-03-24
Sound's like an issue with that repository...

---

### Post by dhap on 2008-03-24
Thanks for replying Sam, what should I do now?

---

### Post by aaaantoine on 2008-03-24
Try removing any repositories you've added since installing 7.04, and then try again.

---

### Post by Sam Lars on 2008-03-24
Yes, namely the one mentioned in the error.

---

### Post by dhap on 2008-03-24
I did install screenlets sometime back and the repository related to that seem to be creating the problem. But, how do I remove the particular repository?

---

### Post by Sam Lars on 2008-03-24
Go to System > Administration > Software Sources, and you can un-check it in the Third Party tab.

---

### Post by dhap on 2008-03-26
Thanks a lot. It worked perfectly.

---

