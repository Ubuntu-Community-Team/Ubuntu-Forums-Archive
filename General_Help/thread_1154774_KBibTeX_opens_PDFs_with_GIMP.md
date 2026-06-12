---
title: "KBibTeX opens PDFs with GIMP"
date: 2009-05-10
forum: General Help
---

### Post by ad_267 on 2009-05-10
Any idea how to get KBibTeX to open PDFs with Evince?

---

### Post by ad_267 on 2009-05-10
Never mind, I figured it out.

I had to create a ~/.kde/share/config/profilerc file and put this in it:
```
[application/pdf - 1]
AllowAsDefault=true
Application=evince.desktop
GenericServiceType=Application
Preference=1
ServiceType=application/pdf
```

---

### Post by serexia on 2009-11-03
Hi, I am having the same problem since I upgraded to 9.10. I am trying to use acroread instead, but the default:

[application/pdf - 1]
AllowAsDefault=true
Application=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
GenericServiceType=Application
Preference=1
ServiceType=application/pdf

in the ~/.kde/share/config/profilerc file results in opening the file with gimp. any alternative idea?

thanks
s

---

### Post by ad_267 on 2009-11-03
Have a look here: [http://forum.kde.org/viewtopic.php?f=17&t=39841](http://forum.kde.org/viewtopic.php?f=17&t=39841)

The last post of that thread might also help.

---

