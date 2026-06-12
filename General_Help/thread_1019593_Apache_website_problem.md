---
title: "Apache website problem"
date: 2008-12-23
forum: General Help
---

### Post by johnkvan on 2008-12-23
In my www folder, I have .css html and image folder but whenever i go to localhost in firefox, it doesn't show any images. However, when I open up the HTML file in the file viewer, it opens up in firefox fine with images. Is there a setting in apache2 that i need to conf?
Thanks

---

### Post by ju2wheels on 2008-12-23
Your HTML file shoud be directly in /var/www/ and not a sub folder in that one and it should be named index.html if you want it to load when you visit [http://localhost/](http://localhost/) which is equivalent to [http://localhost/index.html](http://localhost/index.html) if one exists or simply provides a directory listing of what is in /var/www/ if that is enabled in your configuration settings.

Each subfolder should have an index.html if you want something to load by default when that folder is accessed. So, for example, if you have /var/www/folder1/index.html then it is loaded when you visit [http://localhost/folder1/](http://localhost/folder1/)

---

