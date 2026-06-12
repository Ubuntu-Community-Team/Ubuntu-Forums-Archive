---
title: "question about aptitude"
date: 2006-08-06
forum: Desktop Environments
---

### Post by JohnJSal on 2006-08-06
I know the advantage of aptitude is that it can uninstall dependencies, but what if you've installed program A, and it has dependencies, then you later install program B and it shares some of those dependencies. Finally, you uninstall program A with aptitude. Does it remove the dependencies and break program B, or does it know to leave them when another program uses them?

Thanks.

---

### Post by Jagot on 2006-08-06
I'm pretty sure that aptitude will not remove any packages which other programs you have are dependent on.

---

### Post by teasum on 2006-08-06
That's the beauty of aptitude... it will only remove dependencies that are unused.  If any other program depends on a package, it will leave it alone.

---

### Post by JohnJSal on 2006-08-06
Awesome! I gotta say, Ubuntu is pretty fun so far. I just set up Firefox to use all my settings from Windows, and it works great!

---

