---
title: "Java Issue"
date: 2009-02-12
forum: General Help
---

### Post by Awesom on 2009-02-12
I am trying to load a page that requires java and I do have java and it works but on this page it loads as just a grey screen the same problem happens with windows sometimes but I have no idea how to fix it on linux as I am new so if anyone knows all help is appreciated.

---

### Post by Awesom on 2009-02-12
Any ideas anyone please.. ?

---

### Post by geirha on 2009-02-12
Make sure you have [sun-java6-plugin](apt:sun-java6-plugin) installed, and make sure it is set as the plugin that firefox uses by running in a terminal: ```
sudo update-java-alternatives --set java-6-sun
```

---

