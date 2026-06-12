---
title: "xfce permissions, auto unchecking what I set."
date: 2015-07-09
forum: Desktop Environments
---

### Post by dgosborn on 2015-07-09
I'm trying to set permissions on a file and it is AUTOMATICALLY UNCHECKING the 'execute' checkbox and also countermanding the group permissions I set. Any comments?

---

### Post by Habitual on 2015-07-09
Are you attempting to 'set' graphically or using command-line?
We need more info about 'how' and to 'what/where' basically.

---

### Post by dgosborn on 2015-07-09
using xfce (graphically)
To be clear, I'm not saying it accepts my command then undoes it, It actually unchecks the box before I can hit ok.

---

### Post by Habitual on 2015-07-10
What is the user:group on the directory once above it?

example: Please use terminal and issue:
```
ls -ld path/to/directory/file/ path/to/directory
```
where "path/to/directory/file/" is the actual path to the file and "path/to/directory" is the actual directory once above it.
and paste the results here.

Thank you,

---

