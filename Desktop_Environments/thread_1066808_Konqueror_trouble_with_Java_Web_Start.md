---
title: "Konqueror trouble with Java Web Start"
date: 2009-02-11
forum: Desktop Environments
---

### Post by r.stiltskin on 2009-02-11
I am unable to run the demos from the Sun Java tutorial/uiswing/examples in Konqueror.  Konqueror is trying to run them using Java Web Start 5.0 -- the tutorial examples want Web Start 6.0 so they abort.

I have java-6-sun/jre/bin/javaws selected as the default in update-alternatives.  I do not have this problem with Firefox -- Firefox is running the examples using Java Web Start 6.0 by default.

I can't find anything in Konqueror's menus to configure this.  Where is it hiding?

Ed: Solved - in Settings/Configure Konqueror/File Associations/ Known Types/application/x-java-jnlp-file, moved Sun Java 6 Web Start up to first in Application Preference Order.

But, as there are 3 applications listed there (Sun Java 6 Web Start, Sun Java 5 Web Start, and OpenJDK Java 6 Web Start), I don't know why Konqueror doesn't offer a choice when loading a web application.  It appears that only the first application preference is actually available.

---

