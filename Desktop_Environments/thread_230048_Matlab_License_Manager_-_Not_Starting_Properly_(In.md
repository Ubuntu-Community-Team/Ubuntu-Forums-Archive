---
title: "Matlab License Manager - Not Starting Properly (Intermittent)"
date: 2006-08-05
forum: Desktop Environments
---

### Post by m0nstr42 on 2006-08-05
I seem to get random errors when trying to start the license manager manually with /opt/matlab7/etc/lmstart .. About 70% of the time I get

```
dan@valis:~$ /opt/matlab7/etc/lmstart

Checking license file for local hostname and local hostid . . .

Taking down any existing license manager daemons . . .
trap: usage: trap [-lp] [arg signal_spec ...]
    Note: license manager did not come down properly . . .
```

and the other 30% of the time it starts normally.  There's not really anything different between the times that it works and when it doesn't, e.g. this morning I got the error, hit up and enter on the terminal (to repeat the command), it errored again, repeat, then it worked.  In the span of a few seconds.  Sometimes it just works on the first try, sometimes I have to hit up-enter a few times, sometimes I have to walk away for a minute or two.  I'm not running any weird background processes that would interfere, I don't think.

I tried looking at the actual lmstart script, but my scripting chops weren't good enough to decipher the source of the problem.

---

### Post by m0nstr42 on 2006-08-22
Bump.  This is a really obnoxious problem.

---

### Post by taurus on 2006-08-22
> **m0nstr42 said:**
> Bump.  This is a really obnoxious problem.
Shouldn't you be contacting Matlab instead of bumping!!!

---

### Post by m0nstr42 on 2006-08-22
OK, you got me.  I swear I've searched the MathWorks forums before, but because I'm anal I searched again before bitching about there not being an answer - and just to prove me wrong there is an answer now:  [http://www.mathworks.com/support/solutions/data/1-Q4CNN.html?solution=1-Q4CNN](http://www.mathworks.com/support/solutions/data/1-Q4CNN.html?solution=1-Q4CNN)

Anyways, I still don't understand why it worked intermittently - and I'd like to understand.  Theoretically, linux people are all about exploring the way that software works, so I thought maybe someone here would enjoy explaining to me why this was happening.  The MathWorks site says it is an incompatibility between Matlab and bash 3.0+, but usually "incompatibility" means "broken" - not "broken except on every third or fourth try", so it's not a very satisfying explanation.  It seems to have something to do with the way the trap command works.

---

### Post by taurus on 2006-08-22
Well, have you tried using csh/tcsh instead of bash???

---

### Post by m0nstr42 on 2006-08-22
The MathWorks suggestion fixes the problem.  I can use bash and it works now.

Now I am calling for someone to suggest an explanation of what the problem was all about - especially why it was intermittent.  Intermittent software problems are a pet peeve of mine.

---

### Post by taurus on 2006-08-22
It has something to do with the library!!!  And if it's a pet peeve of yours, then maybe you can come up with a fix and charge it to Matlab!!!

---

