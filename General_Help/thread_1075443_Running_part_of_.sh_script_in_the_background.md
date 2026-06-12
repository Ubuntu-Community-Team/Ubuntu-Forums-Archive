---
title: "Running part of .sh script in the background"
date: 2009-02-20
forum: General Help
---

### Post by change_mode on 2009-02-20
I have a set of problems:

1. A program won't run with compiz, so I use a script to run it.

```
metacity --replace &
start_program
compiz --replace
exit 0
```

2. I need to run the script in a terminal, because if I don't, the program writes all the output to .xsession-errors. Probably can't fix this, as it's the program's fault.
3. Re-enabling compiz creates some (unimportant) error messages. No problem actually, but it means the terminal won't close automatically. It stops at the error.

What can I do for the 'compiz --replace' part to run in the background, so the terminal window closes when I shut down the application?

---

### Post by yeleek on 2009-02-20
how about?

[PHP]compiz --replace & exit[/PHP]

---

### Post by change_mode on 2009-02-20
I forgot to mention this: when I try to background 'compiz --replace' with &, for some reason it doesn't work. Compiz just won't load.

I also tried 

```
#!/bin/bash
compiz --replace
```

and call that script from the first script 

```
./compiz.sh &
```

Same result. It won't load with the & option.

---

### Post by SeanHodges on 2009-02-20
> **change_mode said:**
> 2. I need to run the script in a terminal, because if I don't, the program writes all the output to .xsession-errors. Probably can't fix this, as it's the program's fault.

Can't you redirect the output somewhere else?

```
myscript.sh &> /var/log/myscript.log
```

> **change_mode said:**
> 3. Re-enabling compiz creates some (unimportant) error messages. No problem actually, but it means the terminal won't close automatically. It stops at the error.

What can I do for the 'compiz --replace' part to run in the background, so the terminal window closes when I shut down the application?

If you source the script instead of launching it, it should inherit the existing terminal session and your "exit 0" will actually close the terminal when the script finishes:

```
source ./myscript.sh
```

This assumes that the script is actually stopping, otherwise you'll need to pass some magic to compiz to tell it to stop, and I'm not sure what that might be.

---

### Post by change_mode on 2009-02-21
Redirecting the output doesn't work, I tried /dev/null.

I'm just wondering why & doesn't work with compiz --replace. There must be a way.

---

