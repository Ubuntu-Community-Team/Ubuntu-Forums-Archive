---
title: "Conky Calendar Problem"
date: 2009-03-03
forum: General Help
---

### Post by alex.dason on 2009-03-03
Hello everyone,

My conky is having trouble displaying the calendar. I want ONLY this month and the next month, and it is only displaying the first four calendar weeks [starting on sunday] for this month, and the first four calendar weeks with an error in the last date.

The following is the code I use for the calendar [I got the code from this thread: [http://ubuntuforums.org/showthread.php?t=825676]:](http://ubuntuforums.org/showthread.php?t=825676]:)

```
${font nimbus mono l:size=9}${pre_exec cal -3 | cut -c23-64}
```

Using just *pre_exec cal* properly displays a singly month, but two months won't display properly.

Any help is appreciated,
attached is the screen shot of the malfunctioning calendar.

---

### Post by alex.dason on 2009-03-03
Any help?

---

### Post by alex.dason on 2009-03-12
One last bump.

Any help appreciated.

---

