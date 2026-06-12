---
title: "sh or bash - is there a differance?"
date: 2009-02-15
forum: General Help
---

### Post by sofasurfer on 2009-02-15
I read that I must have #!/bin/bash at the top of my script. I had been using #!/bin/sh.

I think that sh is a newer version of bash. Is this true? Are they interchangable at all? Or does it not matter because the OS will determine how to handle them?

---

### Post by heindsight on 2009-02-15
in ubuntu /bin/sh is dash which is smaller than bash, and faster for running scripts. but it doesn't have as many built in commands or the command line editing features that make bash so good for interactive use.

In general, if you're writing a script it's best to have it interpreted by dash, (if you put #!/bin/sh) at the top of your script ubuntu will use dash to interpret the script, but then you can't use any bash specific features. So if you really need bash specific features, run it with bash by putting #!/bin/bash at the top.

Have a look at: [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh) for more

---

### Post by sofasurfer on 2009-02-15
So they are interchangable to a point. sh (dash) is faster but lacking in some functionality. Bash does it all but its a little slower.

---

### Post by mb_webguy on 2009-02-15
Numerous shells are available for Linux.  Some (such as ash, bash, dash, ksh, and zsh) are compatible with sh, and others (such as csh, tcsh, and fish) aren't.  Scripts written for sh will work in any sh-compatible shell, but scripts written for specific sh-compatible shells that use those shells' extra functionality won't run on sh.  Scripts written for a non-sh compatible shell will only work in that shell.

---

### Post by brandon88tube on 2009-02-15
Thanks for the info, I never knew this.

---

### Post by heindsight on 2009-02-16
> **mb_webguy said:**
> Numerous shells are available for Linux.  Some (such as ash, bash, dash, ksh, and zsh) are compatible with sh, and others (such as csh, tcsh, and fish) aren't.  Scripts written for sh will work in any sh-compatible shell, but scripts written for specific sh-compatible shells that use those shells' extra functionality won't run on sh.  Scripts written for a non-sh compatible shell will only work in that shell.

Excellent explanation :)

Just to further clarify, sh refers to the Bourne shell which was the default shell on Version 7 Unix

---

### Post by ibutho on 2009-02-16
> **brandon88tube said:**
> Thanks for the info, I never knew this.

One thing to note as well is that on most Linux distros, /bin/sh is actually a symlink to /bin/bash. When you run /bin/sh, bash is run in a mode that is compliant with sh (The bourne shell). I think its only on Ubuntu and derivative distros where /bin/sh points to /bin/dash.

---

### Post by kaiju on 2009-02-16
> **ibutho said:**
> One thing to note as well is that on most Linux distros, /bin/sh is actually a symlink to /bin/bash.

Very true. On Arch, I have
```

$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2009-01-28 21:35 /bin/sh -> bash

```

Using #!/bin/sh makes scripts somewhat more 'portable' than bash, as most widely-used shells are bourne shell compatible. Scripts written for sh can still be run by many other shells because in them you can only use the greatest common divisor in terms of functionality.

---

