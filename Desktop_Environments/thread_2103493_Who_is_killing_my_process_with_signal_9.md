---
title: "Who is killing my process with signal 9?"
date: 2013-01-10
forum: Desktop Environments
---

### Post by lutovich on 2013-01-10
Hello!

Situation(short):
Some processes on my machine a quite randomly killed with signal 9 without a visible reason. No out-of-memory, out-swap-space and other stuff is noticed.

Situation(long):
I have a development server with 10 concurrently running Redis(in-memory key-value storage) instances. Redis tries to persist once in a while and quite rarely fails with error: forked for persistence process is killed with signal 9. Server has 24gb of RAM and as a rule no more than 5gb is used, so no out-of-memory is possible. And there is 10gb swap partition.

Monitoring(with Ganglia) is turned on and no OOM for sure.
I've searched /var/log/kern.log but did not find anything useful there.
/proc/sys/vm/overcommit_memory is set to 1
/proc/sys/vm/overcommit_ratio is set to 50(default)
Using Ubuntu 12.04.1 LTS

Any suggestions why this can happen or where to look for the answer would be highly appreciated!

Thanks in advance!

---

### Post by f8l_0e on 2013-01-10
[http://redis.io/topics/persistence]("http://redis.io/topics/persistence")

Pay particular attention to the section on "Snapshotting" and "How it works."  According to that information, the behavior is by design.

---

### Post by lutovich on 2013-01-11
I know how it works. I am not sure you've read my case correctly.
Persistence process is killed by something with SIGKILL. According to Redis logs it can be killed during writing DB to disk or even after it - when DB is already written.
So the question is why system(or may be smth else?) is killing this process without any visible reason(no OOM and stuff like that) ?

---

