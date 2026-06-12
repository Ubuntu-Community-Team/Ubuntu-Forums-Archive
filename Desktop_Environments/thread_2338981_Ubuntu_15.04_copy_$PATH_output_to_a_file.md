---
title: "Ubuntu 15.04 copy $PATH output to a file"
date: 2016-10-03
forum: Desktop Environments
---

### Post by eightbits2010 on 2016-10-03
Perhaps my human  memory is having a problem, but I seem to recall that I could copy the output of executing $PATH to a file ? That doesn't seem to work and I would
like to do that.

---

### Post by mcduck on 2016-10-03
Try this:
```
echo $PATH > path.txt
```

---

### Post by ajgreeny on 2016-10-03
You should also be aware that 15.04 lost support some time ago and is therefore no longer a secure OS and gets no more updates or security fixes to any packages.

You should consider reinstalling with a supported version; I would recommend 16.04.1.

---

