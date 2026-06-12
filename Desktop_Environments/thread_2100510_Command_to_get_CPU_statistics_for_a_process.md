---
title: "Command to get CPU statistics for a process"
date: 2013-01-02
forum: Desktop Environments
---

### Post by vksingh on 2013-01-02
Hi All,

I use mpstat to get CPU statistics in my Ubuntu 12.10 desktop.

Linux 3.6.7 (viveks)     02/01/2013     _x86_64_    (8 CPU)

13:10:08     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
13:10:08     all    2.37    0.19    1.01   14.54    0.00    0.02    0.00    0.00   81.86

**I want to get the above CPU statistics for a process (by giving the process ID). If there is any existing command in linux then please let me know. **

Thanks,
Vivek

---

### Post by papibe on 2013-01-02
Hi vksingh.

Take a look at 'ps' and 'top'.

Happy New Year!

---

### Post by sanderj on 2013-01-02
Does this help?

```
sander@R540:~$ top -bn1 | grep  -e "PID" -e mysql
  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
 1185 mysql     20   0  475m 3028 1356 S   0.0  0.1   1:20.01 mysqld
sander@R540:~$ 
sander@R540:~$ top -bn1 | grep  -e "PID" -e 1185
  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
 1185 mysql     20   0  475m 3028 1356 S   0.0  0.1   1:20.03 mysqld
sander@R540:~$


```

---

### Post by vksingh on 2013-01-02
Hi Sanderj,

Thanks for your response :-)

With top command, i get aggregate %CPU for a process, but I am looking for all the statistics values for the CPU like the following:
    **%usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle**

Please tell me any command to get the results in above format.

Thanks,
Vivek

---

### Post by sanderj on 2013-01-02
I see. Out of curiosity: why do you need that info?

Did you read "man proc", especially the stuff at "/proc/[pid]/stat"?

---

### Post by vksingh on 2013-01-02
Hi Sanderj,

I checked /proc/pid/stat

I see following processor related parameters:

 utime %lu   Amount of time that this process has been scheduled in user mode, measured in clock ticks (divide by sysconf(_SC_CLK_TCK).   This  includes  guest  time,
                          guest_time  (time  spent  running  a  virtual CPU, see below), so that applications that are not aware of the guest time field do not lose that time from
                          their calculations.

              stime %lu   Amount of time that this process has been scheduled in kernel mode, measured in clock ticks (divide by sysconf(_SC_CLK_TCK).

              cutime %ld  Amount of time that this process's waited-for children have been scheduled in user mode, measured in clock ticks (divide by  sysconf(_SC_CLK_TCK).   (See
                          also times(2).)  This includes guest time, cguest_time (time spent running a virtual CPU, see below).

              cstime %ld  Amount of time that this process's waited-for children have been scheduled in kernel mode, measured in clock ticks (divide by sysconf(_SC_CLK_TCK).

              priority %ld
                          (Explanation for Linux 2.6) For processes running a real-time scheduling policy (policy below; see sched_setscheduler(2)), this is the negated scheduling
                          priority, minus one; that is, a number in the range -2 to -100, corresponding to real-time priorities 1 to 99.  For processes running under  a  non-real-
                          time  scheduling policy, this is the raw nice value (setpriority(2)) as represented in the kernel.  The kernel stores nice values as numbers in the range
                          0 (high) to 39 (low), corresponding to the user-visible nice range of -20 to 19.

                          Before Linux 2.6, this was a scaled value based on the scheduler weighting given to this process.

              nice %ld    The nice value (see setpriority(2)), a value in the range 19 (low priority) to -20 (high priority).

What is difference between **priority** and **nice** in above.

Can you help me to understand how these are related to [B]%usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle


[/B]Thanks,
Vivek

---

