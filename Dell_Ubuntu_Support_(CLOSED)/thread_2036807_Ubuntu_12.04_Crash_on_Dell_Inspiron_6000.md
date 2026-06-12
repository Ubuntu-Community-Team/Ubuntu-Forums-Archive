---
title: "Ubuntu 12.04 Crash on Dell Inspiron 6000"
date: 2012-08-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bbirkinbine on 2012-08-02
I have been running Ubuntu 12.04 on my Dell Inspiron 6000 and have not had any problems until recently.  In the past week, I have what seems to be the equivalent of the "blue screen of death" I experienced when I was running Windows XP (which was a big reason for switching to Ubuntu).  I cannot perform any functions and I am forced to shut down.  When I boot up after such an experience, things seem to be running smoothly.  But I've now had the same thing happen at least three or four times in the past week.  

Since I'm not sure exactly what to make of the text on the screen, I'll post it in its entirety below. 

Any help is greatly appreciated (especially if I can make this older computer last for two more years of my PhD work!)

Thanks!
-B

Text reads:
could not write bytes: Broken pipe
* Checking battery state...

1606.951066] Kernel panic - not syncing: Attempted to kill init!
[ 1606.951126] Pid: 1, comm: init Not tainted 3.2.0-27-generic #43-Ubuntu
[ 1606.951173] Call Trace:
[ 1606.951205] [<c155ef8a>] ? printk+0x2d/0x2f
[ 1606.951242] [<c155ee58>] panic+0x5c/0x161
[ 1606.951280] [<c104eeb4>] forget_original_parent+0x1e4/0x1f0
[ 1606.951325] [<c1573f5d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[ 1606.951370] [<c104eed3>] exit_notify+0x13/0x100
[ 1606.951408] [<c104f66c>] do_exit+0x1ac/0x390
[ 1606.951445] [<c104f9a8>] do_group_exit_+0x38/0xa0
[ 1606.951483] [<c105e486>] get_signal_to_deliver+0x1b6/0x3f0
[ 1606.951529] [<c15772c0>] ? vmalloc_fault+0xee/0xee
[ 1606.951567] [<c10028ff>] do_signal+0x3f/0xd0
[ 1606.951603] [<c15772c0>] ? vmalloc_fault+0xee/0xee
[ 1606.951641] [<c15776d8>] ? do_page_fault+0x418/0x490
[ 1606.951680] [<c104ebc6>] ? do_wait+0xf6/0x200
[ 1606.951717] [<c104fadf>] ? sys_waitid+0xf6/0x200
[ 1606.951755] [<c104d770>] ? wait_task_continued+0x140/0x140
[ 1606.951797] [<c1002ba5>] do_notify_resume+0x75/0x90
[ 1606.951836] [<c15741d0>] work_notifysig+0x13/0x1b
[ 1606.951877] panic occurred, switching back to text console

---

### Post by 2F4U on 2012-08-03
Maybe bad RAM? Did you run memtest to test your RAM?
Any recent changes in the hardware?
Is the machine getting hot when this happens?

---

### Post by bbirkinbine on 2012-08-03
> **2F4U said:**
> Maybe bad RAM? Did you run memtest to test your RAM?
Any recent changes in the hardware?
Is the machine getting hot when this happens?

1) I have not run a memtest, but I can do this and get back to you.
2) No changes in hardware...at least not for approx 4 years.  
3) This machine does tend to get a bit hot, especially if I'm trying to stream something (like news clips, or watch an episode of the Daily Show).  The fan has been running loud for some time. Back when I was running Windows, I did have a couple instances of a shutdown related to heat.  Ubuntu seemed to fix all previous issues I had with Windows though.  That's why I was wondering if this was a hardware issue.

Thanks for the response.  Heat could be the issue, but I'll run a memtest and see what it looks like.

Cheers!
-B

---

