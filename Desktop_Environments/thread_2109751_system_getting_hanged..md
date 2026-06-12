---
title: "system getting hanged."
date: 2013-01-28
forum: Desktop Environments
---

### Post by suffiyan on 2013-01-28
hello friends. 
I am a new user to ubuntu.
as i have installed the operating system ubuntu 12.04. 
the problem i am facing is while working my system is suddenly hanged. i have no other option except restart.
it only happens if i add some appearances (like selecting best visual mode).
my system configuration is
1. dual core with 3.00Ghz
2. ram DDR 2 with 1.4gb
3. hard disk of 160 gb.
[no graphic card]
please help

---

### Post by AM Ramakrishnan on 2013-01-30
I think that it could be that you do not have a graphics card. Are there any specific applications that it hangs on?

---

### Post by BlinkinCat on 2013-01-30
Hi,

Copy/paste the following in a terminal then run - 

```
/usr/lib/nux/unity_support_test -p
```All responses in result should be "yes" to confirm if your machine is capable of running Unity.

Cheers - :p

---

### Post by suffiyan on 2013-02-06
not for particular app..   whenever i swith on, it'll work for a while lyk 2 or 3 mins.. n den it wil struck..  mostly it needs graphic card

---

### Post by FahadMKS on 2013-02-06
This can also happen due to a large amount of temp files in the computer. Try removing them manually or you may use the software" bleachbit " to do your job.

Please try that and lemme know.

---

### Post by rajnikhil on 2013-02-08
Hi, I'm having similar issues. I have Ubuntu 12.04 running on my laptop as well as desktop. There are no such issues on my laptop, although it does hang momentarily when the load increases but becomes responsive soon enough. However my desktop hangs and never becomes responsive again. The only way is to force restart it. I've observed it happen mostly when I'm streaming videos on firefox. It may freeze even when I use other load heavy programs like GIMP. When I was running 10.04 on Desktop, it often used to restart automatically when I ran such heavy programs for sometime and I thought the system is overheating and I need to install an extra cooling fan but now after upgrading to 12.04 it only hangs and that too just after starting the system for only a few minutes. This, to me, indicates that the issue is not with heat dissipation.

My Desktop config is:
AMD Athlon 64 2 cores,
3gb in 2DIMM ddr2, 1 chip is 1GB Ram and other is 2GB RAM. However both these chips have different frequencies.

I've tried the two steps mentioned in different replies above but it didn't resolve the issue. Could someone please advice me how detect the issue and resolve. It is really annoying when the system hangs so frequently and I'm avoiding necessary but load heavy programs for this reason.

Thanks in advance.

---

### Post by rajnikhil on 2013-02-10
Can anyone please provide some guidance. Any help will be much appriciated.

---

### Post by suffiyan on 2013-02-11
i've another problem guyz.
i've installed ubuntu 10.10 new to my system.
if i want to install any software i'll go for "ubuntu software center" then if i select any software lyk "vlc" i'm not finding "install" button, only "more info" button is available in left side. please help.. !!

---

### Post by FahadMKS on 2013-02-21
When u click on the more info button it will show u a page to add the software to the software center list and once that's done.. you will be able to install the software.

---

### Post by claracc on 2013-02-21
> **suffiyan said:**
> i've another problem guyz.
i've installed ubuntu 10.10 new to my system.
if i want to install any software i'll go for "ubuntu software center" then if i select any software lyk "vlc" i'm not finding "install" button, only "more info" button is available in left side. please help.. !!

Ubuntu 10.10 reached its end of life some time ago, so it is not supported anymore. You don't have the repositories to install software, you need to change the repositories in your sources.list file as it is addressed in this link: [http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

Any case, I don't recommend to stay with an oudated distro but to install a supported one (12.04, 12.10...)

---

