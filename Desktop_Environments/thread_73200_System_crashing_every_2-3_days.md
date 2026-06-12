---
title: "System crashing every 2-3 days"
date: 2005-10-08
forum: Desktop Environments
---

### Post by guliver on 2005-10-08
I am running Ubuntu with latest updates and all I use is Samba and TeamSpeak server.

The problem is that every 2-3 days system froze, servers are not working. I can move mouse pointer but if I try to open Firefox for example it just freezing ...

Is there any way how I can see what cause that problem?

(Before I used Fedora with same aplications and .conf files and it could run for 3-4 weeks without problem)


Can anybody help?

Thanks guys

---

### Post by GoA on 2005-10-08
Could you tell more about your system, drivers, software, system logs etc.? It's hardf to help if you don't tell any facts.

---

### Post by Zwack on 2005-10-08
Without any additional information all people can tell you is that it's not happening with them...  

Given that Fedora works, it is less likely to be a hardware fault.

You need to do some investigation yourself if we are to be able to help you.

Does this happen at a certain time or interval (after 52 hours uptime say)...

Does this happen after something else, a certain screensaver ran, you connected to /from a specific other machine.

Any connections between this and another event might be worth looking into.

Now, for practical suggestions...  

What is freezing? if it's X can you switch to a text console and run some commands?  

If so then try any or all of the following...

uptime - Look at the load average... is it above 1.0 ?

$ uptime
 10:31:54 up  3:05,  2 users,  load average: 0.12, 0.30, 0.39

If it is above 1.0 then you may have runaway processes, something is using all of your CPU...

next try vmstat 5 2 and look at the si so and free columns.  If si and so are 0 and free is a large number (over a few hundred preferably)  then you don't have any memory problems.  You are looking at the bottom line not the top one... The top one is cumulative since boot and is not very helpful.  You want to know what is happening now.

If si and so are both high then you are paging memory in and out (memory leak somewhere or just using a lot of memory)...

If free is low then you don't have mich memory.

$ vmstat 5 2
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 6  0      0  40076  99844 131364    0    0    25    12 1093  1560  5  1 93  1
 0  0      0  40084  99852 131364    0    0     0     8 1068  1434  0  0 100  0

Finally top will show you a summary of memory/swap/cpu and what is busy...

top -d 5 will show you something like this...

top - 10:42:03 up  3:15,  2 users,  load average: 0.02, 0.10, 0.23
Tasks:  71 total,   1 running,  70 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6% us,  0.8% sy,  0.0% ni, 97.6% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    516380k total,   479136k used,    37244k free,   100328k buffers
Swap:  1510068k total,        0k used,  1510068k free,   133364k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 5450 root      15   0  169m  28m 7328 S  0.8  5.6   1:51.87 Xorg               
 6407 loginid     15   0 13576 7952 6048 S  0.6  1.5   0:03.99 metacity           
 6438 loginid     16   0 18024 9.9m 7760 S  0.2  2.0   0:02.47 wnck-applet        
 8438 login...

The process list fills the screen but it tells you which process is busiest...  

If the process at the top of the list stays there for multiple cycles then it's probably  runaway.  (it might just stay near the top for multiple cycles)...

Of course if you can't run ANYTHING then this won't help much... In that case you might want to check the log files in /var/log/ for any errors or warnings.  You could also set up sar and run that and after you've rebooted see what it can tell you.

If none of this helps then you may need to search for custom monitoring scripts and/or write your own.

I know that I had problems with some screensavers freezing the machine so I disabled a them and that resolved it...

I hope that this helps,

Z.

---

### Post by duan on 2005-10-08
I had a similar situation on my ASUS a7n8x + AMD motherboard, 2 years old now.

I got the same reactions as you mentioned only after starting to use ubuntu fulltime.

Since the crashes were random and grub memtest86+ said the RAM was OK I figured it was not the software. 
Improving airflow over my motherboard solved it for me. 

Most pc boxes are badly designed for cooling and especially so on my cheap rig, some voltage regulators and related circuitry on cheap modern boards take a lot of beating and keeping them cool extends the life sometimes.

It was no software fix, but the software was not at fault, it only looked like that.

The easiest way to check this is to just open up the pc box if you're OK with that (remove some of the metal casing on the pc box ) and see if it runs for longer than 2-3 days.

Duan

---

### Post by guliver on 2005-11-06
After many days of research I found all problems! :)

First I checked LOG file and found in there that Ubuntu reading floppy drive all the time, I disable floppy in BIOS and LOG remains clean now. 
It speed-up PC a lot but it still used to freeze.

CPU FAN was the problem! It did not cool CPU properly and CPU was hot and that was the problem. Now with new FAN it working more than 10 days without restart!

Thanks all.

---

