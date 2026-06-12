---
title: "Aptitude error redirection"
date: 2009-01-14
forum: General Help
---

### Post by rozilla on 2009-01-14
I'm trying to get aptitude to redirect install errors to a log file, as follows:

```
$ sudo aptitude install -q package1 package2 package3 2>install-err.log
```

But it won't let me log errors. It works with 1>, where it logs *everything*, but I need it to show the normal output and redirect the errors into a logfile.
How do I achieve this?

---

### Post by rozilla on 2009-01-15
Well, it turns out the answer is

```
$ sudo aptitude install -q package1 package2 package3 2>&1> install-err.log
```

Unfortunately, that suppresses all output, even the interactive [Y/n] stuff that sometimes comes up. How do I keep the interaction from being surpressed?

---

