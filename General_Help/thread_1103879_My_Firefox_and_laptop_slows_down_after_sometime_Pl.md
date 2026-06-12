---
title: "My Firefox and laptop slows down after sometime? Please help!!!"
date: 2009-03-23
forum: General Help
---

### Post by Spaarkplug on 2009-03-23
Hi all,
I run Ubuntu Hardy Heron 8.04 on a 2.4 Ghz Core 2 Duo with 2GB RAM.
I do not know why this happens. But it always happens.
It happens after sometime my machine is on. So each time I have to restart my laptop. My terminal windows, Firefox browser, everything becomes sluggish and slow. I do not know why this happens. When it happens, I would do a top on my system,.. i understand many services there,.. but there are few in there that I have no idea about. Can I post a 'top' result of my machine the next time it happens? Can somebody please advise me what is going on to my laptop? I have restarted already like 5 times today. Each time it happens at a fairly significant interval. Each time it happens, i would be doing something fairly simple, like watching a movie online or browsing or downloading something. Nothing else.
Thanks SO much.

---

### Post by rolandrock on 2009-03-23
Hi Spaarkplug,

I am quite new too but here are some general rules that I follow to find a specific problem.

You must identify a specific problem or it is impossible for the good people of this forum to help you.

First, identify problem process:

Is your cpu busy?  Even 30-40% with lots of read/writes can impact performance.

Use 'top' and System->Administration->SystemMonitor to find which process is causing problems.

If one process is using a lot of cpu, try to find out what that process is doing.  You might want to kill that process (BE CAREFUL you must know what you are doing) and see if problem goes away.  If you can identify one program (like firefox) causing the problem, try uninstalling/reinstalling the program (using most basic settings).  

Look in these files for errors:

~/.xsession-errors
/var/log/syslog
/var/log/messages

Are file systems being filled?  If yes, what is filling file systems?  If a process is writing very fast to a log file, what is the error in the log file?

Have you made changes recently?

Have you installed programs/drivers that you are not sure about?

Google for your computer and your version of Ubuntu.  See if other people have found similar problems.

If you have made changes to your system recently, try to remove those changes.  Try to re-apply the changes if you need them.

If you still have no idea, back-up files that you need and re-install Ubuntu from disk.

If you have same problem on clean install, try another OS.  If other OS works (i.e. not hardware problem) then post '~/.xsession-errors', '/var/log/syslog' and last 200(?) lines of '/var/log/messages'.

Make sure you document any unusual steps you take in install procedure.

If problems are not fixed by a re-install then it is usually:
1. Incompatible hardware.
2. Broken hardware.
3. Incompatible/broken user.

Number 3 is a joke but it not very funny.  Like life ;-)

Good Luck

---

### Post by lisati on 2009-03-23
> **rolandrock said:**
> 
3. Incompatible/broken user.


HI all... some good ideas from rolandrock. This one reminds me of a defintion I once saw in a dictonary of terminology. It went something like this:
> cursor: person at computer waving fists angrily

---

