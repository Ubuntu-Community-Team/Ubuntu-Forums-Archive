---
title: "how to run a script upon closing a program?"
date: 2009-03-22
forum: General Help
---

### Post by Jameshardy88 on 2009-03-22
Hi i was wondering how i could auto-run a script upon closing a program?

---

### Post by lykwydchykyn on 2009-03-22
This is usually done by running a "wrapper" script instead of the actual program, like so:
```

#!/bin/bash
#Wrapper script for someprogram

someprogram
post_exec_script

```
Occasionally that fails because some programs fork to a new process and exit, but usually that will do the trick.


Or of course you could launch from the CLI like so:
```

someprogram && myscript

```
That will run "myscript" upon successful exit from someprogram.

---

### Post by Jameshardy88 on 2009-03-22
im trying to use it with rhythmbox. I do actually already have a wrapper script for it that starts a conky screen when i open the program. Should i just add this to the bottom?

rhythmbox
post_exec_script
myscript

?

or have i got that totally wrong lol

---

### Post by lykwydchykyn on 2009-03-22
Sorry, "post_exec_script" was just an example of a script name.  Just put your script on the next line after rhythm box.

Didn't make that clear.

---

### Post by Jameshardy88 on 2009-03-22
ok sorry just a bit confused, how you set it run after the program has closed though? or does typing after the program automatically mean after closure?

---

### Post by MaxIBoy on 2009-03-22
Unless you do something fancy, a bash script like this:
```
#! /bin/bash
program1
program2
```
Will not run program2 *until* program1 exits.

---

