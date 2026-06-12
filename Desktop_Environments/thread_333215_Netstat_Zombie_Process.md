---
title: "Netstat Zombie Process"
date: 2007-01-07
forum: Desktop Environments
---

### Post by Ethos on 2007-01-07
Hello everyone I have a weird problem. I have a netsat zombie process and cannot get rid of it. I tried to use sudo kill -9 <pid> but it still remains, and i rebooted twice. Im not sure were to go from here. Help would be appreciated, thanks

---

### Post by ayoli on 2007-01-07
this zombie process must be a child process and you can get rid of it by killing parent process
```
ps -aef -H
```
will list all processes with hierarchy structure.
I also have a netstat zombie process which is a child process of firefox:
```
ayoli     5373  5244  0 10:12 ?        00:00:35     /usr/lib/firefox/firefox-bin
ayoli     5475  5373  0 10:13 ?        00:00:00       [netstat] <defunct>
```
if i do a 
```
kill -9 5373
```
this kills firefox and all its children process, so the netstat zombie process disappear also.

---

### Post by Ethos on 2007-01-07
thanks alot! it was a child process of evolution mail. :) thanks again

---

### Post by Ethos on 2007-01-07
One question, i tried removing evolution and then reinstalling it, but whenever I launch it I get that netstat zombie process...is there a way to get rid of it?

---

### Post by finer recliner on 2007-01-07
related question: what is a netstat zombie process

should be concerned about it?

---

### Post by Ethos on 2007-01-07
On Unix operating systems, a zombie process or defunct process is a process that has completed execution but still has an entry in the process table, allowing the process that started it to read its exit status. The term zombie process derives from the common definition of zombie—an undead person. In the term's colorful metaphor, the child process has died but has not yet been reaped.

When a process ends, all of the memory and resources associated with it are deallocated so they can be used by other processes. However, the process's entry in the process table remains. The parent is sent a SIGCHLD signal indicating that a child has died; the handler for this signal will typically execute the wait system call, which reads the exit status and removes the zombie. The zombie's process ID and entry in the process table can then be reused. However, if a parent ignores the SIGCHLD, the zombie will be left in the process table. In some situations this may be desirable, for example if the parent creates another child process it ensures that it will not be allocated the same process ID.

A zombie process is not the same as an orphan process. Orphan processes don't become zombie processes; instead, they are adopted by init (process ID 1), which waits on its children.

Zombies can be identified in the output from the Unix ps command by the presence of a "Z" in the STAT column. Zombies that exist for more than a short period of time typically indicate a bug in the parent program. As with other leaks, the presence of a few zombies isn't worrisome in itself, but may indicate a problem that would grow serious under heavier loads.

To remove zombies from a system, the SIGCHLD signal can be sent to the parent manually, using the kill command. If the parent process still refuses to reap the zombie, the next step would be to remove the parent process. When a process loses its parent, init becomes its new parent. Init periodically executes the wait system call to reap any zombies with init as parent.

---

### Post by acope on 2007-01-16
Looks like here's a problem with firefox v2.0.1 on *ubuntu.

At least twice a day I get a zombie netstat process hanging off firefox-bin. I know it's there when CPU usage hits 95%.

It's easy to work around:

$ killall firefox-bin
$ firefox &

and fortunately Firefox 2 lets you restore your session. :-)

But it's still a bug! 

Anyone know what's causing the problem?  Is it a firefox plugin doing it?

Cheers
Andrew

---

### Post by Technikal on 2007-01-27
I think I've found a way to fix this, you need to change your firefox launcher to pass firefox %u --sync . I did this and haven't had any zombies since.

 - Technikal

---

### Post by xtrm_redbull on 2007-02-05
> **Technikal said:**
> I think I've found a way to fix this, you need to change your firefox launcher to pass firefox %u --sync . I did this and haven't had any zombies since.

 - Technikal

I followed your instruction, and it works I dont see netstat zombie in system monitor, but everytime I start firefox it doesn't go to my home page, it goes to [www.%u.com](www.%u.com),

Can you explain this. Thanks

---

### Post by wonko on 2007-02-22
I've constantly got a [defunct] netstat prosess under thunderbird. It sometimes makes my desktop hang. Can I use the --sync option on t-bird as well?
Is 'defunct' the same as zombie? I've tried looking for a z in the stat-column, but I can't see ps shows a stat-column...
ayoli: what's the difference between "ps -aef -H" and "ps -efH"? (doesn't e imply a?)
edit: just tested the --sync option. Didn't help for me... Still got a defunct netstat both in firefox and tbird that hangs my desktop :(

---

### Post by zarxcky on 2007-05-06
Hello guys,

Adding -browser to the firefox --sync -a resolved the zombie issue on me after firefox --sync -a did not last long.

firefox --sync -browser -a & (more info at zarxcky.blogspot.com) :)

---

