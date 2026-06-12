---
title: "Clear multiple OOo?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dgermann on 2005-10-17
HI--

After installing Breezy, I see that I have two sets of Open Office.org: 2.0 and 1.1.

Is there any reason to have both? If not, how do I clear the older one out?

Thanks!

---

### Post by DJ_Max on 2005-10-17
I don't see a reason to have both. To remove 1.1

```
sudo apt-get remove openoffice.org
```

---

### Post by dgermann on 2005-10-18
DJ_Max--

Thanks for your quick help!

So how from that command does it know which installation to remove?

---

### Post by DJ_Max on 2005-10-18
There are two meta-packages. *openoffice.org* which is 1.1. As well as *openoffice.org2* for OO 2.

---

### Post by dgermann on 2005-10-18
DJ_Max--

OK, thanks! Will give it a go!

Yup--seems to have worked. Thanks much!

---

