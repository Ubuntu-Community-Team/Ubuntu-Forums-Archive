---
title: "Dumb question - using tee"
date: 2008-12-03
forum: General Help
---

### Post by zilla62 on 2008-12-03
I want to capture my gcc output by...

> gcc -c myfile.c | tee mylog.txt

Why is mylog.txt empty even though I get a screen full of errors? I use bash (why is tcsh not avail?)

BTW, the following works

> ls | tee myls.txt

that is, myls.txt contains the results of the ls command.

---

### Post by jgoguen on 2008-12-03
That's because errors go to a different output stream than output does.  The terminal just puts them together for you.  Use this command instead:
```
gcc -c myfile.c 2>&1 | tee mylog.txt
```
That will force the error stream (number 2) to go to the output stream (number 1) instead.  That will then give you what you're expecting.

---

### Post by zilla62 on 2008-12-03
Ah yeah. I used...
> gcc -c myfile.c |& tee mylog.txt

...with other shells but it errors on bash.

Thanks!!!

---

### Post by jgoguen on 2008-12-03
Glad to hear your problem is solved :)  Could you mark this thread as solved?  Doing so lets other people browsing know that this thread provided you with a working solution.  To mark a thread as solved, click on the **Thread Tools** link just above and to the right of your first post.  A menu will appear, one of the options there is to mark the thread solved.

Thanks :)

---

