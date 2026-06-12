---
title: "cpu always 100% ubuntu 8.10"
date: 2008-12-31
forum: General Help
---

### Post by coombesy on 2008-12-31
Hey,

I've a problem since i upgraded to 8.10 - my cpu is always around 100%! The machine is fairly old (pentium II 700mhz) but with ubuntu 8.04 there was no problem.

I've tried googling it and can only find program specific, or coming out of sleep issues, whereas my problem is all the time.

Any help would be appreciated as it is getting very difficult to test anything i'm developing.

---

### Post by scragar on 2008-12-31
Open up a terminal and run ```
top
```This will show us what the problem is.

---

### Post by wmoore on 2008-12-31
Edit: What scragar said /\/\/\

---

### Post by AlanR8 on 2008-12-31
Hi

I think what the responders meant was open a terminal and at the prompt type "top" without the quotes. This will produce a list of the processes active on your machine together with stats about CPU load etc.

Or, you could press ctrl + esc to bring up a graphical display, rather like task manager in Doze. Here you can sort the processes in order of CPU usage etc and see the same results. You can also select a process and kill it!

---

### Post by scragar on 2008-12-31
> **AlanR8 said:**
> Hi

I think what the responders meant was open a terminal and at the prompt type "top" without the quotes. This will produce a list of the processes active on your machine together with stats about CPU load etc.

Or, you could press ctrl + esc to bring up a graphical display, rather like task manager in Doze. Here you can sort the processes in order of CPU usage etc and see the same results. You can also select a process and kill it!

DON'T KILL IT UNLESS YOU KNOW IT'S SAFE!

Some tasks cannot be safely killed, and some should be manualy restarted afterwards, unless you know what you are killing is safe to kill it's always better to ask.

---

### Post by AlanR8 on 2008-12-31
Scragar is correct.

I had a problem the other day similar to the one at the top of the post. I'm running Kubuntu 8.1 and KDE4.2 Beta so I expect some issues from time to time. I noticed the cooling fan on this Sony Laptop had booted up and things had slowed down. Looking at the System Activity it appeared Mplayer was running at almost 100% CPU usage. 

Can't think why as I hadn't launched it but I do have the Mplayer plugin for Firefox and maybe that's what had stalled.

No problems killing that and back down to the usual < 10% CPU load.

---

