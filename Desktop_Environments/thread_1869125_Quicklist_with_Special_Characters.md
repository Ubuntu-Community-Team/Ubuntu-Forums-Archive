---
title: "Quicklist with Special Characters"
date: 2011-10-25
forum: Desktop Environments
---

### Post by rmccarri on 2011-10-25
Hi Everyone,
Does anyone know how quicklist items in a custom launcher are executed?  I'm having trouble with one that I'm adding to my chrome launcher.  Google reader uses "%2F" to represent forward slashes in some of its urls.  Using

```
google-chrome --new-window url_with_percent_signs
```

at the command line works fine.  I can even execute it with exec.  However, when I add this in the Exec= field of the custom quicklist, it ignores everything after the first percent sign.  I've tried escaping it out with a backslash and adding single and double quotes to no avail.  I've gotten around it by writing a bash script to execute the command and pointing the launcher to the script instead, but it would be better if I could just figure out how to issue commands with special characters in the future.  Any help would be greatly appreciated.
Rob

---

