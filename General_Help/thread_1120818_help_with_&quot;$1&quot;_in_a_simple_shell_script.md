---
title: "help with &quot;$1&quot; in a simple shell script"
date: 2009-04-09
forum: General Help
---

### Post by megamania on 2009-04-09
My knowledge of bash scripting is very limited, but I'm trying to improve a script I recently wrote.

Let's say I have this:
```
INPFILE="movie.avi"`
mencoder $INPFILE [other options follow)
```
What I would like to do is: if $1 is empty, then use "movie.avi", else use that parameter by having $INPFILE="$1".

I tried $INPFILE="$1" (and $INPFILE=$1) on its own, and it doesn't work - I guess I'm using the wrong formatting/quotes here...

Can you help me?

---

### Post by sdennie on 2009-04-09
Try a short circuit OR.  Here is the psuedo-code:

```

Movie == $1 || movie.avi

```

That will choose $1 if it exists and movie.avi if it doesn't.

---

### Post by megamania on 2009-04-09
> **sdennie said:**
> Try a short circuit OR.  Here is the psuedo-code:

```

Movie == $1 || movie.avi

```

That will choose $1 if it exists and movie.avi if it doesn't.
That's a quick reply! I'll try that.

Out of curiosity, however, what's wrong with INPFILE=$1?

In other words, how can I assign the contents of $1 to a variable?

Thanks!

---

### Post by sdennie on 2009-04-09
Dunno.  Assigning $1 to a variable should work just fine.  If it exists.

---

### Post by megamania on 2009-04-09
> **sdennie said:**
> Dunno.  Assigning $1 to a variable should work just fine.  If it exists.
Fixed it. It works, thanks.

However, I tried this:
```

#!/bin/bash
echo parameter=$1
TEST == $1 || movie.avi
echo $TEST
```
If I run it with "Ubuntu" as parameter, I get:
```

sh test.sh ubuntu

parameter=ubuntu
test.sh: 4: TEST: not found
test.sh: 4: movie.avi: not found
```
EDIT: same things happens with no parameter

---

### Post by sdennie on 2009-04-09
It was pseudo-code.  ;)

I was giving you the information but not the details (and looking back, not even giving the information well).  You probably want:

```

TEST=$1 || movie.avi

```

Assuming that works in bash.  I think it does though.

---

### Post by Slim Odds on 2009-04-09
> **sdennie said:**
> Try a short circuit OR.  Here is the psuedo-code:

```

Movie == $1 || movie.avi

```That will choose $1 if it exists and movie.avi if it doesn't.

If you're using bash, you can do this:```
MOVIE=${$1:=movie.avi}
```I highly recommend the Advanced Bash Scripting Guide. It's a great tool both for learning and as a reference.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by megamania on 2009-04-09
> **Slim Odds said:**
> If you're using bash, you can do this:```
MOVIE=${$1:=movie.avi}
```
Thanks, but I get a "bad substitution error". 

I'll check out the guide you're suggesting.

---

### Post by Slim Odds on 2009-04-09
> **megamania said:**
> Thanks, but I get a "bad substitution error". 

I'll check out the guide you're suggesting.

I haven't used this technique much myself.... my bad.

Try something like this:```
MYTMP=$1
MOVIE=${MYTMP:=movie.avi}
```For some reason, you cannot put positional parameters in the ${VAR:=SOMETHING} thing.

---

### Post by megamania on 2009-04-09
> **Slim Odds said:**
> Try something like this:
It works! Thanks a lot!

(now, if I could only remember how to mark the thread solved...)

---

