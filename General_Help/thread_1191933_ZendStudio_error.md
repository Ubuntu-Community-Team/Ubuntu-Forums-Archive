---
title: "ZendStudio error"
date: 2009-06-19
forum: General Help
---

### Post by ongun.kanat on 2009-06-19
I'm trying ZendStudio for Eclipse 6.1.2.After the setup, Its WYSIWYG designer isn't working.I fixed with a sh script for xulrunner.

The script:
> 
#!/bin/sh
MOZILLA_FIVE_HOME=/usr/lib/xulrunner
if [ $LD_LIBRARY_PATH ]; then
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME:$LD_LIBRARY_PATH
else
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME
fi
export MOZILLA_FIVE_HOME LD_LIBRARY_PATH 
'/home/ongun/Zend/ZendStudioForEclipse-6.1.2/ZendStudio' -vm /usr/lib/jvm/java-6-sun-1.6.0.13/bin/java


Now, I's WYSIWYG designer is working but when I try add something It shows an error:

The Error:
> An error has occurred when activating this view
GetMethodInfoForName failed  (0x80070057)



How can I fix it?

---

### Post by ongun.kanat on 2009-06-19
any ideas?

---

