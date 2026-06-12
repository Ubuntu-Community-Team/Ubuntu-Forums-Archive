---
title: "kdeinit starts 195 (!) python threads"
date: 2008-10-22
forum: Desktop Environments
---

### Post by Dryer Lint on 2008-10-22
Recently, applications would occassionally refuse to start. On the terminal there was some kind of error message about "too many connections" to the X server.

So I looked at the processes and there were many many many python threads. 195 the last time I checked!

After a "killall python" it was still 194, but a "killall -9 python" took care of that. I didn't notice any adverse effects so far.

What is this and how can I prevent it from happening again?

---

### Post by piemonkey on 2008-11-15
I've not had the 'too many connections' problem, but kdeinit has spawned 126 python threads (I just did a fresh boot). I don't know how much of an impact these have on my system, but it can't be good, unless there really is a need for them...

They all seem to use up the same amount of memory, and occasionally use a small amount of processor time.

If anyone knows what causes these, and if they are actually doing something, and if not, how to prevent them from starting, I'd really like to know

---

### Post by Vadi on 2008-11-15
I had the too many connections problem when the laptop was up for a long period of times back in 7.10. Not since though...

---

### Post by piemonkey on 2008-11-18
Ok, I got rid of them by telling kubuntu to start a new session, rather than reloading the last session, that explains why kdeinit was starting the threads.

I don't know where they came from in the first place though...

---

### Post by lbmounse on 2009-01-14
I'm having a similar problem.

kdeinit is loading up only one python thread, but this thread is using up to 80% of my CPU, and is slowing down my computer.

I've tried telling kde to load a fresh session, but that did not work.
The only thing that works is manually killing the thread.

Does anyone have any good suggestions?

---

