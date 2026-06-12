---
title: "Konqueror and External Links"
date: 2006-04-14
forum: Desktop Environments
---

### Post by Mau on 2006-04-14
Whenever I click on a link from KMail or KNode, for example, Konqueror opens as it should, but it doesn't load the requested page.  Instead, it downloads it and views it from the cache (so the address ends up being something like /var/kde3cache/blah.html).  This messes up style sheets, images, and hyperlinks.  Any way just to make it load the requested page, as if I typed it in myself?

Thanks,

---

### Post by Mau on 2006-04-19
Any ideas?  Does anyone else experience this?

---

### Post by GoldBuggie on 2006-04-20
i use firefox but i don'thave this problem. maybe it is a redirect to konqueror only problem.

Since I run firefox I have redirected my clicks via Control Center->KDE Components->Component Chooser->Web Browser->in the following browser:

I have typed firefox there but you can always try and type konqueror there and see if this solves your problem

---

### Post by Mau on 2006-04-20
Aha, that did it.  I had "in the following browser" checked with "konqueror" written in it.  I changed it to "an application based..." which solved it.

Thanks.

---

