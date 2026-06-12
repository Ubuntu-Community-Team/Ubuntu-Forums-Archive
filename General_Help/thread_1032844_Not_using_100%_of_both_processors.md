---
title: "Not using 100% of both processors"
date: 2009-01-06
forum: General Help
---

### Post by zbikem on 2009-01-06
I'm running an FEM simulation on a dual-core 64 bit machine.
Using system monitor, I notice that both processors are not being run to their maximum limits. That is, if processor 1 is running at 80%, processor 2 is at 20%, processor 1 at 60%, then processor 2 at 40% and so on.
Why don't both processors run at 100 %. This would greatly improve the speed.

Earlier today, I noticed both processors were running at 100%. I rebooted the system in between, and ever since, I am noticing this issue.

Would you know how I can get around this problem?

Sorry if this is a pretty dumb question, very new to Kubuntu. Would appreciate any help.

---

### Post by LateNiteTV on 2009-01-06
look into the *nice* command.

---

### Post by 2hot6ft2 on 2009-01-06
I don't know why you would want them at 100% seems to me that would mean it would have to slow down since it would be maxed. I don't think they are supposed to be equal since one process runs thru one and another process thru the other, That way both aren't running thru just 1.

I don't know if this just works during the boot up process or not but sounds like what you're talking about. So here's you a little tweak from here. [http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html#feel](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html#feel)

>      I thought I would post a "Bonus" tweak for all those with dual core CPU's.  This tweak will allow processes to be loaded concurrently allowing better utilization of dual core CPU's on boot up, without further adieu.
Open a terminal:

```
sudo gedit /etc/init.d/rc
```

Scroll down until you see:

CONCURRENCY=none

and replace with:

```
CONCURRENCY=shell
```

Enjoy!!!

     Questions?  Comments?  Suggestion to add something feel free to contact me on the forums.

Best regards,

TheeMahn

---

### Post by zbikem on 2009-01-06
Thanks for the replies guys. I think I didn't describe the problem very well at first. I'll give it another shot.

I'm running some models using the software COMSOL Multiphysics to solve an FEM problem. One of the solvers (PARDISO) supports multi-core systems to split the load between multiple cores if available. Thus, if I have a dual core processor I should get a solution in less time. I would also expect both processors to be doing equal amounts of work for intensive problems.

That used to be the case, until about 4 hours ago, when I rebooted the computer. Ever since, I am noticing that only one processor maxes out at 100% while the other remains at about 20%. 

Any help would be most appreciated!

---

### Post by dcstar on 2009-01-06
> **2hot6ft2 said:**
> 
.........
I don't know if this just works during the boot up process or not but sounds like what you're talking about. So here's you a little tweak from here. [http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html#feel](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html#feel)

Loading start-up programs in parallel may well slow system start-up time as many of these things are disk-bound and the overhead of a flood of disk i/o requests will certainly slow most systems down, and it has no relevance to ongoing system operation.

If CPUs are not being utilised it is because the application is not using them, check the application in **top** or System Monitor.

---

### Post by sdennie on 2009-01-07
> **zbikem said:**
> Thanks for the replies guys. I think I didn't describe the problem very well at first. I'll give it another shot.

I'm running some models using the software COMSOL Multiphysics to solve an FEM problem. One of the solvers (PARDISO) supports multi-core systems to split the load between multiple cores if available. Thus, if I have a dual core processor I should get a solution in less time. I would also expect both processors to be doing equal amounts of work for intensive problems.

That used to be the case, until about 4 hours ago, when I rebooted the computer. Ever since, I am noticing that only one processor maxes out at 100% while the other remains at about 20%. 

Any help would be most appreciated!

If you are certain the app is multithreaded, you may need a command line flag or environment variable set to make use of multiple cores.  Also, "multithreaded" doesn't mean, "scales perfectly".  It's possible that there are long parts of your code that need to run in serial (or at least scale poorly) because it's not possible, not practical or very hard to parallelize them.  Is it possible that is the difference you were seeing?  Looking at different parts of the simulation before and after?

---

### Post by hangfire on 2009-01-07
> **zbikem said:**
> I'm running an FEM simulation on a dual-core 64 bit machine.
Using system monitor, I notice that both processors are not being run to their maximum limits. That is, if processor 1 is running at 80%, processor 2 is at 20%, processor 1 at 60%, then processor 2 at 40% and so on.
Why don't both processors run at 100 %. This would greatly improve the speed.

Earlier today, I noticed both processors were running at 100%. I rebooted the system in between, and ever since, I am noticing this issue.

Would you know how I can get around this problem?


I'm not familiar with your system monitor, but it may be summing total CPU core utilization to no more than 100%. You might try the program ***top*** with its various command-line options.

The only way to keep any processor running at 100% is to provide it with I/O at processor speed. This is only possible within the on-board CPU cache. Accessing main memory, disk, and/or network I/O all will keep CPU utilization below 100%, whether you have one core or 16.

The only time I've seen 100% utilization is in processes with bugs or poor coding, such as a busy-wait loop. While seeing 100% might seem satisfying, the CPU's were only spinning their wheels, so to speak.



-HF

---

### Post by sdennie on 2009-01-07
> **hangfire said:**
> 
The only time I've seen 100% utilization is in processes with bugs or poor coding, such as a busy-wait loop. While seeing 100% might seem satisfying, the CPU's were only spinning their wheels, so to speak.


That's possible, yes, but it's highly dependent on the application.  Things that are highly scalable (SETI@home comes to mind) can use an arbitrary number of CPUs at near "perfect scalability".  That doesn't mean that on a single core they are keeping the CPU fed in a 100% optimal way.  It just means that as you add CPUs, the performance increase is proportionate to the number of CPUs added.

Most applications don't scale well.  And, Amdahl's Law says that as you add CPUs to these applications, the performance benefits become less noticeable.  It also means that observing an application at any point during its runtime doesn't mean much about how well it scales.  You have to have a metric to that takes into account the total runtime (wallclock time is good for this!).

---

