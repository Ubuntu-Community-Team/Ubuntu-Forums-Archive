---
title: "Help using Find command"
date: 2009-03-24
forum: General Help
---

### Post by ivallejo on 2009-03-24
Hi, I'm wondering what I'm doing wrong here.

I need to run a command that displays files named "Bing", but everytime I run the find program I get results that don't make sense.

The command needs to search 3 directories up from my current directory, I'm sure it's a syntax error but reading the manpage is just making me scratch my head... I think I'm using the proper syntax.

Anyways, this is how I'm typing it:

find ../../.. -name "Bing"

But it keeps returning so many files.

for instance one result reads like this:

../../../home/logins/censored-login/.gconf : Permission denied

The string "Bing" is no where in that path...  What am I doing wrong here?

---

### Post by snova on 2009-03-24
You're using it correctly, however it is trying to search through directories that you don't have permission to access.

The simplest way to ignore the errors would be to redirect error output:

```
find ../../../ -name "Bing" **2>/dev/null**
```

Though that would catch all errors (including those from find itself), not just permission problems.

---

