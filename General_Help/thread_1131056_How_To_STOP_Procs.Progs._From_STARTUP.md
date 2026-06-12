---
title: "How To STOP Procs./Progs. From STARTUP?"
date: 2009-04-20
forum: General Help
---

### Post by matey3 on 2009-04-20
Hello;

I am running Ubuntu 8.04 and need to know how I can disable a lot of programs which start up automatically?
I sometimes run X but most of the times I don't, so please tell me how in the terminal mode (Not in GUI)!

Thank You in Advance!

if you wondering why;

I test programs some times but most of the times I do not need them to startup and they are slowing this machine and the whole network down every time I boot up.
Is there a Master File some place so I can go thru and uncheck or disable these programs from coming up at the boot time? (sort of like REM-ing out)?

[I]Also sorry if this has come up before I did a search but the threads I found were too old and so I had no access to reply, thats why I had to create a new thread.
[/I]
:)

---

### Post by ibuclaw on 2009-04-20
This thread explains it pretty well, and is still true today:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Regards
Iain

---

### Post by mkrahmeh on 2009-04-20
here is a neat trick that i used once: go into the your default runlevel directory in the /etc/, lets say /etc/rc2.d/ there you will find a bunch of symlinks that point to init.d scripts (startup scripts). notice that these links start with the letter S or K, followed by a number, then the service name..
S stands for start
K stands for kill
the number refers to the precedence of these scripts

once i wanted to stop the jabber startup script from starting at boot, all i did was 
```
mv /etc/rc2.d/[COLOR="Red"]S[/COLOR]20jabber /etc/rc2.d/[COLOR="Red"]K[/COLOR]20jabber
```
and the jabber service stopped starting

_anyway, I recommend reading and follwing the instructions in the post above_, coz i dont feel it like a healthy approach

---

### Post by oldos2er on 2009-04-20
sysv-rc-conf is an easy-to-use CLI tool to manage services.

---

### Post by mkrahmeh on 2009-04-20
> **oldos2er said:**
> sysv-rc-conf is an easy-to-use CLI tool to manage services.

interesting 
i tried the sysv-rc-conf myself, actually its a quick-and-dirty shortcut of what i just described: it renames the initials of the symlinks from S to K (and vice versa) as services are being turned on and off ;)

---

### Post by matey3 on 2009-04-22
Thank you all very much for the info.
thanks lain for the link and thanks to mkrahmeh for the detailed instructions.
I had forgotten about the /etc/rcX directories.(I had only used it once to kill a process b4).
And thanks very much for the tool oldos2er!
The more tools in my toolbox the better off I am.
I may use one or another on my other Linux OSes we have a few servers here.

BTW:

Can you guys Please tell me what are the diff. Run Levels for?
I see 1 thru 5 then 0 and then S.
I think the lower the number the more important the process ? but I am not so sure.
Thanks!

---

### Post by mkrahmeh on 2009-04-22
> **matey3 said:**
> 
I think the lower the number the more important the process ? but I am not so sure.
Thanks!

if you mean that shutting down the computer is the most important process, then yes :lolflag:

level 0 is for shutdown, level 6 is for reboot 

levels 2-5 are different on the service scale (the services they provide) and on the distro scale (debian, redhat,..). level 1, for instance, is for single user mode without GUI or networking, subsequent levels start to offer more services. this scheme can be useful for maintenance and some other reasons that i dont know :)

---

### Post by matey3 on 2009-04-23
> **mkrahmeh said:**
> if you mean that shutting down the computer is the most important process, then yes :lolflag:

level 0 is for shutdown, level 6 is for reboot 

levels 2-5 are different on the service scale (the services they provide) and on the distro scale (debian, redhat,..). level 1, for instance, is for single user mode without GUI or networking, subsequent levels start to offer more services. this scheme can be useful for maintenance and some other reasons that i dont know :)

Thank you MKRAHMEH:

I was hasty in asking this question, I appreciate your answer, later I read about it in that link TINIVOLE posted here.

Thanks a lot!

Nice to know I am in a good company ;-)

---

