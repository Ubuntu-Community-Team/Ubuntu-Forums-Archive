---
title: "system hang or slow"
date: 2019-03-17
forum: Desktop Environments
---

### Post by m.eraj1995 on 2019-03-17
Dear Sir,

In windows machine we can delete temp file and etc if system is getting hang and what to do in ubuntu because my machine is getting .

---

### Post by TheFu on 2019-03-17
Unix systems don't like full file systems, especially in /var/.  Don't let there be less than 1-2G of storage free.

You can check which processes are using all the CPU and RAM. Use '**top**'.
If the GUI appears to lock up, that doesn't mean the OS is having any issues.   Getting slow is how the OS provides end-users feedback that the system is being taxed.  After looking at system resource use, via top, if the RAM and swap are almost used up, then the answer is clear.  Close some large applications - like the browser or huge email program or video editor or ... whatever else is eating all the RAM.

Besides top, you can use **vmstat** and **free** to see virtual memory use and RAM use.

Lastly, sometimes hardware that is slow is from hardware faults. Check the system log files in /var/log/ for problems.  A bad SATA cable can make a system really slow. So can a failing storage device. Always check the log files.

If you have another computer, it is handy to ssh into the problem computer to check the logs while it is still running.  Again, a slow GUI could just be a GUI issue.  IME, that is usually the issue, while the underlying OS is fine.

---

