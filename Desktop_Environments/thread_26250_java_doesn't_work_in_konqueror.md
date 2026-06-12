---
title: "java doesn't work in konqueror"
date: 2005-04-12
forum: Desktop Environments
---

### Post by F for Fragging on 2005-04-12
I followed the instructions from ubuntuguide:

[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)
[http://www.ubuntuguide.org/#jre-mozilla](http://www.ubuntuguide.org/#jre-mozilla)

Java is installed (java apps such as azureus work), but Konqueror doesn't recognize the plugin and Java doesn't work in the browser.

Any ideas?

---

### Post by kal_zakath on 2005-04-12
I got it to work simply by telling konqueror the exact place of my java bin file, so in my case it's : /usr/java/j2re1.4.2_06/bin/java

You can configure it there : Configure Konqueror -> Java & javascript -> Path to java executable

---

### Post by F for Fragging on 2005-04-13
Thanks a lot, doing that made it work for me as well.

---

