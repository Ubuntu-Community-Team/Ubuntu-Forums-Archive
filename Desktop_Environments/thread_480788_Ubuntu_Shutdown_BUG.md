---
title: "Ubuntu Shutdown BUG"
date: 2007-06-21
forum: Desktop Environments
---

### Post by razeshkale on 2007-06-21
I think got BUG in Ubuntu, 
sometimes when i shutdown my Ubuntu i get Ubuntu logo after total shutdown of machine
and then i have to press power button to get fully shut down machine?

is it knows issue? or something new..

Help out

---

### Post by freshmeatz on 2007-06-21
i had that problem in dapper , but so far in fiesty the issue hasnt come back

---

### Post by NJC on 2007-06-22
I had that problem in Dapper as well but then it magically (IE I have no idea what changed it) went away. Agreed, it's an annoyance.

---

### Post by GerryB on 2007-06-22
> **razeshkale said:**
> I think got BUG in Ubuntu, 
sometimes when i shutdown my Ubuntu i get Ubuntu logo after total shutdown of machine
and then i have to press power button to get fully shut down machine?

is it knows issue? or something new..

Help out

Hi! This might solve your problem - it solved mine:
[http://ubuntuforums.org/showthread.php?t=359190](http://ubuntuforums.org/showthread.php?t=359190)

---

### Post by Sunforge on 2007-06-22
I've got Feisty running on several machines. One of them definitely exhibits this problem but the rest are fine. I've had a look through the installation logs and note that the problem machine.

I trawled through /var/log/messages on the problem machine and found the following entry:

"apm: disabled - APM is not SMP safe". 
 
Perhaps this is the problem? I don't have enough knowledge to take it much further but if you get the same message at least we'd know that there are some similarities.

---

### Post by bailout on 2007-06-22
It is one of those long running bugs that I keep hoping will be fixed but never is. I have the problem sometimes on my desktop but never on my laptop. There are lots of 'fixes' but nothing definitive. I used to think it was a kubuntu only bug but certainly in fiesty there are a lot of gnome users affected as well. What I do now is to logout and then shutdown from the kdm screen. I have never had a crash doing this but it can be easy to forget. Try it as it doesn't involve changing any files and I know someone else who has found it works but they were also using kubuntu.

---

### Post by razeshkale on 2007-07-05
yah,
Even on my machine it doesnt happen all the time?
Some time in week say once in week so freuency is very LOW
but we have to consider this as BUG only
so Devlopers can take care of that very soon

Cheers

---

