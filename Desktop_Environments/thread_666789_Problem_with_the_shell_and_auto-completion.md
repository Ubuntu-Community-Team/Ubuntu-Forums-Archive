---
title: "Problem with the shell and auto-completion"
date: 2008-01-13
forum: Desktop Environments
---

### Post by armandino on 2008-01-13
Recently I reinstalled ubuntu and I noticed a small but annoying problem (which I didn't have before) with shell's auto-completion.

Say I have a $SOME_DIR environment variable.

> export SOME_DIR=/path/to/some/directory

If I type $SOME_ and hit tab I get

> cd \$SOME_DIR

instead of

> cd $SOME_DIR

Notice how the shell escapes the dollar sign with a slash.

Has anyone come across this problem before? any suggestions as to how to fix this?

---

### Post by armandino on 2008-01-15
I haven't found a proper solution to this, but there is a workaround. The escaping of the dollar sign in environment variables can be avoided by pressing Esc followed by tab.

For example,

```
# cd $SO + [Esc] + [Tab]
# cd $SOME_DIR
```

If anyone knows a proper solution (i.e. without having to it Esc), please post it.

---

### Post by armandino on 2008-02-13
archtoad6 on Linux Questions posted a solution to this problem if anyone is interested. -- [link]("http://www.linuxquestions.org/questions/linux-general-1/bash-auto-complete-of-environment-variables-613203/")

---

