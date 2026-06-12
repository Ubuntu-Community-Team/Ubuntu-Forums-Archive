---
title: "Can't install Adobe Reader"
date: 2008-12-11
forum: General Help
---

### Post by adamthompson on 2008-12-11
When I try to install Adobe Reader using apt, I get the error message, "The following packages have unmet dependencies: acroread: Depends: libcups2 but it is not installable". How can I install libcups2? I'm using 64-bit Ubuntu, by the way. Thanks.

---

### Post by zvacet on 2008-12-11
I looked [here]("http://packages.ubuntu.com/") and that package is available in Intrepid but not for Hardy.

---

### Post by oldos2er on 2008-12-11
Check your Software Sources to be sure they're all enabled.

---

### Post by scouser73 on 2008-12-13
Go to: [http://get.adobe.com/uk/reader/otherversions/]("http://get.adobe.com/uk/reader/otherversions/") Click the drop-down menu **Select an operating system** and choose **Linux - x86 (.deb)**

Then use the **Select a language** drop-down menu for your region.

---

### Post by Arup on 2008-12-13
Enable medibuntu repos in your sources and you will then be able to install Acroread.

---

