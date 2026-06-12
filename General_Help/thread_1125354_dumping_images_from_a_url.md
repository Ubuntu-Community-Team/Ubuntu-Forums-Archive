---
title: "dumping images from a url"
date: 2009-04-14
forum: General Help
---

### Post by sume on 2009-04-14
I am using lynx and sed. to get a list of image files from a url and download them, the problem is I can't get the regular expression right. Basically I'm dumping the output from lynx into sed and filtering the paths for the image files (jpg, gif etc...)

I'd appreciate any help
Thanks

---

### Post by babounours on 2009-04-14
what do you get from lynx ?

---

### Post by sume on 2009-04-14
> **babounours said:**
> what do you get from lynx ?

lynx -source -image_links [http://www.youtube.com](http://www.youtube.com)

---

