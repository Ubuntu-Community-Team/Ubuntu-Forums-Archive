---
title: "How to uninstall gtkwifi"
date: 2009-03-04
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-03-04
I have download and install this deb of gtkwifi from this page [http://sourceforge.net/project/showfiles.php?group_id=132677&package_id=145736&release_id=477242](http://sourceforge.net/project/showfiles.php?group_id=132677&package_id=145736&release_id=477242)
How can I uninstall it?
Sorry for noobish question.

---

### Post by chriskin on 2009-03-04
you will have to search for gtkwifi at the synaptic package manager  (system - administration) and remove it (right click, you will see the option)

---

### Post by afeasfaerw23231233 on 2009-03-04
I typed gtkwifi in synaptic and it didn't find anything.

---

### Post by afeasfaerw23231233 on 2009-03-04
Now I can't install Wicd because of the present of gtkwifi. I downloaded a Wicd deb package and double clicked on it. It said 
```

**Error: Conflicts with the installed package "gtkwifi"**

```

---

### Post by afeasfaerw23231233 on 2009-03-04
Sorry for my n00bish question. I found out the command apt-get remove is for removing package. [solved]

---

### Post by chriskin on 2009-03-05
anything that is removed with apt-get remove is usually removed through synaptic as well

guess i was wrong
glad you found the command-line way , sorry

---

