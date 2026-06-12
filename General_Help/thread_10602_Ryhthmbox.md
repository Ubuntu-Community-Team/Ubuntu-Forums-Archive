---
title: "Ryhthmbox"
date: 2005-01-09
forum: General Help
---

### Post by bjes on 2005-01-09
I was trying to install ryhthmbox 0.8.8 and I came across this error:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool


any thoughts?

---

### Post by nemin on 2005-01-09
[QUOTE=bjes]I was trying to install ryhthmbox 0.8.8 and I came across this error:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
[/QUOTE]
I think ```
sudo perl -MCPAN -e 'install XML::Parser'
```  will fix this...

---

