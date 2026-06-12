---
title: "How to save a browsable/static copy of a dynamic website"
date: 2009-03-24
forum: General Help
---

### Post by sefs on 2009-03-24
Hi all, i have a couple of dynamic websites in asp, aspx and joomla that I would like to save in static, browsable format so I can burn to cd or usb key and have them be browsable.  

Are there any tools in ubuntu that can do this easily?

Thanks.

---

### Post by cherva on 2009-03-24
wget has a nice "-m" option  [http://www.boutell.com/newfaq/creating/mirroring.html]("http://www.boutell.com/newfaq/creating/mirroring.html") Look here, or google ```
web site mirroring wget
``` yourself. :)

---

### Post by sefs on 2009-03-24
I tried that and it downloaded perfectly but it is not browsable.  

If i click on each individual file it opens, but i can't click on a link in a page and go to a connecting page, it gives me a page not found error in firefox, although the page is right there in the same directory.

I used wget -mk [http://mysite.com/default.asp?siteid=1](http://mysite.com/default.asp?siteid=1) for instance.

All pages downloaded retain there dynaicmic urls such as...
default.asp?siteid=1&pageid=2 etc.  Dont know if thats what causing the local browsing problem.

Any more suggestions?

---

### Post by sefs on 2009-03-24
Pardon me....the extra options at the page you provide hit the spot!  Thanks a mil.

---

### Post by cherva on 2009-03-24
You are welcome.

---

