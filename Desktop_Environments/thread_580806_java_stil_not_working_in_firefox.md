---
title: "java stil not working in firefox"
date: 2007-10-19
forum: Desktop Environments
---

### Post by JvdS45 on 2007-10-19
after i started firefox the browser asked for java because the website was needed it. But when it installed and restart the webbrowser still asking for java which it is installed what can i do to recover and using firefox normally

---

### Post by jespdj on 2007-10-19
Install sun-java6-plugin:
```
sudo apt-get install sun-java6-plugin
```
And restart the browser.

Are you using the 32-bit or the 64-bit version of Ubuntu? Note that there is no Sun Java plug-in for the 64-bit version.

---

