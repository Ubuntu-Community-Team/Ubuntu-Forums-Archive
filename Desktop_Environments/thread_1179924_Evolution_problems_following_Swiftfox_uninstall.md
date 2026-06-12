---
title: "Evolution problems following Swiftfox uninstall"
date: 2009-06-06
forum: Desktop Environments
---

### Post by skiffler on 2009-06-06
In an attempt to get video working correctly with Jaunty (still not BTW), I installed Swiftfox. This didn't fix the problem so I uninstalled it again. Since then, I'm unable to follow a link from an HTML email in Evolution. All I get is this message in a pop-up in Evolution:

Failed to execute child process "/usr/lib/swiftfox/firefox" (No such file or directory)

Clearly, Swiftfox has changed a setting in Evolution and I've no idea how to fix it. Have reinstalled both Firefox and Evolution but this hasn't fixed things. I'm certain that someone here can tell me.

Thanks.

---

### Post by skiffler on 2009-06-06
OK, all fixed. When Swiftfox was uninstalled it failed to reset the checkbox in Firefox that checks whether Firefox is the default browser. As a result the system thought that Swiftfox still was, thus the error.

---

