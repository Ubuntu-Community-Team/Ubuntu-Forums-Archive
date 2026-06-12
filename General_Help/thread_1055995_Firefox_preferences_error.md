---
title: "Firefox preferences error"
date: 2009-01-31
forum: General Help
---

### Post by yoman82 on 2009-01-31
Although I can find the bookmarks and history files in nautilus, they are not recognized in firefox, leaving a blank history and bookmarks area which refuses to take any new information. I also cannot use the go back option. Cookies are still there, oddly.

---

### Post by tom66 on 2009-01-31
I am having a similar problem, broken back/forward buttons. And search doesn't work. Tell me, does going to Downloads or Add-ons crash Firefox?

---

### Post by yoman82 on 2009-01-31
Nope, it still remembers my downloads and addons.

---

### Post by tom66 on 2009-01-31
I may have discovered the cause of the problem, but how to solve it is another issue.

```

Error: this.bookmarks is undefined
Source File: file:///usr/lib/xulrunner-1.9.0.5/modules/utils.js
Line: 884

```

In the error console, do you see this as well? You might need to scroll down. This error comes up numerous times so appears to be a fault somewhere in the code.

---

### Post by yoman82 on 2009-01-31
I have no idea how to access the error console. And I can't report it to launchpad, as Firefox gives me a "Page cannot be displayed" whenever I submit an error report.

---

### Post by tom66 on 2009-01-31
It's under Tools.

---

