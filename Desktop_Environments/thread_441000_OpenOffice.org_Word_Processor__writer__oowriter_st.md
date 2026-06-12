---
title: "OpenOffice.org Word Processor / writer / oowriter stuck in semi fullscreen mode"
date: 2007-05-12
forum: Desktop Environments
---

### Post by StarkD on 2007-05-12
I had oowriter in full screen mode and restarted GNOME using Ctrl+Alt+Backspace. After that oowriter is stuck in a semi full screen mode. It fills up the whole screen but the menu is still visible. I am not able to see dialogue messages as they get stuck behind the program.

Screenshot:
[http://microansa.com/oowriter_bug_2007-04-14.png](http://microansa.com/oowriter_bug_2007-04-14.png)

I reported it as a bug a month ago:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/106506](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/106506)

Any idea what to do?

---

### Post by heimo on 2007-05-12
So what does ctrl+shift+J or double clicking on title bar do? Nothing at all?

---

### Post by StarkD on 2007-05-12
Ctrl+Shift+J brings it to full screen mode and then back to the "semi" full screen mode again.

I have no title bar to click on.

:-k

---

### Post by heimo on 2007-05-12
Does resetting OOo settings fix it?
```
mv ~/.openoffice.org2 ~/.openoffice.org2_old
```

---

### Post by StarkD on 2007-05-12
Yes that fixed it! :-D

---

### Post by twoseids on 2008-06-04
> **heimo said:**
> Does resetting OOo settings fix it?
```
mv ~/.openoffice.org2 ~/.openoffice.org2_old
```
Hey, me too! Thanks much!

---

### Post by bobblehat on 2008-06-28
Thanks - fixed mine too.

---

### Post by AlexisCC on 2008-07-04
Fixed it for me too!  Thanks thanks thanks

---

