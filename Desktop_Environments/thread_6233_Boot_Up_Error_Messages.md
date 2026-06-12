---
title: "Boot Up Error Messages"
date: 2004-11-26
forum: Desktop Environments
---

### Post by spirospr on 2004-11-26
I've posted this before but i need some more help.

When i boot up Ubuntu on my laptop i get some fatal error messages when enabling hot plug in subsystem. As most of you said this not something causing a problem.

The thing is that i made almost everything work on my laptop and i am very satisfied with Ubuntu, but because i want everything to be perfect i hate to see error messages during boot up.  (Although i still believe that gettinh error messages means that sth is not working right there)

Please does any one know what i can do in order not to get this errors. Could i disable in someway this procedure without causing any problems? It would be realy great if i found a solution.....

---

### Post by mr_ed on 2004-11-26
I assume it's the pciehp and shpchp errors?

Tack them (pciehp and shpchp) on the end of /etc/hotplug/blacklist, one on each line, assuming those are the errors you're getting.

---

### Post by jiyuu0 on 2004-11-26
modprobe: FATAL: Error inserting... 
[http://kitech.com.my/ubuntu/4.10/#modprobefatalerror](http://kitech.com.my/ubuntu/4.10/#modprobefatalerror)

>The thing is that i made almost everything work on my laptop
I am near to that... except to print from ubuntu to a shared windows xp printer? 

Have you tried this before?

---

### Post by spirospr on 2004-11-26
[QUOTE=jiyuu0]modprobe: FATAL: Error inserting... 
[http://kitech.com.my/ubuntu/4.10/#modprobefatalerror](http://kitech.com.my/ubuntu/4.10/#modprobefatalerror)

>The thing is that i made almost everything work on my laptop
I am near to that... except to print from ubuntu to a shared windows xp printer? 

Have you tried this before?[/QUOTE]

Well the instructions from there seems to work. Thank you....
But a problem occured. After log in gnome i have no sound card detected. Before log in Gnomei have sound. Why did this happen? 

I have another question.

How can i stop during boot up to to synchronize clock to ntp.ubuntulinux.org

When i'm not connected to internet it takes to much time to boot up because it can't syncronize.

---

### Post by jiyuu0 on 2004-11-26
How can i stop during boot up to to synchronize clock to ntp.ubuntulinux.org

Quick/Temp solution:
Can't wait... just hit Ctrl + C to skip

Permanant solution: 
$ sudo chmod -x /etc/init.d/ntpdate

---

### Post by spirospr on 2004-11-26
[QUOTE=jiyuu0]How can i stop during boot up to to synchronize clock to ntp.ubuntulinux.org

Quick/Temp solution:
Can't wait... just hit Ctrl + C to skip

Permanant solution: 
$ sudo chmod -x /etc/init.d/ntpdate[/QUOTE]

Thank's man you managed to solve my problems.

---

### Post by davaraj on 2004-11-27
I get this message during boot:

'Setting the System Clock using the Hardware Clock as reference'
and nothing happens after that. 

The system seems to hang, but if I press CTRL C, then it continues with the rest of the boot messages and everything seems to be fine after that.
I have noticed another similar boot message appearing earlier and the system responds with a OK and continues, until it reaches the same message again a little later and hangs.

My system :
Dell PowerEdge SC420
512 MB memory
80 GB sata hd

I'm still new to linux and would appreciate any help with this problem.

--davaraj

---

### Post by jiyuu0 on 2004-11-27
I have not encountered the problem before, but you can try these... one at a time

1) [http://kitech.com.my/ubuntu/4.10/#disablesystemdatetimeutc](http://kitech.com.my/ubuntu/4.10/#disablesystemdatetimeutc)
*restart

2) Disable:
$ sudo chmod -x /etc/init.d/hwclockfirst.sh 
*restart, if not work change -x to +x

3) Disable 
$ sudo chmod -x /etc/init.d/hwclock.sh 
*restart, if not work change -x to +x

4) Disable both
$ sudo chmod -x /etc/init.d/hwclockfirst.sh 
$ sudo chmod -x /etc/init.d/hwclock.sh 

If you found the solution, do let me know too ya...

---

### Post by Maxobelix on 2004-12-17
Hi,
I have the same problem on a Dell poweredge 800  :?
I gonna try your tips on the next reboot.



[Edit]

Ok, i have tried your tips but none of them can resolve this issue  :-k 

The badest thing : this synchonization halt my server on shutdown and CTRL+C doesn't work , i have to HW shutdown my server...  :shock:

---

### Post by aziz on 2006-02-20
hallo everybody 
i have too much problems i do not how to lose it
first problem sychronise ntp.ubuntulinux.org
when i try to repair it  
it gives me gedit 5604 **warning...
what shall i do 
please anyone help me

---

